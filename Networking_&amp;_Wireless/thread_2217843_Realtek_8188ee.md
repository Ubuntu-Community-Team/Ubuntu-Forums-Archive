---
title: "Realtek 8188ee"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by Aek_Tiesto on 2014-04-18
hello Friends i'm not new on ubuntu and i'm not a pro on it :D well i used to switch between ubuntu editions i have a wifi card " Realtek 8188ee " when i used to install Ubuntu OS the system never recognized my wifi card so i used to install it via cd , make , make install commands and of course the Tar file i downloaded from Realtek Site ....
every thing used to go fine .. today i was tweaking my Laptop with it Elementary Os 0.2  (" ubuntu 12.04 Precise ") i was using it normally when i decided to update the kernel i did it and after rebooting to take effect the wifi didn't worked i tried to reinstall it like i used to but it gives me this messages >>>
.
.
..
aek-tiesto@aek-tiesto:~$ sudo su
[sudo] password for aek-tiesto: 
root@aek-tiesto:/home/aek-tiesto# cd '/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013' 
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# make
make -C /lib/modules/3.8.0-38-generic/build M=/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-38-generic'
  CC [M]  /home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-38-generic'
make: *** [all] Error 2
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# make install
make -C /lib/modules/3.8.0-38-generic/build M=/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-38-generic'
  CC [M]  /home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-38-generic'
make: *** [all] Error 2
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# ^C
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# ^C
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# ^C
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# ^C
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# ^C
root@aek-tiesto:/home/aek-tiesto/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013# 


NOTE: i'm using the same files i used to install the driver with ("" linux_mac80211_0012.0207.2013.tar.bz2 "") 
my laptop is HP PAVILION 15

---

### Post by Aek_Tiesto on 2014-04-18
this is what the lspci -v shows 
#
#
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 197d
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 4000 [size=256]
    Memory at c2500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl

---

