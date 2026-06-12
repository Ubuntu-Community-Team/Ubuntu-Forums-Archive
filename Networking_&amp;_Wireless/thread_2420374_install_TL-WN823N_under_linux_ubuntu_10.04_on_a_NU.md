---
title: "install TL-WN823N under linux ubuntu 10.04 on a NUC EBOX-3310MX-L3U4 from DMP Electro"
date: 2019-06-04
forum: Networking &amp; Wireless
---

### Post by ecoluxpc on 2019-06-04
Model: TL-WN823N

Hardware Version: V3





Hello

I'm new here in the forum so i hope i post it at the right place...

   
  I'm trying for a customer to install the TL-WN823N on his NUC EBOX-3310MX-L3U4 from DMP Electronics.
 
 Here is the page of the device itself if you need [http://www.compactpc.com.tw/product.aspx?act=detail&id=85](http://www.compactpc.com.tw/product.aspx?act=detail&id=85)
   
  I think the PCU and architecture is compatible with TL-WN823N
   
  Ubuntu 10.04 is installed on it.
   
  The USB device is detected but i can't succeed to compile the driver...
   
  here is the log of the error
   
  [TABLE="width: 500"]
[TR]
[TD] ecoluxpc@ecoluxpc-desktop:~$ sudo su
 [sudo] password for ecoluxpc: 
 root@ecoluxpc-desktop:/home/ecoluxpc# cd Bureau
 root@ecoluxpc-desktop:/home/ecoluxpc/Bureau# cd linux
 root@ecoluxpc-desktop:/home/ecoluxpc/Bureau/linux# cd Driver
 root@ecoluxpc-desktop:/home/ecoluxpc/Bureau/linux/Driver# make
 "******************************************"
 "NO SKRC,we will use default KSRC"
 "******************************************"
 make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-38-generic/build M=/home/ecoluxpc/Bureau/linux/Driver  modules
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
 "******************************************"
 "NO SKRC,we will use default KSRC"
 "******************************************"
   CC [M]  /home/ecoluxpc/Bureau/linux/Driver/core/rtw_p2p.o
 /home/ecoluxpc/Bureau/linux/Driver/core/rtw_p2p.c: In function &#8216;ro_ch_handler&#8217;:
 /home/ecoluxpc/Bureau/linux/Driver/core/rtw_p2p.c:3634: error: implicit  declaration of function &#8216;cfg80211_remain_on_channel_expired&#8217;
 [B][I][COLOR=#d0121b]make[2]: *** [/home/ecoluxpc/Bureau/linux/Driver/core/rtw_p2p.o] Error 1
 make[1]: *** [_module_/home/ecoluxpc/Bureau/linux/Driver] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'[/COLOR][/I][/B]
 make: *** [modules] Error 2
 root@ecoluxpc-desktop:/home/ecoluxpc/Bureau/linux/Driver# [/TD]
[/TR]
[/TABLE]
   
   
  Firstly when i just unzipped the driver and followed instructions, i  got error about unexpected syntax, and i understood the " ( " in the  filename of the folder was not liked by the compile, so i renamed the  name of the folder to something simpler like "linux" and retried again  the "make" command but i came up with this above pasted error...
 
 
 As you have guessed i'm not a Linux guru, i just want this NUC barebone  able to go on Internet before giving it back to my customer who had  windows XP before...
  so if you could guide me step by step that would be great
   
  If we suceed i will offer a (50% discount available in my store :p (kidding... but why not...)
   
  Thanks a lot in advance

---

### Post by TheFu on 2019-06-04
> Ubuntu 10.04 is installed on it.
Support for 10.04 ended for most versions in 2013 and for the server in 2015.
It should never be allowed on the internet. There are many remote root exploits that exist in the unsupported, unpatched, versions of every OS, including unsupported versions of Linux and Ubuntu.

The first step is to load a supported OS. Probably a version of 18.04 is what you need, I'd support Ubuntu-Mate or Xubuntu since the system is probably from 2010.  See how that works, then attack any issues with it.

10.04 is like trying to get Win95 working again in the Linux world.

---

### Post by chili555 on 2019-06-04
> **TheFu said:**
> Support for 10.04 ended for most versions in 2013 and for the server in 2015.
It should never be allowed on the internet. There are many remote root exploits that exist in the unsupported, unpatched, versions of every OS, including unsupported versions of Linux and Ubuntu.

The first step is to load a supported OS. Probably a version of 18.04 is what you need, I'd support Ubuntu-Mate or Xubuntu since the system is probably from 2010.  See how that works, then attack any issues with it.

10.04 is like trying to get Win95 working again in the Linux world.Amen, brother!

Please note: > 
[COLOR="#FF0000"]2.6.32-38[/COLOR]-generic

There are not very many of us around here that ever worked with kernel version 2.6 and precisely none of us still have an installation with which to help you. In fact, I am quite confident that the driver that you attempted to compile was written for at least a 3.xx kernel and maybe even later. 

Please install 18.04 LTS and, if the wireless still isn't working, we'll be very happy to help.

---

### Post by ecoluxpc on 2019-06-04
i agree with you guys

I obviously tried to install on this machine the latest ubuntu version i downloaded first, but the installation failed and was rejected 

Then i checked the compatible OS from the manufacter 

System Specification
CPU
Vortex86MX+ (EBOX-3310MX series)

Main Memory
1GB DDR2
( 32-bit DRAM bus, EBOX-3310MX series)

BIOS
AMI BIOS


Supported Operating System
Windows XP Home/ Pro.
Windows XP Embedded
Windows Embedded CE

Supported Linux Distribution list:
1. Debian 4.0
2. Debian 5.0
3. Ubuntu 8.04
4. Ubuntu 8.10
5. Ubuntu 9.04
6. Ubuntu 10.04
7. Edubuntu 9.04 (Ubuntu 8.10 base)
8. Easy Peasy 8.10
9. Puppy 4.2.1
10. Puppy 4.1.2
11. WattsOS2 Warp30 (Ubuntu 8.10 base)

&#8251; Ubuntu 8.10 / WattOS, Remember to enable the Media Port Instruction option for VGA compatible. Resource (Kernel/Drivers Package)


With those information do you recommand me something better/newer than ubuntu 10.04 ?

Thank you very much for your help so far

---

### Post by TheFu on 2019-06-04
Supported OS lists means little in the Linux world.  If it works, then it is supported.
10.04 is NOT supported **anywhere** today.  The only time I'd be worried about official "support" is for E911 or emergency services or systems used in an industrial control centers like a nuclear, chemical, ATC, or space control centers.  If you are dealing with those, time to buy new hardware from the vendor.

There is a 32-bit Lubuntu 18.04: [https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/](https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/) - be certain to get the 32-bit version.  Or try a 32-bit Debian install.  

Or there are other options:
* Get a Raspberry Pi v3+ (~ $45) - it will be faster, more capable than that system.
* Get some other embedded system, SOC -  
** AtomicPI (this has a 64-bit Atom CPU - ~ $60), 
** APU2C4 (~ $150) - this has a 64-bit AMD CPU with support for AMD-v. 
** Pine64
** RockPro64
** ODroid N1/N2, or others.
All use less than 15W of power and I'd bet they will all be faster.

Anyways, there are options ... which all end with an 18.04 install of some flavor.  We could provide better suggestions if we knew the purpose of the machine.  A NUC that old won't be sufficient as a video player these days. The GPU hardware is too limiting.

---

### Post by him610 on 2019-06-04
> Model: TL-WN823N
Operation is very good using ?buntu 19.04 or 19.10. See my post, [https://ubuntuforums.org/showthread.php?t=2420042]("https://ubuntuforums.org/showthread.php?t=2420042")

---

### Post by chili555 on 2019-06-05
Since your real issue is this: > 
CPU
Vortex86MX+ (EBOX-3310MX series)

I am beginning to suspect that you might not get Ubuntu 18.04 32-bit to load. If not, then I suggest that you download this: [https://static.tp-link.com/2018/201805/20180514/TP-Link_Driver_Linux_series8_beta.zip](https://static.tp-link.com/2018/201805/20180514/TP-Link_Driver_Linux_series8_beta.zip) The accompanying page says: Operating System: Linux (kernel [COLOR="#FF0000"]2.6.24[/COLOR] ~ <4.9.60)

Please try to install that driver and let me know the result. It has been a long time since I worked with kernel version 2.6 or drove my old 1967 Ford, but let's see what we can do.

---

### Post by TheFu on 2019-06-05
Yep. With that CPU, the exact CPU capabilities will be very important to know.
/proc/cpuinfo has that. Saw the Vortex86MX+ is missing a capability that Intel i686 CPUs have.
>  intended for i686 may fail because the CPU lacks a Conditional Move (CMOV) instruction.

[https://help.ubuntu.com/lts/installation-guide/i386/ch02s01.html](https://help.ubuntu.com/lts/installation-guide/i386/ch02s01.html) has more specifics for 18.04.> 
However, Ubuntu bionic will not run on 586 (Pentium) or earlier processors. Support for i586 and lower processors, as well as for i686 processors without the cmov instruction,** was dropped in Ubuntu 10.10**. Most i686 and later processors are still supported.

So ... I'd look to Debian.

---

