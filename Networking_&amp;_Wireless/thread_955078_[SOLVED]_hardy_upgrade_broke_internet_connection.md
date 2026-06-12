---
title: "[SOLVED] hardy upgrade broke internet connection"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by dresnu on 2008-10-21
Hello. I just upgraded to hardy from gutsy. This operation was done normally through Adept by downloading all packages. Upgrade was smooth and connection to the net worked fine until I restarted the computer. We 're talking about an ethernet connection here, no wifi.

The problem is that web pages load until a point and then stop. I tried with konqueror opera and firefox with the same result. Network manager seems to be connected to the rooter and dns settings are fine. I can ping web locations from the terminal too.

Ideas are welcome :)

EDIT: Also my connection per se works fine in windows so its not a router or provider problem

[COLOR="Red"]EDIT: The title is somehow misleading as it was discovered later that the problem has almost surely nothing to do with hardy upgrade and it probably is a hardware issue[/COLOR]

---

### Post by pytheas22 on 2008-10-21
What is the output of:
```

lspci -nn
lshw -C Network
```

Also, do other services besides ping and http work normally?  For example, can you connect to an ftp or ssh server and stay connected for a long period of time?

---

### Post by dresnu on 2008-10-22
Nada, now connection is completely broken. I suspect it is an ethernet problem. I can't even enter the configuration page of the the router. I get an ip though if I use dhclient.

here's the lspci -nn output:```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce Go 7600] [10de:0398] (rev a1)
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
07:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
07:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
07:06.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
07:06.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]
07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
```
lshw -C Network:```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:ce:26:51
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:62:03:23
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```
ifconfig:```
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:62:03:23
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1352 (1.3 KB)  TX bytes:684 (684.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:ce:26:51
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-CE-26-51-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
wmaster0 didn't exist before the upgrade, I don't know what is is. What I'm trying to get working here is eth0

---

### Post by Coreigh on 2008-10-22
You indicated in the original post that this is a <i>wired</i> ethernet connection, not wireless. The output of your ifconfig indicated that there are wireless settings enabled. Do you in fact have a wireless NIC on this computer? It is possible that the is some configuration interference between the wired and wireless settings. I am sorry I don't have any suggestions on resolving the conflicts.

---

### Post by dresnu on 2008-10-22
Yes, indeed there is a wireless adapter on the laptop though it's not the one I'm trying to configure right now.

Before upgrading both wired and wireless connection worked fine. Wired connection worked by just plugging the cable. Netword manager configured the network settings and after a couple of seconds I had a working connection to my router and to the internet. At startup there was connection directly if the cable was already plugged in. I don't have a wireless connection where I am right now so that is not a topic.

As I explained in the first post, after upgrading wired connection was lost. There might be a conflict as you say, but I don't know exactly what I'm looking for and why this upgrade created the problem.

---

### Post by pytheas22 on 2008-10-22
It's strange because you get an IP address, and by all indications from the information you posted, things should work.  But you can't even load your router's configuration page?  Can you ping your router?  Can you access websites if you enter their IP addresses directly instead of domain names?

You may also want to boot to the 8.04 live CD to see if things work there.  If they do, then you know that the problem is rooted in some configuration issue; if you get no connection in the live environment, then it must be some bug in Ubuntu 8.04.  But I suspect the former because I googled and can't find anyone else have problems with your ethernet card on Ubuntu.

I don't think that the wireless card has anything to do with it, unless something really weird is happening, which seems unlikely based on the outputs above.

---

### Post by dresnu on 2008-10-23
Oh man... this is driving me crazy! I went all the way and installed intrepid. But still no luck :(. I even disabled wireless through the manual switch just in case but that did not do any difference...

I don't know what to do, this upgrade mess it up pretty bad for me. Thanks a lot for googling my problem, that's what I'm doing too but like you said I can't really find anyone else experiencing this.

---

### Post by pytheas22 on 2008-10-23
Did you check to see whether it works under the Hardy or Intrepid live CD?  That's useful to know, because it would determine whether the problem is a bug in Hardy/Intrepid, or merely a configuration problem with your particular system.

---

### Post by PSUinDC on 2008-10-23
I'm experiencing something similar, but with a wireless card.

I installed Hardy for the first time, installed drivers for my card, and can't surf with a browser.  All console commands indicate a good connection, and I can even FTP to my website on GoDaddy, but I can't friggin browse the web.

---

### Post by pytheas22 on 2008-10-23
> I installed Hardy for the first time, installed drivers for my card, and can't surf with a browser. All console commands indicate a good connection, and I can even FTP to my website on GoDaddy, but I can't friggin browse the web.

That sounds like it could be a DNS problem.  Can you access websites if you put their IP addresses directly into the address bar (e.g. 72.14.207.99
for Google)?

If that doesn't help, you should probably start a new thread so that things don't become too convoluted here.  Please let me know the URL and I'll follow there.

---

### Post by PSUinDC on 2008-10-23
> **pytheas22 said:**
> That sounds like it could be a DNS problem.  Can you access websites if you put their IP addresses directly into the address bar (e.g. 72.14.207.99
for Google)?

If that doesn't help, you should probably start a new thread so that things don't become too convoluted here.  Please let me know the URL and I'll follow there.

Yeah, I have a thread at [http://ubuntuforums.org/showthread.php?p=6018237#post6018237](http://ubuntuforums.org/showthread.php?p=6018237#post6018237)    

Didn't mean to hijack this one either, it just sounded similar.  I'm at work, and I'll try accessing a website via the IP when I get home.

---

### Post by pytheas22 on 2008-10-23
> Yeah, I have a thread at [http://ubuntuforums.org/showthread.p...37#post6018237](http://ubuntuforums.org/showthread.p...37#post6018237)

Didn't mean to hijack this one either, it just sounded similar. I'm at work, and I'll try accessing a website via the IP when I get home.

Thanks, I'll follow that thread.  It's alright that you posted in this thread, but since I think that the root of your problem is quite different from that of the original poster's here, I think it's better to separate the two issues.

---

### Post by dresnu on 2008-10-23
> **pytheas22 said:**
> Did you check to see whether it works under the Hardy or Intrepid live CD?  That's useful to know, because it would determine whether the problem is a bug in Hardy/Intrepid, or merely a configuration problem with your particular system.

Ok I tried hardy live cd, and got nothing, absolutely nothing. Then I tried fedora 9 live cd and I had problems there too.

In both cases connection was established but I couldn't surf the web. Only in fedora I could access the router, ping sites and occasionaly get at about 60% loading a webpage before it stopped.

I 'm starting to think this might be a hardware related problem. But why work in windows then? The only thing I can think of is that the router suddenly stopped working with linux for some reason.

The router can be operated as a pppoe modem too. I will try this mode next time I boot linux to see if something changes

---

### Post by pytheas22 on 2008-10-23
Yes, I agree that the behavior you're describing is pretty strange and inconsistent, so I wouldn't rule hardware failure out.  Are you sure that the card works 100% in Windows?  And have tried rebooting the router?

---

### Post by dresnu on 2008-10-26
Ok, I solved it somehow. There seems to be a problem with my router.

When set in routed mode it gives an ip to the computer but then it doesn't let it navigate (NAT is configured). I then tried to set it as a dsl modem and establish a connection through pppoeconf and it worked like a charm.

So now I'm using it this way until I figure out what's going on. Apparently this is not a linux problem (having tried ubuntu and fedora), though it's still strange that I don't experience this behaviour in windows...

Anyway, thanks to everyone who replied in this thread.

---

