CC = g++
CFLAGS = -O3 -lpthread
SRC_DIR = src
OUTPUT_DIR = output
OBJ_DIR = $(OUTPUT_DIR)

# 确保输出目录存在
$(shell mkdir -p $(OUTPUT_DIR))

# 目标文件
TARGET = $(OUTPUT_DIR)/evaluate
OBJS = $(OBJ_DIR)/main.o $(OBJ_DIR)/strategy.o $(OBJ_DIR)/matrix.o $(OBJ_DIR)/reduce.o

# 默认目标
all: $(TARGET)

# 链接规则
$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) -o $@ $^

# 编译规则
$(OBJ_DIR)/main.o: $(SRC_DIR)/main.cpp $(SRC_DIR)/strategy.h $(SRC_DIR)/matrix.h $(SRC_DIR)/reduce.h
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJ_DIR)/strategy.o: $(SRC_DIR)/strategy.cpp $(SRC_DIR)/matrix.h
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJ_DIR)/matrix.o: $(SRC_DIR)/matrix.cpp $(SRC_DIR)/matrix.h
	$(CC) $(CFLAGS) -c $< -o $@

$(OBJ_DIR)/reduce.o: $(SRC_DIR)/reduce.cpp $(SRC_DIR)/strategy.h $(SRC_DIR)/matrix.h
	$(CC) $(CFLAGS) -c $< -o $@

.PHONY: clean all

clean:
	rm -f $(OBJ_DIR)/*.o $(TARGET)