---
title: "[SOLVED] NEWBIE - not Wireless - RTL8185 driver set up?"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by Ant68 on 2008-09-28
Hi all,

I am a newbie to Linux & ubuntu and some of the questions may be trivial so thank you in advance for baring with me. :)...

I have removed windows XP and replaced it with linux ubuntu 8.04. Everything seems to be working fine to the exception of the wireless. I have a PC Destop Medion and had installed a wireless network card: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20). (see full output of the lspci command line below). This was working very fine with Windows. It does not work now.

After some investigation on the interet, I have come to realise that the issue might be with the driver (not 100% sure - pls confirm). The wireless card does not show in the Network Manager (only the ethernet cards show)

I have then run the command "ifconfig" to show that the card was not listed. See full output in below.

I have then found out on the internet that this might well be because my driver is not set up so I found the following driver link: [_RTL 8185 driver Kernel for 2.6.22_]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L") . I downloaded the linux version and extracted the content. According to the installation guide in the readme file I have run the command: ./makedrv (see the output below). It seems that there has been a few errors. I initially though it could be becasue of the kernel version which I run 2.6.24 and the driver says it is for 2.6.22. I subsequently find an "unofficial" upgrade but it did the same. 

Looking on the forum and the internet, I have seen people mentioning "ndiswrapper". 
- Should I use this?  
- Where do I do it? 
- How do I set it up (set by set for a newbie...)?
- What should I do to get my wifi working on my computer?    


Supporting material:

See below the output for the command line: lspci
 
hemona@hemona-desktop:~/Desktop/rtl8185_linux_26.1027.0823.2007$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:06.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

See below the output for the command line: ifconfig

hemona@hemona-desktop:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:dc:d4:aa:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc400 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:1f:da:5d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68700 (67.0 KB)  TX bytes:68700 (67.0 KB)


See below the output for the command line: ./makedrv

hemona@hemona-desktop:~/Desktop/rtl8185_linux_26.1027.0823.2007$ ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_encrypt’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:417: error: ‘struct scatterlist’ has no member named ‘page’
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_decrypt’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:511: error: ‘struct scatterlist’ has no member named ‘page’
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function ‘michael_mic’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:613: error: ‘struct scatterlist’ has no member named ‘page’
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:617: error: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_init’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: ‘proc_net’ undeclared (first use in this function)
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_remove’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:594: error: ‘proc_net’ undeclared (first use in this function)
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_init’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:4213: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/hemona/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

---

### Post by Ant68 on 2008-09-28
I got it resolved.

as I suspected, I followed the link:

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

but downloaded the RTL8185 driver (for windows)

I blacklisted 
echo 'blacklist r8185' | sudo tee -a /etc/modprobe.d/blacklist

---

