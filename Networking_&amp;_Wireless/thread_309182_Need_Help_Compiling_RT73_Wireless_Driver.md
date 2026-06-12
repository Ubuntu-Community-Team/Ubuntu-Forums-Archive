---
title: "Need Help Compiling RT73 Wireless Driver"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by OffHand on 2006-11-29
Hi all,

I have some problems compiling the RT73 driver for my Linksys WUSB54GC following this howto:

[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB54GC)

Any help is greatly appreciated.

This is the output of the terminal:

xxx@xxx:~$ cd RT73_Linux_STA_Drv1.0.3.6/
xxx@xxx:~/RT73_Linux_STA_Drv1.0.3.6$ cd Module/
xxx@xxx:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make clean
rm -rf *.o *~ .*.cmd *.ko *.mod.c .tmp_versions built-in.o
xxx@xxx:~/RT73_Linux_STA_Drv1.0.3.6/Module$ make all
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o
In file included from /home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:99: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token
In file included from /home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rt_config.h:189,
                 from /home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:40:
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:506: error: expected specifier-qualifier-list before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:719: error: expected specifier-qualifier-list before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:758: error: expected specifier-qualifier-list before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:793: error: expected specifier-qualifier-list before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1097: error: expected specifier-qualifier-list before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1764: error: expected &#8216;)&#8217; before &#8216;pSrc1&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1770: error: expected &#8216;)&#8217; before &#8216;pSrc1&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1775: error: expected &#8216;)&#8217; before &#8216;pSrc&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1779: error: expected &#8216;)&#8217; before &#8216;pSrc&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1784: error: expected &#8216;)&#8217; before &#8216;pDest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:1820: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2195: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2199: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2705: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2709: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2844: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2862: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:2954: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:3222: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:3226: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp.h:3393: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;PVOID&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function &#8216;RTUSBHalt&#8217;:
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:236: warning: implicit declaration of function &#8216;RTMPMoveMemory&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function &#8216;CMDHandler&#8217;:
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:305: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:393: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;bufferlength&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:394: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:420: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;bufferlength&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:546: warning: passing argument 7 of &#8216;RTUSB_VendorRequest&#8217; makes integer from pointer without a cast
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:546: error: too many arguments to function &#8216;RTUSB_VendorRequest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:557: warning: passing argument 7 of &#8216;RTUSB_VendorRequest&#8217; makes integer from pointer without a cast
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:557: error: too many arguments to function &#8216;RTUSB_VendorRequest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:609: error: &#8216;struct _RX_CONTEXT&#8217; has no member named &#8216;pUrb&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:611: error: &#8216;struct _RX_CONTEXT&#8217; has no member named &#8216;pUrb&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:612: error: &#8216;struct _RX_CONTEXT&#8217; has no member named &#8216;pUrb&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:613: error: &#8216;struct _RX_CONTEXT&#8217; has no member named &#8216;pUrb&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:738: warning: passing argument 7 of &#8216;RTUSB_VendorRequest&#8217; makes integer from pointer without a cast
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:738: error: too many arguments to function &#8216;RTUSB_VendorRequest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:835: warning: passing argument 7 of &#8216;RTUSB_VendorRequest&#8217; makes integer from pointer without a cast
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:835: error: too many arguments to function &#8216;RTUSB_VendorRequest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:846: warning: passing argument 7 of &#8216;RTUSB_VendorRequest&#8217; makes integer from pointer without a cast
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:846: error: too many arguments to function &#8216;RTUSB_VendorRequest&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:895: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:915: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:930: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1144: error: too many arguments to function &#8216;RTMPWPAAddKeyProc&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1226: error: too many arguments to function &#8216;RTMPWPARemoveKeyProc&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1318: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;CmdFromNdis&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1334: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1335: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;buffer&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:1341: error: &#8216;struct _CmdQElmt&#8217; has no member named &#8216;InUse&#8217;
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c: In function &#8216;usb_rtusb_probe&#8217;:
/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.c:2085: warning: unused variable &#8216;device&#8217;
make[2]: *** [/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2
xxx@xxx:~/RT73_Linux_STA_Drv1.0.3.6/Module$ sudo make install 
Password:
make -C /lib/modules/2.6.17-10-generic/build \
        INSTALL_MOD_DIR=extra SUBDIRS=/home/xxx/RT73_Linux_STA_Drv1.0.3.6/Module \
        modules_install 
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  DEPMOD  2.6.17-10-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
Network device directory /etc/sysconfig/network-scripts
Module configuration file /etc/modprobe.conf 
/sbin/depmod -a
xxx@xxx:~/RT73_Linux_STA_Drv1.0.3.6/Module$

---

### Post by OffHand on 2006-11-29
I think I have located the problem.

I think it is this step where it goes wrong:

Edit rtconfig.h, and comment out the line

 #include <asm-i386/atomic.h>  

If I uncomment that line it refuses to compile. If I do not change it I can compile it but I do not know if it's a required step: i.e. can I skip that part?

---

### Post by FrodoB on 2006-11-29
See:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by OffHand on 2006-11-29
> **FrodoB said:**
> See:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

Thanks for the tip but I can spell that guide backwards  :)

I managed to compile and install it. My device got recognized and all that. Still I was unable to configure my network. So I decided to leave it wired for now. Too much of a pain in ***.

P.S. I'm pretty good at networking, I worked as a tier 2 tech support agent at an isp. All Windows related though (except for the servers of course).
Windows is a huge step ahead of Linux with wireless internet. I do not care  who's to blame (the manufactures or linux). Until it gets easier it's back to the wire for me  :)

---

### Post by peterthewolf on 2006-11-29
I have a d-link g122 I am using it now on a ubuntu edgy clone called Linux Mint
Using the rt73 driver from serialmonkey, you will find that with a google search.
I am a complete amateur but by trial and error I have found that installing on the official 6.10 does not work but installing on LinuxMint version of 6.10 does
All I can assume is that the ralink drivers present in 6.10 kernel, which obviously do not work, interfere with the serialmonkey driver. But somehow linuxmint using "the same kernel" does work

Perhaps some real guru could get a proper explanation.

Edit 
Looking at above link perhaps the blacklist will help on official 6.10

perhaps instead of wire you could use you house main circuit see posting
[http://www.ubuntuforums.org/showthread.php?t=250481](http://www.ubuntuforums.org/showthread.php?t=250481)

---

### Post by nik_nah on 2006-11-30
> **OffHand said:**
> 
Windows is a huge step ahead of Linux with wireless internet. I do not care  who's to blame (the manufactures or linux). Until it gets easier it's back to the wire for me  :)

When I purchased my wireless setup recently, I had a feeling linux was going to be crap so I brought both a usb(rt73) and pcmcia card(madwifi).  I have gone back to the wire cause the wireless either can't scan for networks, loses connection after a few minutes, freezes the computer, need recompiling for wpa2, etc.

This was the case a few years ago with wired internet, I was hoping ndiswrapper may have fixed some of these problems.  Maybe in 1 or 2 years the situation will get better unless they keep on introducing new models requiring new drivers.

---

### Post by FrodoB on 2006-11-30
nik_nah;

Very poor form on you part, why would anyone want to spend their own time giving you free support. 

I guess you learned your motivational techniques from DIlbert's boss.

---

### Post by OffHand on 2006-11-30
> **FrodoB said:**
> nik_nah;

Very poor form on you part, why would anyone want to spend their own time giving you free support. 

I guess you learned your motivational techniques from DIlbert's boss.

I now this isn't directed towards me but what exactly do you mean?

---

### Post by FrodoB on 2006-11-30
Everyone prefers to work with and help people who have a positive attitude.

---

### Post by OffHand on 2006-11-30
> **FrodoB said:**
> Everyone prefers to work with and help people who have a positive attitude.

So what exactly do you think is negative about his attitude? 
I do not understand  :-k

---

### Post by FrodoB on 2006-11-30
I quote, " I had a feeling linux was going to be @#$%#".

Profanity, near profanity, and general negativism have no place in a public forum that can and is open to minors, or civil adults. 

The goals of this forum are to help people solve their problems and to show a spirit of ubuntu toward your fellow human beings.

---

### Post by OffHand on 2006-11-30
I'm not offended by the word crap. Either way, he's using Linux and bought two wireless card to try and get it working. And he was sort of right.

---

### Post by marinedalek on 2006-12-02
I read it as "I thought linux was going to be crap *to work with when configuring a wireless card*"

Anyway.

I've found an alternative way of configuring an RT73 USB WiFi adapter, once it's been installed. I ran through the guide but had to keep using "iwconfig rausb0 essid..." etc. each time the system rebooted. I wrote a custom section into interfaces so now the rausb0 section reads like so:

```
# rt73 wireless network device using static IP address
iface rausb0 inet static
pre-up ifconfig rausb0 up
pre-up iwconfig rausb0 essid MY_ESSID mode managed key restricted XXXXXXXXXX
address XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
network XXX.XXX.XXX.XXX
broadcast XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
auto rausb0
```

---

### Post by peterthewolf on 2006-12-04
One thing you must not do is use network manager to enable the rt73 dongle the use of this stops the dongle seeing its router.

---

