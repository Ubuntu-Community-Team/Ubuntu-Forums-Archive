---
title: "lost connection when streaming"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by cartisdm on 2010-11-10
I've been using Ubuntu on my Dell Inspiron since 7.04 and never had much in the way of Wireless problems (aside from initial connection once in a while).  Now that I've upgraded to 10.04 (from 9.10), my internet is all kinds of on the frits.  I can download endless hours of media via a utorrent, and I can surf the internet until my hear is content, but when I stream a video my connection drops.  If I start a YouTube video it will get about a third of the way loaded then my wireless will act like it can't get a connection to my router any more.  Then, I can't connect again unless I reboot.

I have 3 other ubuntu computers running in the house (various versions, including 10.04) and two android phones that all work perfectly.  What's wrong?

```

$ lshw -C
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

```

---

### Post by cariboo on 2010-11-12
Could you paste the output of:

```
lshw -C network
```

---

### Post by cartisdm on 2010-11-12
> **cariboo907 said:**
> Could you paste the output of:

```
lshw -C network
```

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:e0:46:f7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:dfcff000-dfcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ac:1c:14
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:df9fe000-df9fffff

```

---

### Post by cartisdm on 2010-11-17
bump?

---

### Post by cartisdm on 2010-11-20
bump again?

Another thing I'm noticing lately.  When I close my laptop, it gets "stuck" and I can't resume my session anymore.  I have to hard reboot.  Whenever I do that, the Wireless Networking is disabled when I boots back up.  I have to manually enable it and it will then connect to my network.

What's with all these sudden problems in 10.04? I've never had problems like this since 7.04...

---

### Post by Remete7 on 2010-11-28
Hi, I have exactly the same problems. I have no solution for these, but I'm also interested.
TIP: when streaming stops, and connection is lost you just have to type in the terminal:

sudo service network-manager restart

Give your root pswd and if you wait a few seconds, the connection will be fine.

---

### Post by cartisdm on 2010-11-30
> **Remete7 said:**
> Hi, I have exactly the same problems. I have no solution for these, but I'm also interested.
TIP: when streaming stops, and connection is lost you just have to type in the terminal:

sudo service network-manager restart

Give your root pswd and if you wait a few seconds, the connection will be fine.

Not to be an Ubuntu Basher, but it's been giving me a lot of problems since 9.04 and I'm not quite sure why. Prior to that, it worked flawless on 99% of computers I installed it on (the remaining 1% was a quick google search to be up and running).

I just put Jolicloud 1.0 on my netbook and now I'm considering trying it out on my Dell...

---

### Post by akand074 on 2010-11-30
Did you do an upgrade from the package manager? or did you do a clean install? I've never heard of any upgrade on any OS that guaranteed stability. I remember when I temporarily did an in-place upgrade from Vista to 7, a disaster compared to a clean install. Also I did an upgrade via the package manger from 8.10 to 9.04 to 9.10. 9.10 was the one time I complained about a new release in Ubuntu, there was a lot of issues. Do a clean install if you haven't already. Also this sounds more like a Flash/plug-in issue over a networking issue.

---

### Post by cartisdm on 2010-11-30
> **akand074 said:**
> Did you do an upgrade from the package manager? or did you do a clean install? I've never heard of any upgrade on any OS that guaranteed stability. I remember when I temporarily did an in-place upgrade from Vista to 7, a disaster compared to a clean install. Also I did an upgrade via the package manger from 8.10 to 9.04 to 9.10. 9.10 was the one time I complained about a new release in Ubuntu, there was a lot of issues. Do a clean install if you haven't already. Also this sounds more like a Flash/plug-in issue over a networking issue.

I did a fresh install - I've heard of too many headaches from upgrades, plus I like using it as an excuse to clean up my files and reorganize.

The thought of the flash player/plugin is good though, I haven't considered that.

---

