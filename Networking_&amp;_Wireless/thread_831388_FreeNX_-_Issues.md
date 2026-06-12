---
title: "FreeNX - Issues"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by stueng on 2008-06-16
hi, I have installed freenx from a hardy source and added a user + supplied a password

When I attempt to connect using either Gnome or KDE the authentication is successful however when the display is initialized I briefly get a window pop up (same size as chosen resolution) and then it promptly closes

there are no errors on the /var/log/nxserver.log file

NX> 148 Server capacity: not reached for user: stu
NX> 105 startsession  --link="wan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="stu" --type="unix-kde" --geometry="1024x768+448+184" --client="linux" --keyboard="pc105/gb" --screeninfo="1024x768x24+render" 

NX> 1000 NXNODE - Version 2.1.0-72 OS (GPL, using backend: 3.2.0)
NX> 700 Session id: medbuntu-1004-8A57159516E70E0DDCC9ACF26A10527A
NX> 705 Session display: 1004
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 222cc0bed596a5c50bd1b1b165595d0b
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 222cc0bed596a5c50bd1b1b165595d0b
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1009 Session status: terminating
NX> 1006 Session status: closed
NX> 1001 Bye.

---

