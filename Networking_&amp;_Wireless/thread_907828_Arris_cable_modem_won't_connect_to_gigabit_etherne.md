---
title: "Arris cable modem won't connect to gigabit ethernet"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by bchannell on 2008-09-01
I did some searching and couldn't find too much on this problem.
I've switched to ubuntu 64bit 8.10.1 exclusively from XP and am quite glad I did. Built new computer, Gigabyte nforce 570 SLI mobo, AMD 64 X2 6400+, everthing except internet connection is cool. I can connect using the usb port on my Arris cable modem, but not using the onboard gigabit ethernet connection. Couldn't connect in the quick and dirty install of XP I did, just to check it out. Tried Cat6 cable, no dice. I'm using the usb port right now and all is fine, but I'd like to figure out the gigabit connection problem. 
Any ideas?
Thanks

---

### Post by cariboo on 2008-09-01
Are you shure your network card is setup properly? In a terminal type:

```
sudo lshw -C network
```

With my motherboard, Nvidia MCP51, nothing show when I run the above, but when I change the network to bridge it shows the configuration.

Jim

---

### Post by bchannell on 2008-09-02
it shows

bob@bob-desktop:~$ sudo lshw -C network
[sudo] password for bob: 
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:15:a3:22:db:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=75.109.159.92 link=yes multicast=yes
bob@bob-desktop:~$ 

I'm pretty green at this, having used Windows for 25 yrs, what does it mean? Right now I'm using the usb hookup, with no cable in the ethernet.

---

