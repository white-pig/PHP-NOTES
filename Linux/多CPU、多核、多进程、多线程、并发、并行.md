# 多CPU、多核、多进程、多线程、并发、并行

本文转载自：https://www.cnblogs.com/csfeng/p/8670704.html  

首先，理解几个概念：  
1. 进程是资源分配的基本单位(调度单位)。
2. 一个进程可以包括多个线程。
3. 在单CPU中，CPU是无法被多个程序并行使用的。
4. 操作系统调度器：拆分CPU为一段段时间的运行片，轮流分配给不同的进程。
5. 操作系统内存管理模块：管理物理内存、虚拟内存相关的事务。  

由于CPU同一时刻只能执行一个进程，如果我们不加以控制的话，一个进程可能使用CPU直到运行结束，于是出现了操作系统调度器，而进程也成为了调度单位。  

调度器切换CPU给不同进程使用的速度非常快，于是在用户角度来看程序是在同时运行，这就是并发，而实际上CPU在同一时刻只运行着一个进程。  

线程被包含在进程中，线程共享所属进程的地址空间。进程中的不同线程为了使用CPU核心，则会进行线程切换，但是由于线程共享了进程的地址空间，线程的切换比进程的切换开销少了很多，在这里依然是并发，一个CPU核心同一时刻只能执行一个线程。  

如果CPU是多核的话，那么进程之间的不同线程可以使用不同核心，这里就不是并发了，而是并行。  

线程是CPU调度和分配的基本单位，进程是操作系统进行资源分配(包括CPU、内存、磁盘IO等)的最小单位。有句话说CPU只能看到线程，操作系统将一个进程分配给CPU后，CPU看到的是进程中的很多线程，CPU无法调度和分配进程。CPU只能调度看到的线程，比如将线程ABCD分配到核心1234。   

总结：  
1. 单CPU进程只能是并发，多CPU进程可以并行。
2. 单CPU线程只能是并发，多CPU线程可以并行。
3. 无论是并发还是并行，在用户角度来看程序是在同时运行的。



