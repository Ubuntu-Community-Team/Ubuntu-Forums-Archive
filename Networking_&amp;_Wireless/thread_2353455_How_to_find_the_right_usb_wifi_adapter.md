---
title: "How to find the right usb wifi adapter"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by ubu112 on 2017-02-21
Please,can someone suggest to me which can be the right usb wifi adapter,I have Acer Aspire One AOA 150/ZG5 with Ubuntu 16.04 LTS.It works with wireless "g",I'd like to improve my connection speed passing to Wireless "n" or "ac" at 2,4 Ghz.But I have to find the right adapter,with the right drivers and kernel.Probably I need to know how to find right drivers and how update the kernel version,because I'm a beginner.Can someone help me.Thank you

---

### Post by Geoffrey_Arndt on 2017-02-21
After testing at least a dozen adapters over the past few years, the most Linux compatible "plug and play" usb wifi adapters are provided by Panda.

These are available via Amazon, New Egg also.   Costs are reasonable (between $10 and $30 USD).  These require no driver installs or compiling.   No need to reinstall upon kernel updates.

Just plug in and you should see your wireless networks.   (may need to reboot on some models).

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by gordintoronto on 2017-02-22
Interesting... I searched Panda on several Canadian vendors, but the only hit I found was for an "N" adapter at amazon.ca.

---

### Post by SeijiSensei on 2017-02-22
[https://ubuntuforums.org/showthread.php?t=2353297](https://ubuntuforums.org/showthread.php?t=2353297)

---

### Post by ubu112 on 2017-02-24
First of all,thank you,for your advices.Have you some suggestion about wireless AC usb adapters? Thank you

---

### Post by SeijiSensei on 2017-02-25
Took me a couple of seconds to find this: [https://forums.linuxmint.com/viewtopic.php?t=234143](https://forums.linuxmint.com/viewtopic.php?t=234143)

---

### Post by ubu112 on 2017-02-25
Thank you again for your help.But now I don't really know what to do,because I have 2 pc, with Windows, that works with wireless AC and the oldest Acer with Ubuntu 16.04 LTS that works at 2,4 Ghz with a wireless card G.The problem is that Ubuntu 16.04 LTS has kernel 4.4,but no adapters seem to support kernel 4.4,if I buy an adapter AC I can use it for Windows,if I buy an adapter N must be the right one because I'm not able to update the kernel.So,what would be your choice?Thank you

---

### Post by Geoffrey_Arndt on 2017-02-26
The Panda Ultra 150 802.11n works with Linux, Mac, Windows and there is no worry about kernel issues (present or updates).   For about $10.00 USD, it works great (just plug & go).  

They also have dual-band n adapter (PAU07 n600).   Vendor supports product better than most (email or phone).

---

### Post by QIII on 2017-02-26
For about $30, I bought a TP-LINK AC1200 T4U

AC 1200, dual band, just plug it in and go.


Edit:
Hmmm, wait.  I think I actually had to install the rtl8812au driver, but that is simplt.

---

### Post by chili555 on 2017-02-26
I have and use this: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG)

---

### Post by ubu112 on 2017-02-26
Thank you very much "chili555" for your answer.This adapter will work with Ubuntu 16.04 LTS,I mean is plug & play without driver,kernel problems on my old pc?and pass from wireless g to n?Thank you

---

### Post by jeremy31 on 2017-02-26
> **QIII said:**
> For about $30, I bought a TP-LINK AC1200 T4U

AC 1200, dual band, just plug it in and go.


Edit:
Hmmm, wait.  I think I actually had to install the rtl8812au driver, but that is simplt.

There have been some complaints about the rtl8812au-dkms not working correctly on kernel updates and has to be compiled and installed again
The fix is to go to the /usr/src/ folder and find the source dkms.conf and change the MAKE= line to
```
MAKE="'make' all KVER=${kernelver}"
```

---

### Post by ubu112 on 2017-02-26
Thank you "jeremy31"for "the fix".Have you,please,some advices to give me about usb adapters, for Ubuntu 16.04 LTS,plug & play,because I'm a beginner,that works with wireless n or ac,from my old pc?Thank you

---

### Post by jeremy31 on 2017-02-26
I have the same USB adapter that chili555 recommends as a backup.  It is wireless n, no ac but gets good reception and you just plug them in and they work in Ubuntu 16.04.

I also have a TP-Link WN723N but it has bad reception because of its size and isn't supported by the kernel

---

### Post by ubu112 on 2017-02-26
Thank you again,at the end I fund the right one

---

### Post by uRock on 2017-02-26
I see you have already bought one, but wanted to give mention to the one I've bought several times. I get the one for the RaspberryPi from Canakit. 
They are great and seem to have better range than to factory WiFi NICs that have came with the systems I own. 

If I had any complaint, it would be the the cards not being capable of packet injection with Kali. The only affects those wanting to do penetration testing.

---

### Post by SeijiSensei on 2017-03-07
I tried today to install the TP-Link AC 1200 USB adapter but cannot get the driver to compile.  I have a brand-new installation of Kubuntu 16.04.2 with kernel 4.8.0-36-generic.  Installing with "sudo apt-get install rtl8812au-dkms" downloads the required objects but the compilation fails with
```

 In function &#8216;rtw_android_priv_cmd&#8217;:
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/rtw_android.c:
577:6: error: implicit declaration of function &#8216;is_compat_task&#8217; [-Werror=implicit-f
unction-declaration]
  if (is_compat_task()) {
      ^
cc1: some warnings being treated as errors
scripts/Makefile.build:289: recipe for target '/var/lib/dkms/rtl8812au/4.3.8.12175.
20140902+dfsg/build/os_dep/linux/rtw_android.o' failed
make[2]: *** [/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build/os_dep/linux/
rtw_android.o] Error 1
Makefile:1491: recipe for target '_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140
902+dfsg/build' failed
make[1]: *** [_module_/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/build] Erro
r 2

```
I find all the references to Android puzzling.  Why would a Linux kernel module for Ubuntu need anything having to do with Android?

I tried installing from source on Kubuntu 14.04 but got different compilation errors.  I also tried upgrading my 14.04 kernel to the latest available from the 4.x series and got other errors.

---

### Post by jeremy31 on 2017-03-07
With the 4.8 kernel you may want to try [https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)

I can't answer the Android question but the source code may have been multi platform

---

### Post by SeijiSensei on 2017-03-07
Thanks so much, Jeremy!  I downloaded the driver from the git archive, and it built cleanly!  Even those "android" modules.  Even better it works with my 14.04 installation with the kernel upgraded to 4.4.0-64-generic.  Now all I have to do is figure out how to register this with dkms, or I'll have to recompile with each kernel change.  Not the end of the world.

Kubuntu's network manager now reports my connection speed is 867 Mbps, up from 72 or so with my TP-Link N adapter!  I'll have to run a few tests downloading large files from my server.

---

