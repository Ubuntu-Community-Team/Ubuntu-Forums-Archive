---
title: "Subnets And Samba"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by shonen on 2007-05-21
I'm working on an Ubuntu/Samba server for file storage and backup at my work, and have successfully used one of the tutorials around here to set up a great file sharing devices with ADS as the security of choice

(I thank the community here for that)

But I have a new problem that I was wondering if you all could help me address, My boss seems to have trouble finding the server when he is on any other subnet. 

So the server is on 192.168.1.*, he can't find it on .2 or .3  and so on...

How can I make the shared file "seen" on all subnets successfully so that anyone with the subnet IPs can see and back up what they need to!

Thanks in advance!

~shonen

---

### Post by tomroffe on 2007-05-21
is your samba config bound to the 192.168.1.0 subnet...

post your smb.conf file

---

