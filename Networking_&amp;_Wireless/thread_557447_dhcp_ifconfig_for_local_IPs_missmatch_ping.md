---
title: "dhcp ifconfig for local IPs missmatch ping"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by pacohc on 2007-09-22
I have a wired LAN behind an internet router, all works fine when I assign static IPs to each computer on the LAN. However, Dynamic IPs have a problem that I can't manage to fix, and I tried a lot . . . .

The DHCP assignment works fine apparently, the command "ifconfig" gives the correct ip that the router assigns to each machine. However, the command "ping localname" tries to ping a wrong address

For example, the computer name "shuttle", recognized by the router, receives the ip 192.168.1.2, and this is what "ifconfig" displays. 

But when I type  "ping shuttle"
I get the message  "PING shuttle (212.68.205.83) 56(84) bytes of data"
which of course is wrong.  The consequence of this is that I cannot communicate between the computers in the LAN

It looks like the DHCP does not convert local names. But the router has  the local names registered in his configuration page, and windows worked fine before only with tcp/ip protocol

what am I missing?

thanks a lot in advance to anyone who can help me !!!
(in the meantime I continue with static IPs)

---

### Post by dcstar on 2007-09-22
> **pacohc said:**
> 
..........
But when I type  "ping shuttle"
I get the message  "PING shuttle (212.68.205.83) 56(84) bytes of data"
which of course is wrong.  The consequence of this is that I cannot communicate between the computers in the LAN

It looks like the DHCP does not convert local names. But the router has  the local names registered in his configuration page, and windows worked fine before only with tcp/ip protocol

what am I missing?

thanks a lot in advance to anyone who can help me !!!
(in the meantime I continue with static IPs)

It is a DNS issue, either your DHCP server is not supplying correct DNS info (it may by ok for Windows, though....), or (more likely) you have to manually set the correct DNS info in your Linux setup - including the "search domain".

Check the contents of your /etc/hosts file and compare DHCP versus static.

---

### Post by pacohc on 2007-09-27
Thanks David for your comments. 

Your suggestion to look at the domains helped me find something: in linux everything works fine adding the domain "local", for example, I can "ping asus.local" and "mount asus.local:/home/public", but the samba shares don't work in the windows 98 inside the QEMU emulator nor in the real windows XP computer connected to the local network. This may give a clue to what I am doing wrong, I don't know

The fact is that if I change back to static IPs with all local hosts listed in /etc/hosts then everything works fine, both linux ping and mount commands and samba shares inside  windows in Qemu emulation, also to the external windows XP, so I leave this way for now, in the future I will probably keep investigating further

regards
paco

---

### Post by pacohc on 2007-10-22
I spent several days trying network setups, also restarting the ubuntu 7.04 installation from scratch again several times. no way. I decided to give up with this and stay with manual IPs

Then 7.10 came, I upgraded, and, just to be sure, I tried the same again. ALL WORKS FINE NOW !, I did nothing, just works as comes out of the box, everything connects fine, samba shares between linux computers, drive maps to linux and windows computers, internet and email, pings and also network access between virtual qemu pcs and hosts

For me it is clear that either it was a bug in 7.04 or there is some "improvement" in the default network configuration in ubuntu 7.10, whatever, now it REALLY WORKS

now this thread can be really closed

---

### Post by pacohc on 2007-10-23
well, unforntunately the good news are not true anymore, after a short period the system behaviour reverted to the same situation as before with 7.04, no idea what I did, other that updates and so on

all works ok but, for connecting shared dirs between local computers in samba I must add the suffix ".local"

for example, connect to smb://asus
gives error

connect to smb://asus.local
works fine

any suggestion from anybody what to loo at?

thanks a lot

---

