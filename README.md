# LS2K0300-linux-4.19-0802-2026
用于龙芯99派上，基于 linux-4.19-0802.tar.gz 内核源码，修改添加摄像头、TFT(2.0寸)、gtim、atim的源码。

编译步骤：
1 添加环境变量 
 编写bash文件 set2k300env.sh
#!/bin/sh
#set -x
export LC_ALL=C LANG=C
export PATH= 【你的交叉编译工具链路径】/bin:$PATH

#set +x
在控制台中运行 source set2k300env.sh
用命令 loongarch64-linux-gnu-gcc -v 查看编译器版本，从而检查 是否添加成功

2 配置内核
make menuconfig ARCH=loongarch

3 编译内核
make vmlinuz ARCH=loongarch CROSS_COMPILE=loongarch64-linux-gnu- -j 4 "$@"

编译后生成 vmlinux（未压缩） 和 vmlinuz（压缩后的文件 ），复制到开发板的 /boot 目录下。
