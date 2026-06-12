---
title: "Cannot get any of my 3 WiFi dongles to work with 14.04"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by rosen3 on 2014-08-20
Hi mates, 

This is my third attempt to switch from Windows to Linux, as previous two has always failed for the same reasons - getting wireless to work. But now I am very determined, I even did research on which wireless dongle works out of the box with Ubuntu and bought it. That was of course the ASUS N13. But guess what - it works for a while and then I am getting constant disconnects every 10 to 15 minutes. Then I have to unplug and plug back my usb wifi to get it working again. I tried some posts over the internet that claim they work but no chance. Here is what I've tried by now: 

1) tried to install the original driver from asus Linux_2302 (DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz) but failed to compile with this error: 

make[2]: *** [/home/xxx/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/xxx/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-35-generic'
make: *** [LINUX] Error 2

2) I did everything as described here: [http://ubuntuforums.org/showthread.php?t=2205444&p=12967859#post12967859](http://ubuntuforums.org/showthread.php?t=2205444&p=12967859#post12967859), and now my wifi dongle does not light up at all. I have no internet. 

3) I tried something related to the power management, cannot find the post now to paste it here, but it did not helped either. 

My other two wifi dongles are: TP-LINK TL-WN821N and TL-[COLOR=#545454][FONT=arial]WDN3200. Attached also wireless-info.txt[/FONT][/COLOR]

Please help me get my internet working.

---

### Post by weatherman2 on 2014-08-20
Looks like you are using an Alpha version of Ubuntu 14.10?  And it sounds like you are not very experienced with Ubuntu?  If that's true, I highly suggest NOT using an unstable alpha version of Ubuntu - and go back to Ubuntu 14.04 LTS, which will be supported for five years.  14.10 will be supported for only nine months even after it is released.

The wireless-info.txt file indicates your Asus N13 is the Realtek version (using RTL8192CU).  If you have the same problem in Ubuntu 14.04, try downloading the latest driver from Realtek's website for that chipset and trying to compile it.

---

### Post by kurt18947 on 2014-08-20
> **weatherman2 said:**
> Looks like you are using an Alpha version of Ubuntu 14.10?  And it sounds like you are not very experienced with Ubuntu?  If that's true, I highly suggest NOT using an unstable alpha version of Ubuntu - and go back to Ubuntu 14.04 LTS, which will be supported for five years.  14.10 will be supported for only nine months even after it is released.

The wireless-info.txt file indicates your Asus N13 is the Realtek version (using RTL8192CU).  If you have the same problem in Ubuntu 14.04, try downloading the latest driver from Realtek's website for that chipset and trying to compile it.

I doubt the download from Realtek will work, it hasn't since 12.10 to my knowledge unless there's been a recent update.  If indeed the chipset in question is RTL8192CU, there is a solution I've had good luck with in 14.04.  And yes, my generic RTL8192CU based adapter works for several minutes then stops. It does sound like that the chipset is using the 'baked-in' driver.  I've found that if I turn off wifi, wait a few seconds and turn it back on the adapter will work for a few minutes more.

A more satisfactory solution can be found here:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

This uses Realtek's driver but fixes some flaws that prevent Realtek's driver installing.  I simply copy & paste the shaded lines of text into a terminal, one at a time.  Once everything completes I restart and I'm in business.

One way to determine which driver is in use is to type "lsmod" in a terminal.  This will list the modules (sort of like Windows drivers) in use.  When I'm using the 'broken' driver, the module in use shows as rtl8192cu.  The fixed module shows up as 8192cu.

---

### Post by rosen3 on 2014-08-21
Hi mates, 

Thank you very much for your help. I had the same problems in 14.04 LTS and I updated to 14.10 in a hope that there will be some network fixes in there. 

Anyway, to clean the garbage from numerous attepmts to get my internet stable, I did a clean install of 14.04 LTS and then installed the rtl8192cu-fixes as described in the Git readme file. Now my internet is very stable and very fast for over two hours now. I am very confident the problem is resolved permanently as before I installed the fixes my internet connection dropped every 3-4 minutes. Now I am even downloading several torrents at the same time at a very stable speed. 

Thank you again guys.

---

