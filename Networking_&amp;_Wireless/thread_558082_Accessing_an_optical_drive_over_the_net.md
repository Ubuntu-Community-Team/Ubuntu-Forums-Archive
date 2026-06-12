---
title: "Accessing an optical drive over the net"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by fazza on 2007-09-23
hi all
sorry if this is in the wrong place...
my laptop is seriously on the blink - doesn't always boot up, can't install anything etc, so I need to back up the data. I have no burner installed, so I came up with a few ideas - remote desktop control via vncviewer (couldn't move any files), networking between pcs (couldn't find each other), shared folders (haven't got the correct programs installed, and can't install them - long story) and remote login (can't access hardware). Now I'm completely stumped. The only thing I can think of is accessing the burner over the net, except I don't know how.
Could use a usb stick, but there is much too much data for that!
If anyone can help, thanks in advance.

ps I'm only 14.11 y.o. :P

---

### Post by obrient on 2007-09-23
Have you tried SSH? Where are you backing it up to another linux box or a windows box? Is Samba installed?

If Samba is installed on your machine that you are backing up to you should be able to access it over the wire.

---

### Post by fazza on 2007-09-25
how do I use ssh? not sure if ssh or samba are installed. I was backing up to another linux box, running ubuntu 7.10. Think it's got samba.
Cheers:KS

---

### Post by obrient on 2007-09-26
Okay if you indeed have samba installed on your 7.10 box which you are backing up to you will want to mount a folder across the network from the box you are trying to backup.

To do this go to **Places>Connect to Server** on the box you are backing up select Window Share and then enter the share name that you have set up on the 7.10 box. (if you don't get this then you might have to set up the share on the box). Then you should be able to drag and drop files across the network. 

Hope this helps

---

### Post by Jose Catre-Vandis on 2007-09-26
Install openssh-server on your laptop, then on your remote machine, open nautilus, then click on Places/Connect to Server, choose SSH from first box, Ip of laptop in second box and click connect. your laptop should be listed on the folder tree in nautilus. Double click on it, and you will be asked for password (of laptop user) enter password and then you should be able to copy files over. It'll be slowish but will get the job done.

---

### Post by fazza on 2007-09-27
ok, thanks obrient. I'll try it
Jose, I cannot actually install anything on my laptop at the moment... in fact, here's the post I made back in June [http://ubuntuforums.org/showthread.php?t=461045]("http://ubuntuforums.org/showthread.php?t=461045"), which still hasn't been fixed. (btw, I do now realise the concept of MySql.)

---

### Post by Jose Catre-Vandis on 2007-09-27
why not use a usb stick then, and do it bit by bit

---

