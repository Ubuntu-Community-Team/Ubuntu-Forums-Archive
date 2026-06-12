---
title: "[SOLVED] poor wifi performance 8.04"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by wincen on 2008-11-14
I'm using ubuntu 8.04 and I have extremely poor wifi performance.  I'm using the built in Ralink wifi from my laptop.

The major problem is after seemingly random amounts of time the network speeds suddenly slow down eventually 95% or more packets are lost.  Sometimes it take only a few minutes for this to happen, other times 2 hours.

This is quite frustrating, so much so that I have had to install windows on my laptop in order to actually get anything done online.  My wifi works just fine in windows.  The speed is much faster, everything from downloads, to torrents.

Has anyone else experienced this problem?
Is this a known issue?  I have heard there are many wifi issues with ubuntu but not very familiar with them all.
Any suggestions on getting my wifi to perform reliably?  I would prefer being able to do everything using ubuntu instead of dual booting into windows.


---------------------------------------------------
FIX: install ndiswrapper.  That's it!  =)

---

### Post by Plumtreed on 2008-11-14
I run 8.04 Hardy and have always got reasonable speed from WIFI. I suggest that the problem may come from the provider rather than Hardy.

Most 'issues' really come from the way of connecting! I have updated NetworkManager to 0.7 and most issues have gone.

Tell us more about your gear, location and so on, please.

---

### Post by wincen on 2008-11-14
i'm backpacking around some countries in se asia and do not always have the best connection so it's possible the problem could be from the provider, but since I've installed winxp, xp doesn't have these problems. 

is the network manager you installed the one included in 8.10?  how did you install it?

---

### Post by Plumtreed on 2008-11-15
I followed this thread and it went together easily.[HTML]http://ubuntuforums.org/showthread.php?t=948977[/HTML]

Sorry, I guess I don't know how to make a link???? but cut and paste:)

Doing a similar thing in Europe, some areas better than others for mobile broadband but have had great luck with WIFI with no charge associated with it! It seems many people are happy to share a bit of their connection. It is a similar idea as Ubuntu, making computers and internet access available and universal. 

Do the upgrade, it is simple to do and really works well. Good luck!

---

### Post by wincen on 2008-11-16
Thanks!  This seems to have improved my wifi a lot!  It still doesn't have the performance that windows has when downloading say torrents, but after using my computer on and off today I haven't noticed the majors slow downs I was experiencing.  I'll cautiously mark this solved... at least for right now.

I want to note though that when I first installed and rebooted the machine I could not connect to my wifi network.  It was really strange.  The app kept rejecting the WEP key.  Oddly enough after rebooting again things worked.  I can't explain it.

Here is the link Plumtreed provided:
[http://ubuntuforums.org/showthread.php?t=948977]("http://ubuntuforums.org/showthread.php?t=948977")

I'm going to copy the post by Patrick793 on the thread linked above on how to update Network Manager to 0.7 in Ubuntu 8.04.

The Link referenced by Patrick793 for installing Network Manager 0.7 on Hardy [http://ubuntuforums.org/showthread.php?t=797059]("http://ubuntuforums.org/showthread.php?t=797059")

first backup your sources.list
```
cp sources.list sources.list.bk
```

Edit your apt-get source list
```
gksudo gedit /etc/apt/sources.list
```

Add this to the end of the file.
```
## Network Manager 0.7
deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main
```

Finally, update.
```
sudo apt-get update && sudo apt-get upgrade
```

Also a note from jbrown96:
> +1 to this solution. You should probably remove this section after you install for security reasons. When you run the upgrade command, it will complain about installing unsigned packages. Someone could highjack this and cause a security breach if you leave them enabled.

If you wish to remove this section comment out the Network Manager source you just added.
```
## Network Manager 0.7
# deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
# deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main
```


Note:
I have heard Network Manager still has some problems, though in my limited time using it I haven't encountered them.  A Network Manager alternative that many people seem very happy with is wicd.  Supposedly it has no problems working with WPA.

[http://help.ubuntu.com/community/WICD]("http://help.ubuntu.com/community/WICD")
[wicd website]("http://wicd.sourceforge.net/")

---

### Post by wincen on 2008-11-18
Well, looks like I spoke too soon.  I do think Network Manager 0.7 is an improvement over the previous version but it did not fix my problem.

It looks my routing table is being changed, and when it happens I can no longer reach my gateway even though I still have a wifi connection.  I cannot ping my gateway, 100% of packets are dropped.

This is what the route command displays when everything is ok:
```
billhill@alto:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         **.**               0.0.0.0         UG    0      0        0 wlan0
```

This is what the route command displays when I can no longer reach my gateway:
```
billhill@alto:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         **192.168.2.1 **    0.0.0.0         UG    0      0        0 wlan0
billhill@alto:~$ 

```
In this case the IP Address of my gateway is 192.168.2.1 so I do not understand why my network connection will only work as "."



This is what it looks like in windows... It just works in windows.  :confused:
```
C:\Documents and Settings\billhill>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 40 45 2c 43 f1 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
0x10004 ...00 1d 92 c4 43 d3 ...... 802.11g Mini Card Wireless Adapter - Packet
Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1   192.168.2.101       25
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.2.0    255.255.255.0    192.168.2.101   192.168.2.101       25
    192.168.2.101  255.255.255.255        127.0.0.1       127.0.0.1       25
    192.168.2.255  255.255.255.255    192.168.2.101   192.168.2.101       25
        224.0.0.0        240.0.0.0    192.168.2.101   192.168.2.101       25
  255.255.255.255  255.255.255.255    192.168.2.101               2       1
  255.255.255.255  255.255.255.255    192.168.2.101   192.168.2.101       1
Default Gateway:       192.168.2.1
===========================================================================
Persistent Routes:
  None
```


Why in the world will my network connection work only when the gateway is "."?
Anyone?  This problem is killing me.

---

### Post by wincen on 2008-12-28
Ok fixed the problem.  I just needed to install ndiswrapper and get the windows driver.  Wifi works fine now.

---

