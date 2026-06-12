---
title: "Accessing other computers on the network"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by jigantor on 2006-09-01
I'm had a small (Cat6 cable) network running at my house for most of the year - 3 windows machines and my Ubuntu desktop. Having recently got a laptop (also running Ubuntu), I added a switch upstairs to cater for it. So, the network is now 3 windows, 2 Ubuntu. All computers can access the internet fine. Both my Ubuntu machines can access the Windows machines. But for some reason, neither Ubuntu machine can access the other. I know this is probably a stupidly obvious question (and I apologise!), but I haven't been able to find anything about it anywhere. So: how do I access other Ubuntu machines over a network? Any help would be appreciated - I'm getting sick of transferring files on a usb stick!

---

### Post by goatflyer on 2006-09-01
You want to install and setup samba.  Then you can share some directories with all other machines on your network - including windows machines.

---

### Post by blackened on 2006-09-01
Or you could use Gnome's built-in Connect To Server function.

In the menu bar go to Places->Connect to Server.

Or in Nautilus go to File->Connect to Server.

Both will bring up the same dialog. Just set the internal ip, the folder path, and the user name accordingly.

[IMG]http://static.flickr.com/96/230772483_e81ba8c887.jpg[/IMG]

Edit: It's helpful to use static ip addresses within the network, but not required.

---

### Post by sebastfr on 2006-09-01
> **blackened said:**
> Or you could use Gnome's built-in Connect To Server function.

In the menu bar go to Places->Connect to Server.

Or in Nautilus go to File->Connect to Server.

Both will bring up the same dialog. Just set the internal ip, the folder path, and the user name accordingly.

[IMG]http://static.flickr.com/96/230772483_e81ba8c887.jpg[/IMG]

Edit: It's helpful to use static ip addresses within the network, but not required.


Well that'll work only if the ubuntu machines have some kind of server set up which seems to be the problem!

solution: make sure you have sshd/samba installed (and started!) on both ubuntu machines then you can use the above dialog box (and pick up the correct protocol eg. smb,ssh)

Seb

---

### Post by blackened on 2006-09-01
Ah too true. You know what they say about assumptions eh. :)

---

