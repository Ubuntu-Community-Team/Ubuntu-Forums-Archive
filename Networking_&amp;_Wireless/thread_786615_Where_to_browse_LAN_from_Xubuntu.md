---
title: "Where to browse LAN from Xubuntu?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Hannz on 2008-05-08
Hi All!
I'm giving another shot at Xubuntu right now. I tried it a couple of months back, and now I'm still having the same problem.

I have a small home office network, consisting of one Ubuntu 7.10 as a file server, and five computers (three Ubuntu 7.10 and two XP) that connects to the file server. On my way to upgrading one of the 7.10 to 8.04, but since it's an old computer (P2-333MHz with 160MB RAM), I thought I'd try using Xubuntu.
Installed and working alright, I can connect to the internet via ADSL gateway. I can ping the file server, but I don't know where I can browse it from. Ubuntu's Nautilus got the 'Places - Network' to start browsing the network, but I can't find (or don't know yet) where to go from Xubuntu's Thunar.
I know this is kinda stupid, and I did try to search about this in the documentation and the forums, but can't find an answer. Do I have to install something or anything? I'd like to use Xubuntu at least on this computer, it's testing my patience if I try to use Ubuntu on it :-|

---

### Post by superprash2003 on 2008-05-08
go to places->computer and in location .type smb://(ip of windows machine)

---

### Post by bodhi.zazen on 2008-05-08
Optional : First with Xubuntu , enable your menu by right clicking on the desktop and selecting "Desktop Settings"

Click the "Behavior" tab and select off, check off, the box "Show Desktop menu on right click".

==============

1. To share a file :

Go to "System -> Shared Folders" -> Elect to "Install Services" and Install Samba. Log off and back on. You should be able to share folders. 


==============

2. Browsing network shares, similar to Ubuntu, is not supported on XFCE (yet) ...


Two options :

pyNeighborhood : [http://programminglinuxblog.blogspot.com/2007/06/windows-file-sharing-samba-xubuntu.html](http://programminglinuxblog.blogspot.com/2007/06/windows-file-sharing-samba-xubuntu.html)

 Nautilus Share : [http://www.vincentkong.com/?q=node/138](http://www.vincentkong.com/?q=node/138)

---

