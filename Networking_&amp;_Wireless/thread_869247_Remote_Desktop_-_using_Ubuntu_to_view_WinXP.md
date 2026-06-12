---
title: "Remote Desktop - using Ubuntu to view WinXP"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by phantomjoker on 2008-07-24
I'm using Hardy at the moment and want to be able to remotely view and access my Windows computer - running XP

I have set the XP computer to allow remote "desktop'ing" and turned of the windows firewall - I am not aware of any other firewall on that computer.

The computer is in my local network so I'm only trying to connecting to it within out wireless. 

I use the 'remote desktop viewer' that hardy gets as standard - and type in it's IP address and port no. 3389 and I get a message saying connection refused after a period of about 30 seconds. If I type any other port or IP I get the same message but within 2 seconds - so I think it is 'almost' connecting - if thats possible.

Also if I attempt the same thing in the terminal I get the following message -
> mckenzie@ubuntu:~$ rdesktop 192.168.2.2:3389
Autoselected keyboard map en-gb
ERROR: connect: Connection refused
mckenzie@ubuntu:~$ 


any help would be greatly appreciated.

cheers

---

### Post by Nem1976 on 2008-07-24
> **phantomjoker said:**
> I'm using Hardy at the moment and want to be able to remotely view and access my Windows computer - running XP

I have set the XP computer to allow remote "desktop'ing" and turned of the windows firewall - I am not aware of any other firewall on that computer.

The computer is in my local network so I'm only trying to connecting to it within out wireless. 

I use the 'remote desktop viewer' that hardy gets as standard - and type in it's IP address and port no. 3389 and I get a message saying connection refused after a period of about 30 seconds. If I type any other port or IP I get the same message but within 2 seconds - so I think it is 'almost' connecting - if thats possible.

Also if I attempt the same thing in the terminal I get the following message -


any help would be greatly appreciated.

cheers



If I remember right your XP machine needs to have a password for the user account your using.  I have tried to RDP from a XP workstation to another XP workstation and I couldn't do anything unless I had a password setup on the account I was logging in with.

---

### Post by superprash2003 on 2008-07-25
the vnc way works neat [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html)

---

