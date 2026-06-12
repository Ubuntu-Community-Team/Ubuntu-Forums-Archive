---
title: "wireless stopped working after update"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by ra_sar on 2009-06-27
I have an Acer Aspire One and I am running UNR.  Last week after I rebooted from some updates, I found that my computer could no longer see any of the wireless networks that I had previously been connected to.  I use Wicd and it says "No wireless networks found" though thankfully the wired connection still works.

I haven't yet gotten my wireless LED working so I'm never 100% sure if I've somehow manually turned it off or on, but I've tried everything from rebooting after flicking the switch and then again, to restarting the network after doing so, so I'm fairly confident it does not work in either position.

---

### Post by Michael.Godawski on 2009-06-27
Just a wild guess: have you tried to boot into another (older) kernel? Perhaps the kernel updated mixed something up. 

Can you please post the output from 
```
iwconfig
ifconfig
sudo lshw -C network
sudo iwlist scan
```

---

### Post by LewRockwell on 2009-06-27
well, I'll just include some links to information pertaining to your machine

note: these links refer to more than just one issue and should give much insight regarding what others are experiencing using new-fangled netbooks

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

[http://ubuntuforums.org/showthread.php?t=903280](http://ubuntuforums.org/showthread.php?t=903280)

[http://ubuntuforums.org/showthread.php?t=915524](http://ubuntuforums.org/showthread.php?t=915524)

[http://ubuntuforums.org/showthread.php?t=1192215](http://ubuntuforums.org/showthread.php?t=1192215)

[http://nino.me.uk/?p=286](http://nino.me.uk/?p=286)

[http://blog.marxy.org/2009/05/ubuntu-904-netbook-remix-on-acer-aspire.html](http://blog.marxy.org/2009/05/ubuntu-904-netbook-remix-on-acer-aspire.html)

[http://people.uleth.ca/~daniel.odonnell/Blog/installing-ubuntu-904-jaunty-on-aspire-one](http://people.uleth.ca/~daniel.odonnell/Blog/installing-ubuntu-904-jaunty-on-aspire-one)

you can find new/newer links as time wears on by searching for:

"ubuntu 9.04 Acer Aspire One"(without the quotations)

---

### Post by ra_sar on 2009-06-27
I wouldn't even know how to boot into another kernel. 

Result of **iwconfig**:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Result of **ifconfig**:
eth0      Link encap:Ethernet  HWaddr 00:23:5a:4d:58:3f  
          inet addr:192.168.69.130  Bcast:192.168.69.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fe4d:583f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14280 errors:0 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1000 
          RX bytes:15190163 (15.1 MB)  TX bytes:2616439 (2.6 MB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 B)  TX bytes:600 (600.0 B)

**sudo lshw -C network**

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:5a:4d:58:3f
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.69.130 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:fd:a8:2d:a6:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by stednick on 2009-07-03
ra_sar,

I am having a similar issue.  Did you get different results after booting from the older kernel?

---

### Post by Michael.Godawski on 2009-07-03
To boot into another kernel you have to do this:


[LIST]
[*][https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)
[/LIST]

---

### Post by nothingspecial on 2009-07-03
You can fix this using madwifi

Have a look at [this]("https://help.ubuntu.com/community/AspireOne") 

Scroll down untill you find the bit about getting wireless to work on intrepid.

---

### Post by ra_sar on 2009-08-12
Belated thanks for the advice to all--I am able to access wireless when I boot from an earlier kernel, and my wireless LED now works every so often when it feels like it.  Still haven't sorted out what the issue is but at least it's functional.  I was hoping that more updates would fix it but no such luck.

---

