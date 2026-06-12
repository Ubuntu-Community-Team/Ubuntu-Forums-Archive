---
title: "LAN/Wifi not working ubuntu 12.04"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by vinoth4 on 2014-03-01
Hello Guys, 

I am new to Linux, i am a Windows guy. Today i installed Ubuntu 12.04 in my other laptop and i see WIFI/Lan not working at all. 

Here is what i have tried. 

```
lspci -nn | grep 0200
```

The ethernet controller is Realtek Semiconductor ```
RTL8101E/RTL8102E
```

I tried the solution of Komdodev posted here. 
[http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)

But it does not work. I don't know what to do?.

> sudo update-initramfs -u && cd ~/Downloads && tar xvf r8101-1.022.00.tar.bz2 && cd r8101-1.022.00 && sudo sh autorun.sh
[sudo] password for vamsi: 
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
r8101-1.022.00/
r8101-1.022.00/src/
r8101-1.022.00/src/r8101.h
r8101-1.022.00/src/r8101_n.c
r8101-1.022.00/src/rtl_eeprom.c
r8101-1.022.00/src/rtltool.c
r8101-1.022.00/src/rtltool.h
r8101-1.022.00/src/rtl_eeprom.h
r8101-1.022.00/src/Makefile_linux24x
r8101-1.022.00/src/rtl_ethtool.h
r8101-1.022.00/src/Makefile
r8101-1.022.00/readme
r8101-1.022.00/autorun.sh
r8101-1.022.00/Makefile


Check old driver and unload it.
Build the module and install
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5396:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_board&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5799:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_init_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5926:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl8101_remove_one&#8217;
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7851:12: error: &#8216;rtl8101_init_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:2: error: implicit declaration of function &#8216;__devexit_p&#8217; [-Werror=implicit-function-declaration]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7852:25: error: &#8216;rtl8101_remove_one&#8217; undeclared here (not in a function)
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:7488:12: warning: &#8216;rtl8101_poll&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:869:1: warning: &#8216;rtl8101_xmii_reset_pending&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:885:1: warning: &#8216;rtl8101_xmii_link_ok&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:894:1: warning: &#8216;rtl8101_xmii_reset_enable&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1117:1: warning: &#8216;rtl8101_link_option&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1239:1: warning: &#8216;rtl8101_set_speed_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1565:1: warning: &#8216;rtl8101_gset_xmii&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1776:27: warning: &#8216;rtl8101_ethtool_ops&#8217; defined but not used [-Wunused-variable]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1811:13: warning: &#8216;rtl8101_get_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:1879:1: warning: &#8216;rtl8101_print_mac_version&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:4584:1: warning: &#8216;rtl8101_release_board&#8217; defined but not used [-Wunused-function]
/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.c:5729:1: warning: &#8216;rtl8101_check_eeprom&#8217; defined but not used [-Wunused-function]
cc1: some warnings being treated as errors
make[3]: *** [/home/vamsi/Downloads/r8101-1.022.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/vamsi/Downloads/r8101-1.022.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2


---

### Post by chili555 on 2014-03-02
Please see posts #23 and following: [http://ubuntuforums.org/showthread.php?t=1964200&page=3](http://ubuntuforums.org/showthread.php?t=1964200&page=3)

The newer version should compile just fine on your 3.8.0-xx kernel. I doubt you need the patch.

---

