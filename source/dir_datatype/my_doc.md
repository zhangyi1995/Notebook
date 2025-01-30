# 数据结构

常用的数据结构及其衍生的高级数据结构涵盖了不同的用途和特点，下面是常见的基本数据结构及其高级衍生结构的简要介绍：

## 1. **数组 (Array)**
   - **基本特点**: 存储在连续的内存位置，支持随机访问。
   - **衍生结构**:
     - **动态数组 (Dynamic Array)**: 可以动态调整大小，通常是在数组容量不足时进行扩展。
     - **环形数组 (Circular Array)**: 数组的末尾与开头相连接，适合用于循环队列等场景。
   
## 2. **链表 (Linked List)**
   - **基本特点**: 由节点组成，每个节点包含数据和指向下一个节点的指针。
   - **衍生结构**:
     - **双向链表 (Doubly Linked List)**: 每个节点有两个指针，分别指向前一个和后一个节点。
     - **循环链表 (Circular Linked List)**: 最后一个节点的指针指向头节点，形成一个循环结构。
     - **跳表 (Skip List)**: 基于链表的一种数据结构，使用多级链表来提高查找效率，常用于实现有序集合。

## 3. **栈 (Stack)**
   - **基本特点**: 遵循“后进先出” (LIFO) 的原则。
   - **衍生结构**:
     - **多栈 (Multiple Stacks)**: 使用一个共享数组来存储多个栈，每个栈有独立的边界。
     - **递归栈 (Recursive Stack)**: 用于函数调用时维护的栈帧。
   
## 4. **队列 (Queue)**
   - **基本特点**: 遵循“先进先出” (FIFO) 的原则。
   - **代码实现**
      ```{eval-rst}
      .. jupyter-execute::

        class Queue:
            def __init__(self):
                # 初始化队列，使用列表来存储队列元素
                self.queue = []
            
            def is_empty(self):
                # 判断队列是否为空
                return len(self.queue) == 0
            
            def enqueue(self, item):
                # 向队列中添加元素
                self.queue.append(item)
            
            def dequeue(self):
                # 从队列中移除并返回队首的元素
                # 如果队列为空，抛出异常
                if self.is_empty():
                    raise IndexError("dequeue from empty queue")
                return self.queue.pop(0)
            
            def peek(self):
                # 返回队列队首的元素但不移除它
                if self.is_empty():
                    raise IndexError("peek from empty queue")
                return self.queue[0]
            
            def size(self):
                # 返回队列中元素的个数
                return len(self.queue)
            
            def __str__(self):
                # 返回队列的字符串表示
                return f"Queue({self.queue})"

        def test_queue():
            # 创建一个空队列
            q = Queue()

            # 测试 is_empty() 方法
            assert q.is_empty() == True, "Test Case 1 Failed: The queue should be empty initially."
            
            # 测试 enqueue() 方法
            q.enqueue(10)
            assert q.is_empty() == False, "Test Case 2 Failed: The queue should not be empty after adding an element."
            assert q.peek() == 10, "Test Case 3 Failed: The first element should be 10."
            
            q.enqueue(20)
            q.enqueue(30)
            assert q.size() == 3, "Test Case 4 Failed: The queue size should be 3 after adding three elements."
            
            # 测试 dequeue() 方法
            assert q.dequeue() == 10, "Test Case 5 Failed: The dequeued element should be 10."
            assert q.size() == 2, "Test Case 6 Failed: The queue size should be 2 after dequeuing one element."
            
            # 测试 peek() 方法
            assert q.peek() == 20, "Test Case 7 Failed: The front element should be 20 after dequeuing 10."
            
            # 测试队列为空时的行为
            q.dequeue()
            q.dequeue()
            assert q.is_empty() == True, "Test Case 8 Failed: The queue should be empty after all elements are dequeued."
            
            # 测试 dequeue 和 peek 的异常处理
            try:
                q.dequeue()
                print("Test Case 9 Failed: Should raise IndexError when dequeuing from empty queue.")
            except IndexError:
                pass  # 预期会抛出 IndexError
            
            try:
                q.peek()
                print("Test Case 10 Failed: Should raise IndexError when peeking from empty queue.")
            except IndexError:
                pass  # 预期会抛出 IndexError

            print("All test cases passed!")
            
        # 运行测试用例
        test_queue()

      ```

   - **衍生结构**:
     - **双端队列 (Deque)**: 允许在队列两端进行插入和删除操作。
     - **优先队列 (Priority Queue)**: 每个元素都有优先级，优先级高的元素先被处理，通常使用堆实现。
     - **循环队列 (Circular Queue)**: 使用环形结构来实现队列，避免了普通队列中的空闲空间浪费。
   
## 5. **哈希表 (Hash Table)**
   - **基本特点**: 使用哈希函数将键映射到数组索引，实现常数时间复杂度的查找。
   - **衍生结构**:
     - **开放寻址法 (Open Addressing)**: 哈希冲突时通过线性探测、二次探测等方法来寻找空槽。
     - **链式哈希 (Chaining)**: 解决冲突时，采用链表将相同哈希值的元素串联起来。
     - **哈希树 (Hash Tree)**: 采用树结构来解决哈希冲突，能够提高查找效率。

## 6. **树 (Tree)**
   - **基本特点**: 由节点组成，每个节点包含数据和指向其子节点的指针。
   - **衍生结构**:
     - **二叉树 (Binary Tree)**: 每个节点最多有两个子节点。
     - **平衡二叉树 (Balanced Binary Tree)**: 自平衡二叉树，如 AVL 树和红黑树，保证操作在对数时间内完成。
     - **堆 (Heap)**: 完全二叉树，满足堆性质，常用于实现优先队列。
     - **B 树/B+ 树**: 自平衡树，用于数据库和文件系统中，支持高效的磁盘存储和查询。
     - **Trie 树 (前缀树)**: 用于高效存储和查找字符串，特别适合词典和自动补全等应用。

## 7. **图 (Graph)**
   - **基本特点**: 由节点和边组成，边可以是有向或无向的。
   - **衍生结构**:
     - **邻接矩阵 (Adjacency Matrix)**: 使用矩阵表示图的连接关系，适合稠密图。
     - **邻接表 (Adjacency List)**: 使用链表或数组来表示图的连接关系，适合稀疏图。
     - **带权图 (Weighted Graph)**: 图的边有权值，常用于最短路径算法（如 Dijkstra 算法）中。
     - **无向图和有向图 (Undirected/Directed Graph)**: 无向图的边没有方向，而有向图的边有方向。
     - **欧几里得图 (Euclidean Graph)**: 适用于描述点之间的距离和几何关系。

## 8. **集合 (Set)**
   - **基本特点**: 不包含重复元素的无序集合。
   - **衍生结构**:
     - **并查集 (Union-Find)**: 支持快速合并和查询集合，常用于处理连通性问题。
     - **哈希集合 (HashSet)**: 基于哈希表实现的集合，能够实现高效的查找、插入和删除操作。

## 9. **位图 (Bitmap)**
   - **基本特点**: 通过位操作存储和查询数据，适用于空间效率要求较高的场景。
   - **衍生结构**:
     - **布隆过滤器 (Bloom Filter)**: 一种空间效率高但允许有一定误判的概率的数据结构，适用于大规模数据的查重。

## 10. **字符串 (String)**
   - **基本特点**: 字符的序列，可以是静态或动态的。
   - **衍生结构**:
     - **KMP 算法**: 通过模式匹配算法，减少查找重复子串的时间复杂度。
     - **后缀树 (Suffix Tree)**: 用于高效的字符串查找、最长公共子串等问题。
     - **后缀数组 (Suffix Array)**: 通过排序所有后缀，能够高效处理字符串匹配问题。

## 11. **跳表 (Skip List)**
   - **基本特点**: 是一种层级化的链表，允许在多层链表上进行快速查找，平均查询时间复杂度为 O(log n)。
   - **应用**: 常用于有序集合的实现，类似于平衡二叉搜索树，但实现更简单。

## 12. **线段树 (Segment Tree)**
   - **基本特点**: 用于处理区间查询问题，支持区间的合并、更新等操作。
   - **衍生结构**:
     - **懒标记线段树 (Lazy Segment Tree)**: 对线段树的改进，通过延迟更新减少操作的复杂度。

## 13. **树状数组 (Fenwick Tree)**
   - **基本特点**: 用于高效计算前缀和，可以进行更新和查询操作，常用于处理区间求和问题。


# 算法
