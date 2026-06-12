---
title: "[SOLVED] How to fix file and folder sharing in 7.04"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-10-31
I set up a shared folder on my linux laptop and was able to view it on the linux desktop. I am using smb to share the folder.

What I need to be able to do is write and copy files to the shared folder from the desktop. 

When I open the folder I am not asked for a password. 

How do I get permission to write and copy for the desktop user?
Why am I able to view the files in the folder without a password?

I've attached screenshots from the network manager.
This is  a wireless network. The dns is coming from the ISP over ppp0.

hosts file:
127.0.0.1 localhost
127.0.1.1 SOL

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by jludeman on 2007-11-07
I got this and a lot of other problems on my home lan fixed. With help from the web of course. See the link below for a detailed description.
[http://ubuntuforums.org/showthread.php?t=587560](http://ubuntuforums.org/showthread.php?t=587560)

---

