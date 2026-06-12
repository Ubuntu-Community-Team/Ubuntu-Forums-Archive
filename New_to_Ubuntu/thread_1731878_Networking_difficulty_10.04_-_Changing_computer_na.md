---
title: "Networking difficulty 10.04 - Changing computer name?"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by pracrichard on 2011-04-17
Hi, 
I have been having trouble connecting my desktop computer to my network. It is accessible from windows computers on my workgroup (called WORKGROUP) but not from my ubuntu laptop. 

Internet through my Old Netgear cable router and the Virgin cable broadband is fine

All the computers are visible in 'computers near me' but when I try to connect I get the dreaded "unable to obtain share list from server"

Details of problem:
**The lappy cannot access shared folders on the desktop**
The desktop **can** access shared folders on the Lappy.
Both Desktop and Lappy can access my Netgear NAS-ID box perfectly.
Neither can can access a windows 2000 computer on the system but that may be a problem with the win 2000 machine. 
The Win 2000 machine can be accesses from other windows machines.
The Win 2000 machine can see and write to shared folders on both Desktop and Lappy

Both Desktop and Lappy are running ubuntu 10.04 Lts.

Now for the specific question:[INDENT]On the list of 'computers near me' in WORKGROUP the desktop appears as '**RICHARD2-DESKTO**' (no 'P' at the end) despite being actually registered as 'richard2@richard2-desktop' which appears in the terminal. **Could this be too long a name for the system to cope with?** I have never deliberately created this truncated name. **If this is the case how can I change the name to a shorter one?**
[/INDENT]Many thanks

Richard

---

### Post by Wobblybob on 2011-04-18
I think that name is far too long for windows [not sure of the limit] to rename in a Terminal 

sudo gedit /etc/hosts

and rename [keep it short] and resave

and again for 

sudo gedit /etc/hostsname

replace gedit for you installed text editor of choice. reboot networked PC's to see the updates.

---

### Post by bodhi.zazen on 2011-04-18
If you manually change you hostname you need to change it in both 

/etc/hostname 

AND

/etc/hosts

or you will break sudo.

Your problem is with dns. You should be able to mount your share using the ipaddress and not the hostname.


If you want to use the hostname rather then the ip address, you can either edit your windows hosts file adding in your ubuntu samba server , install wins, or install a dns server, dnsmask is easy ;)

---

### Post by pracrichard on 2011-04-20
A great many thanks for quick replies. Bodi-Zazen lables worked. a very simple change when you know how and my network now works perfectly.

For future reference to anybody eles viewing this thread it is '**hostname**' which works not 'host**s**name' as in wobblybobs response. Simple typo which we all make.

Richard:P

---

