---
title: "ndiswrapper"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by rmf8066 on 2009-04-09
i've been lookin up stuff on ndiswrapper thinking that it might help me with my wireless connection, and went to the help page on the bar. searched in ndiswrapper, and clicked on Internet and Networks. I started from the beginning, checkin to see if the device is on. Since my cards picking up a signal, i figured it was on. I then checked for device recognition, and went into my terminal and typed sudo lshw -C network. this came up:

*-network               
       description: Ethernet interface 
       product: 3c905C-TX/TX-M [Tornado] 
       vendor: 3Com Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 78 
       serial: 00:08:74:e4:3d:77 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s 
  *-network 
       description: WaveLAN/IEEE 
       product: Version 01.01 
       vendor: Lucent Technologies 
       physical id: 0 
       slot: Socket 0 
       resources: irq:3 
  *-network:0 DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 7e:9d:08:64:4c:d5 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
  *-network:1 
       description: Wireless interface 
       physical id: 2 
       logical name: eth1 
       serial: 00:60:1d:1e:98:40 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 4.32 ip=192.168.1.136 link=yes multicast=yes wireless=IEEE 802.11b 

network 0 says disabled, and since the help told me an output should say "claimed, unclaimed, enabled or disabled". since the only thing i saw with those words was disabled, i'm a little confused. it says if its disabled, then to check to see if the device is on, which i thought it was to begin with?

and when i click onto 5.2.3 using windows wireless drivers, i click on install the ndisgtk package, an error comes up saying:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb) 
  Could not resolve 'us.archive.ubuntu.com' 


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb) 
  Could not resolve 'us.archive.ubuntu.com' 


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb) 
  Could not resolve 'us.archive.ubuntu.com' 

i'm lost...any help?

Farah

---

### Post by pytheas22 on 2009-04-10
You should not need ndiswrapper, because it looks like your card is already recognized and up (and if you can see networks, it's definitely working).  Are you simply unable to complete the connection to a network?  Or is there some other problem?

> network 0 says disabled

Don't worry about this.  network-0 (pan0) is a virtual interface, and by default it's always disabled.

---

### Post by rmf8066 on 2009-04-10
my connection strength is very low for everything, even the router i used before used to be around 80%. Now its maybe at 25%. i just want to be able to use the internet without having to reload the page. i think i might just need a new wireless card, but this one i have now works fine, just getting a weak connection. Now my roommate is using our neighbors internet while ours is getting fixed, and his connection is 100%. Now for me, i cannot get onto it with the password, and on my laptop, the connection is shows its around 40%.

---

### Post by pytheas22 on 2009-04-10
If you want to try ndiswrapper on this card, post the output of these commands:
```

lspci -nn
lsusb
uname -rm
```

---

