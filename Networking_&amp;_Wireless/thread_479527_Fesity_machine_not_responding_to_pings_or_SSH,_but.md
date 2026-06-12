---
title: "Fesity machine not responding to pings or SSH, but can be seen via samba"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by chejrw on 2007-06-20
I've just done a fresh install of Feisty on a new machine, and I installed and configured samba, proftpd, and ssh (it's going to be a fileserver).  I'm testing it out from one of my other machines, and it connected fine to the samba share (a windows machine, via the 'my network places' interface).  However, the machine is not responding to pings, and attempts to connect via SSH or FTP time out.  

Suggestions?  I can connect to ftp/ssh via the loopback address on the machine itself, so I know the daemons are active.

One other thing - I can't get the GUI to load (x doesn't seem to like my video card - I'm trying to fix that also) so limit your suggestions to things I can do from a command line.  Thanks.

---

### Post by Macros42 on 2007-06-20
Did you open port 22 for ssh and port 21 for ftp? Ping could be Firestarter - I think by default it doesn't respond to pings - you have to allow replies.

---

### Post by chejrw on 2007-06-20
How would I go about doing that?  I'm connecting from within my own LAN, so the router isn't in play.  My other Ubuntu machine responds to pings and when I installed SSH it was able to connect right away - I didin't have to enable any ports there.

---

### Post by cdrw on 2007-06-20
are you using dhcp or static IP? if dhcp, give your machine a static one. Also try to connect your new machine directly to one of your existing ones with a cross over cable and see if it works.

cdrw

---

### Post by chejrw on 2007-06-20
I thought I had set it to static, but I just ran ifconfig, and it's not on the IP I assigned it.  I edit my /etc/network/interfaces file and put in the IP, gateway, and subnet, then restart networking, and it doesn't pick up the proper IP.  I have no idea why.

In any case, when I try to ping/ssh/ftp the IP it *is* on, it still doesn't work.

I don't have a crossover cable, but I could try to pick one up if you think it would help.

---

### Post by chejrw on 2007-06-21
Sorry to bump, but I'm still looking for a resolution to this.  I got my video situation sorted out, and now all I need is for my other computers to be able to see this machine on the network and I'll be all set!  It's very frustrating.

---

