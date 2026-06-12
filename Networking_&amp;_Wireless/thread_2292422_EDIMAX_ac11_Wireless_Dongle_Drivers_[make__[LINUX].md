---
title: "EDIMAX ac11 Wireless Dongle Drivers [make: *** [LINUX] Error 2]"
date: 2015-08-27
forum: Networking &amp; Wireless
---

### Post by logix-2006 on 2015-08-27
I recently purchased this dongle: [http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_ac450/ew-7711mac](http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_ac450/ew-7711mac) because it's supposed to work with Linux.

  I downloaded the drivers from their site, but when I try to 'make' it, I get the following error:   
```
make[2]: *** [/home/user/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/user/Downloads/mt7610u_wifi_sta_v3002_dpo_20130916/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-38-generic'
make: *** [LINUX] Error 2
```

Going off this old thread: [http://ubuntuforums.org/showthread.php?t=2270202](http://ubuntuforums.org/showthread.php?t=2270202) the problem is likely due to the drivers being outdated.

   I found this github:[https://github.com/coolshou/mt7610u](https://github.com/coolshou/mt7610u) but I'm a little afraid of blindly running commands without properly understanding them

Am I on the right track? if I follow the instructions from the older thread, but substitute the mt7610u would that work?

   lsusb
 ```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 13d3:5165 IMC Networks 
Bus 001 Device 005: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 7392:a711 Edimax Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``` 


 NOTE: the wireless drivers for my laptop's internal card works fine. Plan is to disable it and use the Edimax exclusively.


The readme file that came with the drivers refers to the device as a 'Ralink RT2870 USB ABGN WLAN Card' but I believe this is a mistake.

---

### Post by Hadaka on 2015-08-27
Hi, from your lsusb ..
Bus 003 Device 002: ID [COLOR=#ff0000]7392[/COLOR]:[COLOR=#ff0000]a711[/COLOR] Edimax Technology Co., Ltd 

please post the output of..
```
 uname -a 
```

To Load:
[CODE]sudo apt-get install --reinstall build-essential linux-headers-generic[CODE]

---

### Post by logix-2006 on 2015-08-27
> **Hadaka said:**
> Hi, from your lsusb ..
Bus 003 Device 002: ID [COLOR=#ff0000]7392[/COLOR]:[COLOR=#ff0000]a711[/COLOR] Edimax Technology Co., Ltd 

please post the output of..
```
 uname -a 
```

To Load:
```
sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
```


```
Linux user-K46CB 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

I messaged EdiMax customer service, here's the respond I got from them 
> 
The official driver from our website only supports Linux kernel     versions 2.6.18~3.14 and any versions beyond that are not     supported.  At this moment, we don't have any schedule for an     updated Linux driver.  If your Linux is running the latest kernel,     you may need to look for another alternative.  Sorry for able to     help you here.  Thanks! 



Time to roll back the kernel? or could I use a wrapper on the W10 or W8.1 driver?

---

### Post by Hadaka on 2015-08-27
Hi, sorry about the previous post..this should work for you and your current kernel

```
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/porjo/mt7601.git](https://github.com/porjo/mt7601.git) 
cd mt7601/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta
```

*Ignore any warnings but post any errors,
thanks

---

### Post by logix-2006 on 2015-08-27
> **Hadaka said:**
> Hi, sorry about the previous post..this should work for you and your current kernel

```
sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/porjo/mt7601.git](https://github.com/porjo/mt7601.git) 
cd mt7601/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta
```

*Ignore any warnings but post any errors,
thanks

Thanks for the help. Ran everything with no errors. Tried unplugging and  plugging in the wireless adapter, still no lights (on the adapter) or  5.0GHz networks detected. [s]Going to restart the computer to see if  that helps.[/s] No luck even after restarting the laptop. 

 

I do have a question though, Isn't the github you linked for the mt7601? The official drivers are stored in this folder "**mt7610u**_wifi_sta_v3002_dpo_20130916" doesn't that mean I need the mt7610u?

Someone on the amazon page for this adapter suggested using the  'rtl8812au' driver for this adapter, but I don't really get how realtek  drivers would help me run a mediatek device.

EDIT: GOT IT WORKING
git clone [https://sanrath@bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit.git](https://sanrath@bitbucket.org/sanrath/mediatek_mt7610u_sta_driver_linux-64bit.git) and then I just followed your instructions

now... if only I could disable that needless white indicator light.

EDIT2 : It's working.. but it's extremely slow.
Speedof.me reports latency of 14104ms. Speedtest.net can't even decide on a server, and most websites time out. 

In windows my latency was 4ms and download speeds were ~200Mbps. 

I  guess these drivers need some work. How do I un-install them so I can  try another one. Looks like mt7610u is what I'm looking for though.

---

### Post by Hadaka on 2015-08-28
[URL="http://ubuntuforums.org/showthread.php?t=2210930"]http://ubuntuforums.org/showthread.php?t=2210930
post #6
[/URL]

---

### Post by logix-2006 on 2015-08-28
> **Hadaka said:**
> [URL="http://ubuntuforums.org/showthread.php?t=2210930"]http://ubuntuforums.org/showthread.php?t=2210930
post #6
[/URL]

Unfortunately, the drivers from the mediatek website don't compile either. 

I'm still trying to get these drivers to work though:
[http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)


Playing around in /etc/Wireless/RT2870STA/RT2870STA.dat

I found that 13 and 15 are the AC modes. In both I'm able to get a connection speed of ~170mbps (Windows get the full 433)

However, I can't browse the web properly in those modes. I tried lowering the TX power from 100 to 20, but that didn't do much either. 

In Wireless mode 8, I'm able to browse the internet, but I'm limited to wireless N. Which defeats the purpose of this adapter. 

SideNote: This adapter is only capable of connecting to 5G networks. I have my laptop's internal wireless card for 2.4G

---

### Post by alfred7 on 2015-08-28
I also use the patched driver bases on [http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/](http://hprath.com/2014/06/cisco-linksys-ae6000-ac580-media-tek-mt7610u-mt7630u-mt7650u-linux-x64-driver-patch/)

I have a mt7610u - lsusb shows:```
Bus 001 Device 037: ID 0e8d:7610 MediaTek Inc.

```

Same as you, I can only stuck on wireless mode 5 or 8; otherwise, in any mode support AC, the network is not workable - can connect AC wireless AP, but nearly cannot send out anything (check with wireshark). It looks like a VHT problem, maybe the driver is not right, but I have no idea how to fix it.

You can see some debug output by "iwpriv ra0 devinfo" and "iwpriv ra0 stainfo", the output is in syslog; you can refer to my [output]("https://bitbucket.org/fbid/mediatek_mt7610u_sta_driver_linux-64bit/issues/4/vht-issue#comment-20879793").

Actually I also made more changes, because the WIFI regulation setting in codes is not up to date, it does not support all 5G channels in my country.

---

### Post by logix-2006 on 2015-08-28
Just tried installing kernel 3.13 but compiling the official drivers still fails.

---

### Post by logix-2006 on 2015-08-31
Spoke with some people who purchased this adaptor. 

They are apparently using this driver: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) 

```
cd /usr/src/rtl8812AU_8821AU_linux
sudo make clean 
sudo make 
sudo make install
sudo modprobe -a 8812au
```
But no lights. Am I supposed to do anything before that? I've noticed in alot of tutorials, there's mention of a 'blacklist', do I need to do anything with that?

---

### Post by alfred7 on 2015-09-01
from this post, [http://amazeballsysadmin.blogspot.com/2015/07/getting-mt7610u-edimax-7711macsabrent.html](http://amazeballsysadmin.blogspot.com/2015/07/getting-mt7610u-edimax-7711macsabrent.html)

I think your "[COLOR=#000000][FONT=Ubuntu Mono]7392:a711 Edimax Technology Co., Ltd" is very likely to be mt7610u   :)
[/FONT][/COLOR]

---

### Post by steve254 on 2016-05-07
> **alfred7 said:**
> from this post, [http://amazeballsysadmin.blogspot.com/2015/07/getting-mt7610u-edimax-7711macsabrent.html](http://amazeballsysadmin.blogspot.com/2015/07/getting-mt7610u-edimax-7711macsabrent.html)

I think your "[COLOR=#000000][FONT=Ubuntu Mono]7392:a711 Edimax Technology Co., Ltd" is very likely to be mt7610u   :)
[/FONT][/COLOR]

Thanks for pointing me in the right direction. Now getting much better speeds up and down after using the info in your link
I had already downloaded Sanrath's driver so used the right mouse button and opened a terminal window from file manager
-guess you can tell i'm fairly new at this
Have given up on Windows 10, really enjoying Linux

---

