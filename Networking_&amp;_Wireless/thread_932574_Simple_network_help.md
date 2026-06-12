---
title: "Simple network help"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by lemmy999 on 2008-09-28
I have three PCs, all running Ubuntu, all are connected via a modem/router. I want to be able to access files on each of the machines from any of the  other machines. Can anyone point me to a simple guide to sort this out. I have searched on this forum but most people seem to need help networking between Linux and MS machines.

---

### Post by cariboo on 2008-09-28
If you have a mixed network have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

If all the computers on the network are linux based, have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

You can also mix the two nfs, to connect to linux based computers and samba to allow windows computers to connect to your network.

Jim

---

### Post by lemmy999 on 2008-09-28
Well, it looks pretty easy to start off with. BUT 
1. Do I have to decide that one of my PCs is the server and the other two are client machines?

2. If the answer to 1 is Yes then how am I supposed to know what its called?

eg ( from [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889))
> Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

---

### Post by ww711 on 2008-09-28
> **lemmy999 said:**
> Well, it looks pretty easy to start off with. BUT 
1. Do I have to decide that one of my PCs is the server and the other two are client machines?

2. If the answer to 1 is Yes then how am I supposed to know what its called?

eg ( from [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889))

Yes you will have to decide on which pc will be your server.

You can find out the name of the PC in Linux by loading up the terminal application(if you are using gnome desktop manager, navigate to Applications -> Terminal), this will display a window with the information you need to get the pc name, e.g.'some.username@this.will.be.the.name.of.your.machine'

---

### Post by lemmy999 on 2008-09-28
Maybe I haven't been specific enough. All I want to do is be able to access /home on each of my machines from any other machine on the network so that I can move/copy files around. 

Whats confusing me now is the instruction 
> The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

Surely /home is already mounted!

---

### Post by lemmy999 on 2008-09-28
@ ww711

thanks- that seems eminently sensible!

---

