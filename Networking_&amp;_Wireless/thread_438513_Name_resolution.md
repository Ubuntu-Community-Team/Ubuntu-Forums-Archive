---
title: "Name resolution"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by Eladon on 2007-05-09
Well, I have spent hours reading lots of posts & web pages, and all I can say is, I must be really missing something, because getting computers to talk to each other on a LAN with names rather than IP address can't be rocket science.  I am certainly no expert in name resolution.  But one thing is for sure, it's no where near as easy as setting up a couple of Windows boxes.

I am running an Edgy server which I set up as a DNS server, and my desktop is also running Edgy.
I am not however using the DNS server for DHCP, so maybe that's what makes things not work?

I was never able to get DNS to do anything useful for me, so I also installed Samba on both machines and set up the server as a WINS server, and directed the workstation to use my server for WINS.  But my desktop still can't ping my server using it's name.  Ironically, I have always been able to browse to other machines from Nautilus without problems (and it sees their names), I don't know how that's possible.

So rather than pummel you with too many details, does someone know of a good guide for a non expert to set up name resolution on a server that has a static IP & workstation(s) that use DHCP (not provided by the server)?

Thanks!

---

### Post by chili555 on 2007-05-09
Well, the quick and easy way is to amend the /etc/hosts file of your desktop(s) to add a line:```
192.168.0.5  server
```Substitute the actual name and IP address as appropriate.

You will then be able to ping -c3 server or ssh user@server, etc.

The Winbind/Samba guys will scream like banshees, but on a simple linux to linux network, it works perfectly.

---

### Post by Eladon on 2007-05-10
Yeah, I guess I could do that, at least to hold me over until I can figure out a more automatic way to do it.  Eventually I will have several desktops running, it would be nice to not have to be manually fixing host files.  But beggars can't be choosers I suppose!  :)

---

### Post by dannyboy79 on 2007-05-15
> **Eladon said:**
> Yeah, I guess I could do that, at least to hold me over until I can figure out a more automatic way to do it.  Eventually I will have several desktops running, it would be nice to not have to be manually fixing host files.  But beggars can't be choosers I suppose!  :)

if you want to use WINS than you need to update your nsswitch.conf file within /etc/
I have written up a guide here for using hosts file for name resolution and the other person wrote it up using WINS but didn't really say that. also, ahve you enabled NETBIOS over TCP/IP in windows?

his way:
[http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+resolution](http://ubuntuforums.org/showthread.php?t=88206&highlight=hostname+resolution)

my way:
[http://ubuntuforums.org/showthread.php?t=391601&highlight=resolution](http://ubuntuforums.org/showthread.php?t=391601&highlight=resolution)

---

