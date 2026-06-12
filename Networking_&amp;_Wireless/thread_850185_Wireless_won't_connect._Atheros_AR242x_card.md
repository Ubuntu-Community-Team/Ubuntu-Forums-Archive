---
title: "Wireless won't connect. Atheros AR242x card"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by sweetaussie on 2008-07-05
Hi all i am unable to get my wireless card to work.  This is the first install on my compaq Preserio laptop.

This is my infomation:  


```
janny@janny:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions
```.
 

```
janny@janny:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```


```
janny@janny:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:08:77:7d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.68 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

Im sorry to be asking new Questions but im just out of the box on this one.

---

### Post by WoodyandEye on 2008-07-05
bump

Sorry, I know it is a Holiday, but I am sure someone can help this poor lady.  I don't know enough.

---

### Post by Midwest-Linux on 2008-07-05
This might be helpful, but just be aware that updates can kill wireless down the road.


[http://ubuntuforums.org/showthread.php?p=5047061](http://ubuntuforums.org/showthread.php?p=5047061)

Good Luck

---

### Post by walkerk on 2008-07-05
I have the same wireless NIC. I installed [ndiswrapper]("http://ndiswrapper.sourceforge.net") and used the XP driver. Just an idea. I believe you can use madwifi as well but I haven't tried...

---

### Post by linuxonbute on 2008-07-05
> **walkerk said:**
> I have the same wireless NIC. I installed [ndiswrapper]("http://ndiswrapper.sourceforge.net") and used the XP driver. Just an idea. I believe you can use madwifi as well but I haven't tried...

You might want to look at this thread as well :

[http://ubuntuforums.org/showthread.php?t=849984](http://ubuntuforums.org/showthread.php?t=849984)

---

### Post by sweetaussie on 2008-07-05
> **Midwest-Linux said:**
> This might be helpful, but just be aware that updates can kill wireless down the road.


[http://ubuntuforums.org/showthread.php?p=5047061](http://ubuntuforums.org/showthread.php?p=5047061)

Good Luck

Thank You.  I made some great progress with that link.

But, I now have a couple new problems.

[LIST=1]
[*]I can no longer log on with my Ethernet wired connection.
[*]My Laptop appears to recognize everything.  Wicd finds my modem and others in the area.  It allows me to sign on to mine, and gives me the message that I am connected.  But I cannot access the Net yet.  I get errors on my browser.
[/LIST]


I appreciate all of your help.  You are all very kind.
Once I have exhausted this route, and if it doesn't work, I will try the other suggestions.  I just don't want to get "too" confused.

Thanks to all for your continued help.

---

### Post by sweetaussie on 2008-07-05
**[COLOR="Red"][SIZE="4"]Update![/SIZE][/COLOR]**

I made some corrections in WICD and now have Wireless Access!  Yeah!  :)

Still unable to connect using Ethernet Card.

I will leave this open for a bit on that issue.

I can't thank you enough for all your help.

:guitar:

---

