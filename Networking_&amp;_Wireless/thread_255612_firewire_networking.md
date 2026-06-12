---
title: "firewire networking?"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by GameManK on 2006-09-11
Hi, I'd like to get Firewire over Ethernet going to share and/or sync files between my desktop and new laptop, but according to [https://help.ubuntu.com/community/EthernetOverFirewire](https://help.ubuntu.com/community/EthernetOverFirewire), I need to recompile the kernel.  I'm using Edgy, does anybody know if this still holds true for edgy?  Anybody else using ethernet over firewire?

(Also, any other ideas for a fast, easy, and safe way to share files on a network but not on the same subnet?)

---

### Post by GameManK on 2006-09-21
I got a firewire cable, plugged it in to the laptop (running windows) and the desktop (running edgy).  I did sudo modprobe eth1394.  It then shows up in system settings as eth1, and I can give it an IP, but then the system locks up after a few seconds.

---

### Post by ranpha on 2006-09-22
i was thinking about this. I know firewire network is crap in windows. So i thought he i'm using linux now it has to be better now. Only i don't see my firewire cards as network cards. So i really like to know how to do this. (image a 400mbit network :-))

---

### Post by GameManK on 2006-09-22
> **ranpha said:**
> i was thinking about this. I know firewire network is crap in windows. So i thought he i'm using linux now it has to be better now. Only i don't see my firewire cards as network cards. So i really like to know how to do this. (image a 400mbit network :-))

you have to load the firewire over ethernet driver by running
```
sudo modprobe eth1394
```
But my system freezes shortly after loading that module :(

---

### Post by ranpha on 2006-09-25
well I got the cards working (atleat they show up) i gave them two ipadress 192.168.168.1 and 192.168.168.2 and subnets 255.255.255.0 

I tried to ping but nothing....euh I need a little more help her. What should i do now?

---

### Post by GameManK on 2006-09-26
> **ranpha said:**
> well I got the cards working (atleat they show up) i gave them two ipadress 192.168.168.1 and 192.168.168.2 and subnets 255.255.255.0 

I tried to ping but nothing....euh I need a little more help her. What should i do now?
I got as far as you did :-k  except my machine froze.

Anyone else?

---

### Post by mips on 2006-09-27
I recall seing a firewire networking guide in these forums before, just dont know where.

Try a search or look in the howto section.

---

### Post by cld71 on 2007-11-24
I installed a eth1394 just using the above info.
And it worked at about 7MB/s but after transferring for only 15 sec. the connection stalled.:(

Is there anyway to get a reliable network connection better than 12MB/s(Standard 100Mb connection) with firewire?

---

