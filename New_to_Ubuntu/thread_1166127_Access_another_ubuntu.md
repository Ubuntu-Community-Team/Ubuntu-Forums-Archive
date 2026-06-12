---
title: "Access another ubuntu"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by piousp on 2009-05-21
Ok, i know this may be really easy but i didnt have to use it until now.

Scenario: Image a network with 2 computers (even same subnet), one with ubuntu 9.04 and the other with u9.04 as well.

What i need is to access the other computer, say, his /home fs to read some files. My first guess was ssh, but ubuntu has shh closed by default.

How i can i access those files? Should i create an user for me in the other ubuntu? Is that even secure?? Thanks in advance

---

### Post by tomcheng76 on 2009-05-21
If both server and client uses Ubuntu, you just need NFS
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by issih on 2009-05-21
Options galore...

1. use samba, which is pretty easy just right click and select sharing options on the directory in question, then let the OS install what is required when prompted.

2. Use ssh - you just need to install Openssh server on the machine you want to log into (they only have clients by default) just have a poke around in synaptic and install the server, then you can connect to server from places and use ssh (or use the terminal)

3. NFS as suggested above.

Hope that helps

---

### Post by piousp on 2009-05-21
Thanks for the answers!!! ;)

I'm gonna try the openssh first, since NFS seems to requiere a bit more work. Just in case, both are the default desktop edition.
Alright, let me do the stuff and i'll tell you how it went!!

SSH is working like a charm!!! THANKS a lot!
How did i mark this as solved again? :P

---

