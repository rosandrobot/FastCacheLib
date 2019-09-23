# FastCacheLib
一个c++的类似于std::map的结构，此结构线程安全，支持快速增删改查和老化

# 思路
- 用户视图
    - 用户看到的是一个存储着许多节点的快速缓存，通过此缓存，用户可以插入和查找节点；
    - 用户拿到节点后，可以对节点中的value进行自定义操作，还可以删除节点本身；
    - 用户拿到节点时，节点是锁闭状态，此时的节点在其他线程中是无法获取到的。用户使用完节点后需要解锁。
    - 节点是由cache管理，在缓存构建时，内存就已经分配好，用户不需要关心节点的内存使用；
    - 优雅与实用不可兼得，如此设计不太优雅但很实用；
