---
title: "Driver Encore N150"
date: 2018-02-06
forum: Networking &amp; Wireless
---

### Post by raziel272 on 2018-02-06
I have a problem with the installation of the driver of my USB network card

I use the command 
```
cd /home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/
./install.sh

but drop this massage:

Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.13.0-32-generic/build M=/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922  modules
make[1]: se entra en el directorio '/usr/src/linux-headers-4.13.0-32-generic'
  CC [M]  /home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o
In file included from /home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.c:24:0:
/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/include/osdep_service.h:49:29: fatal error: linux/smp_lock.h: No existe el archivo o el directorio
compilation terminated.
scripts/Makefile.build:308: fallo en las instrucciones para el objetivo '/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o'
make[2]: *** [/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922/core/rtw_cmd.o] Error 1
Makefile:1550: fallo en las instrucciones para el objetivo '_module_/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922'
make[1]: *** [_module_/home/raziel/Escritorio/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.20110922/driver/rtl8192_8188CU_linux_v3.1.2590.20110922] Error 2
make[1]: se sale del directorio '/usr/src/linux-headers-4.13.0-32-generic'
Makefile:447: fallo en las instrucciones para el objetivo 'modules'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg
```

I have the Driver disk and i follow all instructions but i havent idea what happens

---

### Post by richard378 on 2018-02-06
I'm a newbie myself, but I think you should try to install the kernel source code first as on this wiki
[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)

and after that try the following remember sudo for install scripts is usually needed.  Change ./install.sh to the following:
sudo ./install.sh

---

### Post by wildmanne39 on 2018-02-06
The steps in post 2 are not needed and would probably be difficult for a new person.

The driver is almost without a doubt to old to build on a newer ubuntu, they almost never work and most likely not needed.

*Thread moved to **Networking & Wireless, a more appropriate forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chili555 on 2018-02-07
> RTL8192CU_8188CUS_8188CE-VAU_linux_v3.1.2590.[COLOR="#FF0000"]2011[/COLOR]0922The main problem is that this ancient circa-2011 driver is never going to compile on your modern 4.13.0-xx kernel. We no longer use wooden wheels on our sleek, black BMWs.

The second problem is that the newer, better driver rtl8192cu already exists in 4.13. If it isn't working as expected, something else is wrong. Please run and post:```
lsmod | grep rtl
rfkill list all
```

---

