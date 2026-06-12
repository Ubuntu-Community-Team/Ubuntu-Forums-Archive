---
title: "internet connection intermittent"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by coalhole on 2011-08-05
I'm using Ubuntu 10.4 on a samsung N130 netbook... I've set bios to connect to the internet automatically on boot... Sometimes it doesn't connect and I can't find any way to connect without having to reboot... sometimes a couple of times before it connects.... Any suggestions for what I can do about this inconsistency?

---

### Post by amjjawad on 2011-08-05
> **coalhole said:**
> I'm using Ubuntu 10.4 on a samsung N130 netbook... I've set bios to connect to the internet automatically on boot... Sometimes it doesn't connect and I can't find any way to connect without having to reboot... sometimes a couple of times before it connects.... Any suggestions for what I can do about this inconsistency?

I'm sorry but why you set BIOS to connect to the internet automatically? any reason for that?
If your Wireless Connection is ON and your Wireless Router is on too **AND/OR** your LAN Cable is plugged in, then by default, you are connected to the internet.

I do have the same machine at home (not mine though) and it has Windows 7 Starter but I'll have a look at that option. I'm not aware that this option does exist because I don't think it's needed but I'll have a look.

Edit:
I just checked and there is an Option under Boot Menu that says: "Wireless Always ON". 
Is that what you were referring to?

---

### Post by coalhole on 2011-08-05
> **amjjawad said:**
> I'm sorry but why you set BIOS to connect to the internet automatically? any reason for that?
If your Wireless Connection is ON and your Wireless Router is on too **AND/OR** your LAN Cable is plugged in, then by default, you are connected to the internet.

I do have the same machine at home (not mine though) and it has Windows 7 Starter but I'll have a look at that option. I'm not aware that this option does exist because I don't think it's needed but I'll have a look.

Edit:
I just checked and there is an Option under Boot Menu that says: "Wireless Always ON". 
Is that what you were referring to?
sorry... I should have said that the bios setting was "wireless always on"

---

### Post by amjjawad on 2011-08-05
> **coalhole said:**
> sorry... I should have said that the bios setting was "wireless always on"

Never mind :)

From Terminal, please post the output of 

```
sudo lshw -C network

```
Please wrap up the text with "CODE" tags or highlight the output and click "#".

---

### Post by coalhole on 2011-08-05
> **amjjawad said:**
> Never mind :)

From Terminal, please post the output of 

```
sudo lshw -C network

```
Please wrap up the text with "CODE" tags or highlight the output and click "#".
All I got was "command not found"... Is there somewhere else I should have looked for the output? please note i'm totally new to command lines....

---

### Post by amjjawad on 2011-08-05
> **coalhole said:**
> All I got was "command not found"... Is there somewhere else I should have looked for the output? please note i'm totally new to command lines....

1) Open Terminal (Applications > Accessories > Terminal ) 

2) Copy the command I posted and paste it.

3) Press Enter.

4) Done :)

---

### Post by coalhole on 2011-08-05
Here's what I got this time after your instructions...


 *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:c6:4a:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE ip=192.168.1.3 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:59:14:23
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
robert@robert-laptop:~$ #

---

### Post by amjjawad on 2011-08-05
> **coalhole said:**
> Here's what I got this time after your instructions...


 ```
*-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:b6:c6:4a:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**[COLOR=Red]rtl819xE[/COLOR]** ip=192.168.1.3 latency=0 multicast=yes wireless=802.11bg
       resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:54:59:14:23
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:3000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
```robert@robert-laptop:~$ #

[http://ubuntuforums.org/showpost.php?p=10983947&postcount=5](http://ubuntuforums.org/showpost.php?p=10983947&postcount=5)

Follow the steps in the above link.
I had a similar issue but different driver.
[http://ubuntuforums.org/showthread.php?t=1643545](http://ubuntuforums.org/showthread.php?t=1643545)

---

### Post by coalhole on 2011-08-05
Many thanks for your patience with a newby... That seems quite comprehensible... I'll give it a try but it'll be a few boots before I know if its made a difference...

---

### Post by amjjawad on 2011-08-05
> **coalhole said:**
> Many thanks for your patience with a newby... That seems quite comprehensible... I'll give it a try but it'll be a few boots before I know if its made a difference...

You are welcome and we all were new to Linux so don't worry about that :)

Sure, but please let us know what will happen with you ;)

---

### Post by coalhole on 2011-08-06
Your suggestion seems to have worked... connection OK after several boots... Many thanks... Coalhole

---

### Post by amjjawad on 2011-08-06
> **coalhole said:**
> Your suggestion seems to have worked... connection OK after several boots... Many thanks... Coalhole

Glad to know it's working right now.
However, please let us know in case something happened :)

Enjoy :)

Keep this thread as it's and after few days, if everything will remain fine, you can mark it as SOLVED.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

