---
title: "[SOLVED] Printing Predicament"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by finch127 on 2008-09-07
Alright, so I have a very complicated situation here.

I have an HP All in One Officejet 6310xi.

The xi designating a scam from Sam's Club because it has no ethernet port and therefore it doesnt have its own IP.

It plugs into my Windows Server (XP) via USB then, but heres the messed up part. 

Through my terminal I can use xsmbrowser to view my Windows Net (XP) via SMB and when i go to my Server, I have to provide the username*(look at end of document) but no password and i can see everything including the printer I want to use. When I go to System, Administration, Printing on Ubuntu, I can add a new printer via Samba (HOME[my workgroup name]/SERVER[comp name with printer]/HPALLINONE[printers name] and I provide my own ppd that I know is correct because when i plug it in directly it works. However, over this network it doesn't work for some reason!!!

The address in the bar is smb://HOME/SERVER/HPALLINONE and it says the printer is idle. I sent a test page and it never prints no matter how long I wait or try.

I am not that well versed in Linux, but I do know basic command usage, and I need help in setting up this printer because it is frankly driving me mad. Thanks in advance to anyone who would help me, and I will post any necessary outputs.

*Ok so when I do this from the command line, I have to do it like this:
smbclient -I 192.167.1.13 -N -W HOME -L SERVER -U Administrator
and it works fine so I can see the server and printer, only see

---

### Post by finch127 on 2008-09-09
alright, i got it working after some tinkering

basically i reinstalled and reconfigured CUPS and i tinkered samba into navigation to the server IP and mooching off of it

thanks if you tried anyway :D

---

