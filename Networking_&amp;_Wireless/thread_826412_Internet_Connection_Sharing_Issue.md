---
title: "Internet Connection Sharing Issue"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Malh on 2008-06-11
Here's the scenario:  I have a server running 7.04 that has device eth0 hooked directly to a fiber modem with a static IP.  Device eth1 is hooked to a switch that is hooked to 2 other switches.  I'm trying to use said server to share the internet connection from device eth0.  It works with 2 computers out of about 20 so far, and it was working previously with all machines.  I have the machines set up for DHCP but the machines that don't work have the default gateway incorrect by default.  The non-server machines are running Mac OSX and XP/Vista.  What is causing this problem?  I have tried rebooting and unplugging the switches multiple times.  Thanks in advance.

---

### Post by hariprs on 2008-06-11
Post your DHCP server configuration.

---

### Post by molotov00 on 2008-06-11
This might be a dumb question, but if "it was working" then what has changed since then?

It does seem wierd that some machines work but others don't. Is it possible they are remembering the old Gateway instead of fetching the new one (which doesn't get sent by the server correctly)? If that's the case then hariprs's got the right idea with the config.

---

### Post by Malh on 2008-06-12
The problem is I dont even know what I'm using for DHCP.  I'm about to do a fresh server install of 8.04 and wipe out all of these config files and start over from scratch to see if that helps.  Will post results once I start over with fresh config files.

---

### Post by Malh on 2008-06-12
Ok so I started out from scratch and now DHCP is assigning addresses to all the computers, however my FTP and Apache servers are not working anymore.  Any idea what would cause this problem?

---

