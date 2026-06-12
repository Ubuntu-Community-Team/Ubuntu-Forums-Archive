---
title: "Compiling ra3070 driver for my android device."
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by beafles98 on 2014-07-21
Hi. I'm having trouble with compiling ralink 3070 driver for my android device.
I know it's a bit tricky part, but I really need it.

So, I've downloaded the file : [http://www.mediatek.com/AmazonS3/Downloads/linux/DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2](http://www.mediatek.com/AmazonS3/Downloads/linux/DPO_RT5572_LinuxSTA_2.6.1.3_20121022.tar.bz2)
and then extract it successfully.
In the Makefile, I replace the target from 'PC' to 'ARM'. (I also added the following in the makefile : 
ifeq ($(PLATFORM),ARM)
LINUX_SRC = /home/k9qp1/Documents/E220S/Kernel
CROSS_COMPILE = arm-eabi-
endif
)

Just let you know that I've added toolchain directory to PATH variable.

Hopefully, the config.mk file in os/linux was configured properly. All I needed to do was to add the following in the config.mk file :

ifeq ($(PLATFORM),ARM)
EXTRA_CFLAGS := $(WFLAGS) -I$(RT28xx_DIR)/include
endif

So I issued the command make clean and make -j8...
But it gives me the error 


> 
make -C tools
make[1]: Entering directory `/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/tools'
gcc -g bin2h.c -o bin2h
cp -f os/linux/Makefile.6 /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/Makefile
make -C /home/k9qp1/Documents/E220S/Kernel SUBDIRS=/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux modules
make[1]: Leaving directory `/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/tools'
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/tools/bin2h
make[1]: Entering directory `/home/k9qp1/Documents/E220S/Kernel'
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/crypt_md5.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/crypt_aes.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/mlme.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_wep.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/action.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/rtmp_init.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_aes.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_sync.o
  CC [M]  /home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/eeprom.o
cc1: warnings being treated as errors
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.c: In function 'RtmpPrepareHwNullFrame':
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.c:3142: error: passing argument 2 of 'hex_dump' from incompatible pointer type
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/include/rt_os_util.h:679: note: expected 'unsigned char *' but argument is of type 'UINT32 *'
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.c:3150: error: passing argument 2 of 'RTUSBReadMACRegister' makes integer from pointer without a cast
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/include/rtmp.h:7214: note: expected 'USHORT' but argument is of type 'USHORT *'
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.c:3151: error: passing argument 2 of 'hex_dump' from incompatible pointer type
/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/include/rt_os_util.h:679: note: expected 'unsigned char *' but argument is of type 'UINT32 *'
make[2]: *** [/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../common/cmm_data.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/home/k9qp1/Documents/E220S/Module/Ralink/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux] Error 2
make[1]: Leaving directory `/home/k9qp1/Documents/E220S/Kernel'
make: *** [LINUX] Error 2


What could be the problem???

---

