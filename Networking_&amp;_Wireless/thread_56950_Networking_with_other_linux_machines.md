---
title: "Networking with other linux machines"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by klutzini on 2005-08-14
Hi there,

I have a network through a router (10.0.0.1 - 10.0.0.?) and want to connect to 2 other linux (ubuntu and Kubuntu) machines.

What is the best way to connect to them? ie: what programs and how.

Also, how do I then add a printer connected to 1 machine and access it from another?

Hope I have made myself simple enough. (pics and few words help!!)

Regards

Paul

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=klutzini]Hi there,

I have a network through a router (10.0.0.1 - 10.0.0.?) and want to connect to 2 other linux (ubuntu and Kubuntu) machines.

What is the best way to connect to them? ie: what programs and how.

Also, how do I then add a printer connected to 1 machine and access it from another?

Hope I have made myself simple enough. (pics and few words help!!)

Regards

Paul[/QUOTE]

What kind of connection are you talking about?  Do you just want a basic TCP/IP connection, or do you have more specific protocols in mind (SSH, FTP, TELNET, SMB (Windows File Sharing), NFS)?

---

### Post by klutzini on 2005-08-14
well, having not had windoze for a long time (thank goodness!!) I don't know which is the best one to use.

I used to browse and copy/move files via network neighbourhood, so something along those lines would be good, though as I said, I don't use windoze anymore. Just Linux!!

Each machine has a ip address as well ie: 10.0.0.6 etc..

Hope this answers your reply. If it helps, reply via ICQ or anyother IM

---

### Post by cwaldbieser on 2005-08-15
[QUOTE=klutzini]well, having not had windoze for a long time (thank goodness!!) I don't know which is the best one to use.

I used to browse and copy/move files via network neighbourhood, so something along those lines would be good, though as I said, I don't use windoze anymore. Just Linux!!

Each machine has a ip address as well ie: 10.0.0.6 etc..

Hope this answers your reply. If it helps, reply via ICQ or anyother IM[/QUOTE]
Well, for copying files and doing remote administration, nothing beats "ssh" and "scp".  You need to install "sshd" on the machines that act as servers, so if you copy files back and forth a lot, you probably want to install it on both.

I am not sure about the printer sharing.  If I have some time, I will try to look up the info-- I am pretty sure you can do it via CUPS.

---

