---
title: "SAFECOM Wireless PCMCIA Card SWLC-54108 does not working in 8.10"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by jackygurui on 2008-11-28
I had an old wireless PCMCIA card made by safecom. The model number is SWLC-54108. It was working in the previous version of Ubuntu, however I couldn't get the 8.10 system to boot up when the card is connected.

I tried LiveCD without install, upgrade install, fresh install. the symptom is whenever I connect the card to the laptop, the entire system hangs up, and the CAP LOCK is FLASHING on and off. Very wired and spooky.

I've googled a bit and couldn't find a simple solution. Apart from recompile the kernel using the driver downloaded from safecom. But that means every time, when there is an kernel upgrade, I need to compile it over again. Plus I don't know how, although I tried once and it failed.

According to the official website([http://safecom.cn/code/support/DMF.aspx?pid=317](http://safecom.cn/code/support/DMF.aspx?pid=317)), there is no difference between SWLC-54108 and SWLCT-54125. So I've dowloaded it from [http://safecom.cn/code/product/WLAN/SWLCT-54125/driver/Linux.zip](http://safecom.cn/code/product/WLAN/SWLCT-54125/driver/Linux.zip)

The zip file contains a deb file, driverLinux_i386.deb. I installed it but failed to re-compile the kernel during post-installation process.

Is there any chance that Ubuntu will support this card in the future? Or anyone can help me to get this card working?

Many thanks.

---

### Post by jackygurui on 2008-11-28
By the way, the kernel I am using is 2.6.27-7-generic.

---

### Post by old_codger on 2010-01-30
This card works well with linux. All you need to do is blacklist the acx driver by placing an entry in the...

/etc/modprobe.d/blacklist.conf

file. It should say...

blacklist acx

Then use the windows driver using ndiswrapper following the instructions here...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing) Windows driver

---

