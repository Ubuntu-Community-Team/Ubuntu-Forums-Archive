---
title: "Getting Ubuntu working on a windows network"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by hexbase on 2008-05-18
Hi,

I've a small network (4 pc). 3 pc have windows xp and 1 has ubuntu 8.04(installed yesterday).
The thing is i cannot see the other machines. I get a nt_status_bad_network_name error on smb4k

Could you please give me some advice or a link of a tutorial or how-to explaining how i get it working?


Thanks!

---

### Post by hexbase on 2008-05-18
After some smb.conf editing, i get:

Could not connect to server X (X is my hostname and my user on ubuntu)

Connection error: nt_status_bad_network_name

Can anybody help me?

---

### Post by Iowan on 2008-05-19
I found [this]("http://ubuntuforums.org/archive/index.php/t-61425.html")... It's more about printing, but suggests the hostname is somehow incorrect. Are you having problems connecting TO Ubuntu or FROM Ubuntu?  Another thread I found asked about Windows firewall settings.

---

### Post by hexbase on 2008-05-20
Now i can connect, but i've problems listing the network shares on smb4k.
Also, the windows machine doesn't see my ubuntu machine! :mad:

Thanks!

---

### Post by mapes12 on 2008-05-20
I couldn't get sharing to work at all across my home LAN therefore I gave up on network shares. Having read a number of posts my network now accesses clients using Secure Shell - SSH. I find it much easier.

These links may be helpful:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[http://www.openssh.org/](http://www.openssh.org/)

---

### Post by hexbase on 2008-05-20
Well, i gave up :( I've reinstalled windows. I don't have the experience to configure samba, and i cannot have a machine without network. Yes, im a noob, maybe that's why i couldn't get it running, but at least the developers should do it easier, at least as easy as windows.

---

