---
title: "Beginner. Can't seem to get Linksys WUSB54G v3 go work"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by moree on 2009-11-06
I have Linux Mint Gloria (which I'm told is based on ubuntu).  I was also told it was the most user-friendly for newbies to Linux.  I used ndiswrapper to install the driver that I downloaded from Linksys.

I put in my disc. Click on Windows Wireless Drivers. I get the message "Unable to see if Hardware is Present" before I even do anything.

I click OK.

Then I click Install New Driver.  I find the .inf file on my CD and click OK.

It now says it's installed and hardware is present.  However, I cannot pick up a wireless signal.

I'm including some info here so maybe someone can help me - cause I can't seem to get help on the Linux Mint forum...or at least the advice I'm given isn't working.



lsusb
Bus 002 Device 002: ID 1737:0077 Linksys 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver




* I. scanning WIFI PCI devices...
-------------------------
* II. querying ndiswrapper...
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
rt2870 : driver installed
    device (1737:0077) present
-------------------------
* III. querying iwconfig...
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:0c:46:f5  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe0c:46f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11738344 (11.7 MB)  TX bytes:868425 (868.4 KB)
          Interrupt:11 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

-------------------------
* V. querying DHCP...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/6e:6a:af:82:e4:b8
Sending on   LPF/pan0/6e:6a:af:82:e4:b8
Listening on LPF/eth0/00:c0:9f:0c:46:f5
Sending on   LPF/eth0/00:c0:9f:0c:46:f5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 10.0.0.5 from 10.0.0.1
DHCPREQUEST of 10.0.0.5 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.5 from 10.0.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 10.0.0.5 -- renewal in 33909 seconds.
-------------------------
* VI. querying nslookup google.com...
Server:        10.0.0.1
Address:    10.0.0.1#53

Non-authoritative answer:
Name:    google.com
Address: 74.125.67.100
Name:    google.com
Address: 74.125.53.100
Name:    google.com
Address: 74.125.45.100

---

### Post by moree on 2009-11-06
Oh, I'm thinking of switching to Ubuntu.  Will that wok better?

---

### Post by Arla on 2009-11-06
> **moree said:**
> Oh, I'm thinking of switching to Ubuntu.  Will that wok better?

Might be worth a try, can always just boot from the livecd and see if your wireless is supported "out of the box". I remember having to mess around with ndis-wrapper last time I tried ubuntu, but that was probably around 7.04, now it handles my wireless flawlessly.

Note: Last time I tried Kubuntu the network manager did NOT handle wireless flawlessly (had to install Gnome Network manager to get wireless working) so Ubuntu LiveCD is the way I'd go if I was you.

---

### Post by moree on 2009-11-07
OK.  I booted up with Ubuntu from the CD.  No luck in getting it to see my wireless USB adapter.  Anyone out there able to give me some advice?

---

### Post by DUKANE on 2009-11-07
Check the list here [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB) to make sure your device is compatible!

---

### Post by moree on 2009-11-07
Linksys Cisco WUSB54GC USB wireless adapter

Not listed.  Other versions of it are, though.  

So because mine isn't listed, does that mean it will never work with Linux?

---

### Post by LewRockwell on 2009-11-07
> **moree said:**
> Linksys Cisco WUSB54GC USB wireless adapter

Not listed.  Other versions of it are, though.  

So because mine isn't listed, does that mean it will never work with Linux?

we searched and found these pages for you:


[http://www.amazon.com/review/R34YN3FGTUR7S1/ref=cm_cr_rdp_perm](http://www.amazon.com/review/R34YN3FGTUR7S1/ref=cm_cr_rdp_perm)


[http://forum.linuxmint.com/viewtopic.php?f=53&t=29218](http://forum.linuxmint.com/viewtopic.php?f=53&t=29218)


[http://ubuntuforums.org/showthread.php?t=923387](http://ubuntuforums.org/showthread.php?t=923387)

.

---

### Post by cariboo on 2009-11-07
From the looks of your first post you are trying to use the Windows drivers, hopefully you are using ndiswrapper.


If as LewRockwell says that the device RT73 drivers, It should be detected and the proper driver installed by default. I don't see the output of:

```
sudo lshw -C network
```

Your device should show up in the listing. Report back with the results.

---

### Post by moree on 2009-11-07
> **LewRockwell said:**
> we searched and found these pages for you:


[http://www.amazon.com/review/R34YN3FGTUR7S1/ref=cm_cr_rdp_perm](http://www.amazon.com/review/R34YN3FGTUR7S1/ref=cm_cr_rdp_perm)


[http://forum.linuxmint.com/viewtopic.php?f=53&t=29218](http://forum.linuxmint.com/viewtopic.php?f=53&t=29218)


[http://ubuntuforums.org/showthread.php?t=923387](http://ubuntuforums.org/showthread.php?t=923387)

.


Thank you.  I'll review these links and see if they can help me.

---

### Post by moree on 2009-11-07
> **cariboo907 said:**
> From the looks of your first post you are trying to use the Windows drivers, hopefully you are using ndiswrapper.


If as LewRockwell says that the device RT73 drivers, It should be detected and the proper driver installed by default. I don't see the output of:

```
sudo lshw -C network
```Your device should show up in the listing. Report back with the results.


OK here it is:

sudo lshw -C network
[sudo] password for jean: 
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:c0:9f:0c:46:f5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=10.0.0.5 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:de:05:db:09:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by moree on 2009-11-14
Thank you so much for all your time and work. I did everything in your instructions except copy the file to the wireless folder in the etc folder as I had no wireless folder present and could not create one. The USB adapter still does not work. I'm giving up and going back to windows even though I LOVE using Linux. If I can't access the internet wirelessly, then it's useless. Thanks all.

---

