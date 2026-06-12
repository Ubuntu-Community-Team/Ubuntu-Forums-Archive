---
title: "wireless limited to 11mbps"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by velozoom on 2006-11-04
I finally got my wireless card working but I can't seem to change the speed up from 11mpbs.  It's a b/g card, a Broadcom 4311, and should be capable of full 54mpbs.  My Wrouter is working fine with a g-connection to a WinXP box in the other room.  

The driver for the nic was isntalled using FWCutter and I am not using ndsiwrapper.  

```

$ iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:"XXXXXX"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:C8:CB:46   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=85/100  Signal level=-49 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



$ifconfig
eth1      Link encap:Ethernet  HWaddr 00:14:A5:E7:5F:F2  
          inet addr:10.10.10.103  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fee7:5ff2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3392197 (3.2 MiB)  TX bytes:463468 (452.6 KiB)
          Interrupt:255 Base address:0x8000 


```

How do I enable the nic for g?  I've tried changing with ethtool but I either can't or don't know the proper syntax.

Thanks for any help.

---

### Post by spd106 on 2006-11-04
As far as I know the bcm43xx driver is still limited to 11 Mb/s. I can't be certain since I bought an atheros based card as a replacement, so I'm not up to date on the latest developments. 
There may have been new updates to edgy so it might be worth searching the forum and the wiki.

---

### Post by wieman01 on 2006-11-04
This limitation may apply to the Linux driver, but certainly not to the native Windows driver. That's why I advise you to install "ndiswrapper" & make use of your Windows driver (get the latest version). Then follow this guide:

[http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by velozoom on 2006-11-04
ok, I will try the Winblows driver and ndiswrapper.  I was hoping to avoid that but c'est la vie, non?  

Thanks for the advice

---

### Post by wieman01 on 2006-11-04
> **velozoom said:**
> ok, I will try the Winblows driver and ndiswrapper.  I was hoping to avoid that but c'est la vie, non?  
Understand that... It's not my preferred solution, either, but after I had messed around with the Linux driver for day I eventually decided that I would save myself a lot of trouble when install "ndiswrapper". And so I did... Have never had an issue since.

C'est la vie! :-)

---

### Post by velozoom on 2006-11-06
wow....that fried both my NICs....now I don't have wired net access either.  Is there a good tutorial on how to configure nics for linux?  I don't even know where to look to see what went wrong....ugh

[edit] when I run iwconfig my eth0 (wired) only says 'no wireless extensions'.....how I did get this trying to use wireless?  argh!

---

