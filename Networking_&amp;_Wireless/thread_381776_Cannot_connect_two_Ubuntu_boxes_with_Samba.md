---
title: "Cannot connect two Ubuntu boxes with Samba"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by sup on 2007-03-11
I would like to share files between two Ubuntu boxes (both 6.10) using Samba. I know about NFS, but I for various reasons prefer samba. Only it does not work.

I have samba installed, I can ping the other computer and they are both on the same subnet (192.168.2.120). We can play LAN Frozen-bubble alright so the network itself works, only Samba does not.

the config file is the same on both boxes, only shared folders vary:
```

[global]
   workgroup = UBAKA
   server string = bill
   security = share
   netbios name = bill1
   socket options = TCP_NODELAY
   hosts allow = 0.0.0.0/0

```
shares of the first computer
```

[Desktop]
path = /home/tom/Desktop
available = yes
browsable = yes
public = yes
writable = no


[Osobni]
path = /home/tom/Osobni
available = yes
browsable = yes
public = yes
writable = no


[Hudba]
path = /home/tom/Hudba
available = yes
public = yes
writable = no
browsable = yes


[new]
path = /home/tom/Desktop/new
available = yes
browsable = yes
public = yes
writable = yes
force user = tom

```
shares of the second computer
```

[Desktop]
path = /home/frenkac/Desktop
available = yes
browsable = yes
public = yes
writable = no
guest ok = yes

```

I know this is very insecure, but I want to make it work first, then make it secure.
Several thoughts:
1) Can a problem be somewhere in NetBIOS? I tried to open its ports on both computers, but it seems not to have helped:
```

#/bin/bash
iptables -A INPUT -p tcp --dport 445 -j ACCEPT
iptables -A INPUT -p tcp --dport 139 -j ACCEPT
iptables -A INPUT -p udp --dport 138 -j ACCEPT
iptables -A INPUT -p udp --dport 137 -j ACCEPT

```
but then again, I cannot access the other computer even with smb://192.168.2.120, which is its address
2) do I need to specify interface that can be used for this? but samba should use all byt default, should not it?

3) I noticed it takes some time for smbtree to list anything... how long should I wait to be sure Samba is not working with the other computer? It takes about a minute to be able to list shares on my computer, how long would it take with the second. This delay makes it hard to troubleshoot.

I am a bit hopeless, can anyone give me a hint.

---

### Post by sup on 2007-03-11
well, teh config files actually differs - server string and netbios names are different. I forgot to mention that.

---

### Post by Mr. C. on 2007-03-11
Slow down - too many questions and too much randomness.

Did you assign a guest user since you are using Share level security?  Is that user in /etc/group ?

Find my previous post about getting samba to work; has several points of clarification for the user.

You do not have to wait for shares to appear - you can always try to access them by name:

\\computer\share

and they will appear.  Windows share discover takes some time - its just the way it was implemented.

MrC

---

### Post by sup on 2007-03-12
Alright, so I added 
guest account = samba
guest ok = yes
guest only = no
and ran 
```
sudo adduser samba --system --group
```
but it did not help. I also tried using my own user name (and the othr username on the other machine) but that did not work. I remember that once when I was setting up samba shares I needed to use force user option, but only when i wanted to write into shares, which is no concern now (I need the computers to see each other first)

---

### Post by sup on 2007-03-12
So I figured out what the problem was in. I am connected to a NAT router (a very cheap embedded device with no linux support whatsoever, so it is almost unconfigurable) through an another embeded wifi AP that is in a bridge mode and cannot be accesed from the network (i.e. it is not assigned and IP address and so on). This device runs linux so it can be configured, which is where my hope is (I hope I can setup some kind of routing instead of bridging in there that will solve the problem). For when I tried to connect my laptop directly to the NAT router with a cable, it suddenly started to work. So the problem somehow lies in the bridge, but I have no idea how it can be related to it, I thought the communication was as if the bridge (the AP) were not there.

Well, I cannot say I am not confused now.

---

### Post by thelinuxguy on 2007-03-12
> **sup said:**
>  through another embeded wifi AP that is in a bridge mode and cannot be accesed from the network (i.e. it is not assigned and IP address and so on).  

I think even in the Bridge mode routers are accessible by a predetermined IP because otherwise there would be no way to configure it over the network. My router (Broadcom UT-300R2U) is in Bridge mode and can be accessed at 192.168.1.1 which is its default IP. Try getting into the router administration page at [http://192.168.1.1](http://192.168.1.1) and see if you can tweak some settings to make  the whole thing work.

---

### Post by sup on 2007-03-14
Hm, this one would not work, I tried to set up proper routing but that did not work (after several hours I got a good grasp of routing only to discover that whereas linux wifi ap was capable of almost anything, that cheap NAT router is a piece of crap) so I ended up with wifi ap being a client of the NAT router NATting it own clients, my LAN now works through hamachi and it works like a charm. 
Lesson learned: do not buy something that can't do linux, it does not work:-D.

---

