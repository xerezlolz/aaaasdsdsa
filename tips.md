Tips for my sight
===================

## 概念 for bootload 
        Boot Loader,就是在操作系统内核运行之前运行的一段小程序。通过这段小程序，我们可以初始化硬件设备、建立内存空间的映射图，从而将系统的软硬件环境带到一个合适的状态，以便为最终调用操作系统内核准备好正确的环境。
### 1.Boot Loader 的启动过程是单阶段（Single Stage）还是多阶段（Multi-Stage)
        多阶段的 Boot Loader 能提供更为复杂的功能，以及更好的可移植性。从固态存储设备上启动的 Boot Loader 大多都是 2 阶段的启动过程，也即启动过程可以分为 stage 1、stage 2：
#### 2.bootloader stage 1：
    · 硬件设备初始化;
    · 为加载 Boot Loader 的 stage2 准备 RAM 空间;
    · 拷贝 Boot Loader 的 stage2 到 RAM 空间中;
    · 设置好堆栈;
    · 跳转到 stage2 的 C 入口点.
#### 3.bootloader stage 2:
    · 初始化本阶段要使用到的硬件设备;
    · 检测系统内存映射(memory map);
    · 将 kernel 映像和根文件系统映像从 flash 上读到 RAM 空间中;
    · 为内核设置启动参数;
    · 调用内核.