---
title: "How to install RTL8821AU from CD?"
date: 2019-05-01
forum: Networking &amp; Wireless
---

### Post by JimHiTek on 2019-05-01
Ubuntu 16.04, Cinnamon desktop. 

Just purchased a high gain Wifi adapter. If I just plug it into a USB port the adapter is not recognized. So I have no internet while it's plugged in. 

It comes with a Linux directory on the CD. In that directory are several folders for different hardware setups and an Install.su file. There is also a 'Drivers' directory that has a single folder "rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51". 

I downloaded that folder to it's own folder under 'Downloads' on my machine. When I dbl click on it it opens and has a 'Makefile', several other files and several folders.

I assume this is all I need to install the drivers. My question is HOW? I've tried following several threads on google but none of them work. Another thing I find interesting is that all those threads end up being for the RTL8812, NOT the RTL8821 which confuses the issue. I have a Git account but there's nothing about the 88212AU there. I don't know if there's a difference between the 8821 and 8812 or not but it's curious how a search for 8821 keeps leading to 8812 threads.

So can someone let me know how to install?   

Here's the error I get when I navigate to the Download directory where Makefile is, open Term and type 'make'

make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-145-generic/build M=/home/jim-hitek/Downloads/Network Hrdwr/Realtek/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-145-generic'
arch/x86/Makefile:167: CONFIG_X86_X32 enabled but no binutils support
Makefile:717: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
make[1]: *** No rule to make target 'Hrdwr/Realtek/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-145-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2

I don't know what it's trying to tell me. Or how to fix it. No rule? Failed recipe? I have a general sense of how to address those issues but nothing concrete.

Thanks for any help.

---

### Post by JimHiTek on 2019-05-01
OK, this is weird...I've tried to edit my above post 3X...the 88212 is suppose to be 8821 (eighty eight twenty one ) but every time I change it and 'save' it comes back as 88212 ??? Why!?

---

### Post by jeremy31 on 2019-05-01
If you have an internet connection by ethernet or other means do
```
sudo apt install git build-essential dkms
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
Reboot and make sure Secure Boot is disabled in BIOS, you can check ```
mokutil --sb-state
```

---

