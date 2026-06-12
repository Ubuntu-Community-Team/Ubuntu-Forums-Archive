---
title: "Intel PRO/Wireless 4965 AG going down after a while"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by m9dhatter on 2008-02-13
ok. im using a compaq presario v3638 wih intel PRO/Wireless 4965 AG using iwl4965. 
my wireless connection goes down after around 15 minutes and i cannot, for the life of me, bring it back up unless i restart. vista doesn't seem to have that problem but i really don't want to go that route for personal reasons. 

```

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 61
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.101 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

the wireless light is on and router is working (the other machines are still connected). when it goes down, the nm-applet asks for the WEP key again. i enter it and nothing happens. when i restart, i automatically get connected again. like i should. 

```
$ uname -a
Linux michelle 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

ifconfig up/down doesn't work. restarting networking service or dbus service doesn't work.

any suggestions would be appreciated. i've read some posts saying they use ndiswrapper. would this help me? this is the first time i've used wireless.

---

### Post by dca on 2008-02-13
I don't know if this matches your current criteria but it seems (maybe) there's a bug in the current Intel firmware supplied w/ Ubuntu...  It talks about it here...
 
[https://answers.launchpad.net/ubuntu/+question/16768](https://answers.launchpad.net/ubuntu/+question/16768)
 
...see if that matches your issue...

---

### Post by spartan_87 on 2008-02-13
> **dca said:**
> I don't know if this matches your current criteria but it seems (maybe) there's a bug in the current Intel firmware supplied w/ Ubuntu...  It talks about it here...
 
[https://answers.launchpad.net/ubuntu/+question/16768](https://answers.launchpad.net/ubuntu/+question/16768)
 
...see if that matches your issue...

I had the same exact problem and this link worked for me. I have a Intel Pro/Wirless 3945 ABG and I followed the instructions in Anton Khokhlov post. And my connection hasn't dropped once all day. :)

---

### Post by m9dhatter on 2008-02-14
I've tried this [COLOR="Blue"][one]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144621/comments/42")[/COLOR] myself.
it has a packaged deb [COLOR="Blue"][here]("http://download.tuxfamily.org/3v1deb/xtra-debs/ubuntu-modules/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38~3v1ubuntu0_i386.deb")[/COLOR]

i will report back if i still have the network problem. thanks dca and spartan. :)

[update]
well, its been 2 hours and it's still up. thanks guys! :D

---

