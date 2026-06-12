---
title: "Wired network having trouble."
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by SteinbergerNate on 2007-06-11
I haven't used my wired network device in so long because I don't have internet access at my home. When I do connect it's somewhere that has wireless and so I don't worry about it. (this is a laptop.) Well, yesterday I wanted to pull out the network hub I have and backup my home directory to a desktop computer I have at home. I went to go connect it but the light on the port didn't come on when I thought it should. I checked the back of the computer for network activity but didn't get anything. Linux sees the card and I can even ping the loopback. I also ran the diagnostic disc that came with the computer and it says that everything should be ok with that interface. 

Any ideas on what the problem is?

---

### Post by turinglabs on 2007-06-11
Some questions and a few ideas - are you connecting through a hub or a switch? If a hub, is the cable in an uplink port? Does an ifconfig show the interface as 'UP' with an IP address? What does the output of 'mii-tool' show you?

---

### Post by SteinbergerNate on 2007-06-11
I can't remember if it says that it's up or not. I don't get an ip address because this is a hub without any kind of dhcp on the network (all I need to do with it is an smb share). Please forgive me. I don't have the computer here in front of me. 

I just remembered that last night I booted into Windows just to see what would happen. I got the green power light on the back of the nic during boot but it turned off once I was in Windows. I'm not sure if this is a hardware issue or not (I hope not seeing that it's integrated) but I don't think it is since everything sees the interface. The desktop is XP and it is connecting to the hub just fine and I get a light on the front of the hub for that port.

I'll try mii-tool when I get home.

edit: I have the cable plugged into the first of the 8 normal ports on the hub. (there's a 9th at the end specifically for the rest of the network to connect through.

---

### Post by turinglabs on 2007-06-11
With the cable plugged in, mii-tool will tell you if the link has been established. Once it has, you'll need to manually assign an IP with ifconfig (you can use network-manager, too, but I find something like 'ifconfig eth1 192.168.3.1 up' quicker, with the added benefit of being temporary).

```

serenity:~# mii-tool
eth0: no link
eth1: no link
eth2: negotiated 100baseTx-FD flow-control, link ok
serenity:~#

```

---

### Post by SteinbergerNate on 2007-06-11
Thanks. I'm gonna try that when I get home. The XP machine isn't showing that it has an IP either. Will that be a problem for smb once I get everything working?

---

### Post by turinglabs on 2007-06-11
> **SteinbergerNate said:**
> Thanks. I'm gonna try that when I get home. The XP machine isn't showing that it has an IP either. Will that be a problem for smb once I get everything working?


Yes, they'll both need IP's on the same network.

---

### Post by SteinbergerNate on 2007-06-11
Ok. I've never had to handle this kind of problem on a network that didn't have a router or some other form of dhcp server.

---

