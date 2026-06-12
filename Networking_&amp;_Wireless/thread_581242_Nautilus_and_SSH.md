---
title: "Nautilus and SSH"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by mivo on 2007-10-19
I have an older computer with Xubuntu 7.10 (connected to my router/switch) that runs an OpenSSH server and that I use for backing up stuff. From my Ubuntu 7.04 machine I can ssh to it just fine in a terminal (no lag or delays). However, I am unable to connect to it using Nautilus. After a couple of minutes it just says: **Nautilus cannot display 'ssh://username@192.168.1.2'. Please select another viewer** (it never asks for the password or tries to access the keyring). Other times, it reports:Timeout reached. Nautilus does however connect just fine to my employer's CentOS server, also using SSH. Using *ssh username@192.168.1.2* in a terminal works well.

I saw some older threads about the same trouble, but no solutions. Am I looking for a problem on the server or on the client side?

---

### Post by mivo on 2007-10-19
Well, the solution provided [here](https://answers.launchpad.net/ubuntu/+question/9146) fixed the problem. This wasn't exactly the same problem, though, and I don't understand why this worked or why this was needed for Nautilus, but not for the terminal ... or, and that confuses me more, why it was not needed to connect to my employer's remote machine, just to my local box.

Would be great if someone with more experience could shed light on this. If only so that I learn. :)

---

### Post by Wuu on 2007-11-13
Don't help for me! I easy create luncher for FTP but can't connect to ssh :( 
and i add config file to .ssh folder! 

nautilus --browser ssh://[COLOR="Red"]user[/COLOR]@[COLOR="Red"]host[/COLOR]:[COLOR="Red"]port[/COLOR]

maybe bad command to do this? Nautilus after some time saying **Please select another viewer and try again.**

---

