---
title: "Connecting Two Machines"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by azuiden on 2005-11-12
What I would like to do is connect two machines using a cross over cable to be able to share hard drives and use synergy [[http://synergy2.sourceforge.net/]](http://synergy2.sourceforge.net/])

On one machine i have Ubuntu 5.10 and on the Other Windows XP all service packs.

The cable is in both...

now what do i do?

---

### Post by mips on 2005-11-12
For file sharing between Linux & Windows you need SAMBA installed on your Ubunto box

For Synergy to work I guess you will just have to configure TCP/IP on both LAN cards. Ensure you use a common IP Subnet and Mask for both PC's and assign each PC a unique IP Address from that IP Subnet.

---

### Post by azuiden on 2005-11-13
i have samba installed on my ubuntu machine and the wiki article talks about features i don't have....

---

### Post by mips on 2005-11-13
[QUOTE=azuiden]i have samba installed on my ubuntu machine and the wiki article talks about features i don't have....[/QUOTE]

Please be a bit more specific, what features are you refering to ???

---

### Post by azuiden on 2005-11-14
well i mean i installed samba and i would like to know what i have to do from there


right now i typed in apt-get install samba

unfortunately the wiki seems to be a bit out dated, as it talks about the networks tool button saying something about windows networking

---

### Post by mips on 2005-11-14
I have never used samba so cannot give you more specific details put wil try and point you in the right direction.

You have to configure the windows machine for file sharing and configure samba as well.

Do a search for SAMBA in these forums and I'm sure your questions have been answered already.

The official samba website is here:   [http://us4.samba.org/samba/](http://us4.samba.org/samba/)

Everything you will ever need to know about samba you will find there. They have HOWTOs, Docs etc.

---

