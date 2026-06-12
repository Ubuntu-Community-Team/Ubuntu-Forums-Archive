---
title: "D-link AirPlus G wireless PCI card."
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by NickL87 on 2006-12-13
Hi

I have been using Ubuntu on my laptop for some time now, and i am actually very pleased with the system. So i decided to get rid of windows totally, and install Ububtu (Edgy) on my desktop computer to.

My problem is that i cant get my wireless network card working (D-Link DWL-G510). I have tried installing ndiswrapper and installing the following driver, from the ndiswrapper driver list: [ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip](ftp://ftp.dlink.com/Wireless/dwlg510/Drivers/dwlg510_driver_100.zip)
But this did not work, as far as i know anyway. ](*,) 

The terminal prints the following when i enter the command iwconfig:

nick@nick-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"wn"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

And the driver looks as if it is correcly installed:

nick@nick-desktop:~$ sudo ndiswrapper -l
Password:
Installed drivers:
mrv8k51         driver installed 

So if anyone can help me i would become a very happy man ;)

---

### Post by FrodoB on 2006-12-13
Can you give us the output from lspci for your device?

lspci -v

---

### Post by NickL87 on 2006-12-14
> **FrodoB said:**
> Can you give us the output from lspci for your device?

lspci -v

yes it is the following:

```
00:09.0 Network controller: RaLink Unknown device 0302
        Subsystem: D-Link System Inc Unknown device 3c09
        Flags: bus master, slow devsel, latency 32, IRQ 10
        Memory at e6000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
```

So the driver I installed is obviously not working, so now I am really stuck ](*,)

---

### Post by FrodoB on 2006-12-14
See:

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

---

### Post by NickL87 on 2006-12-15
> **FrodoB said:**
> See:

[http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

Thanks :) worked like a charm.

---

