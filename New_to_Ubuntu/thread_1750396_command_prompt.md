---
title: "command prompt"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by Dr. div11 on 2011-05-05
i am basically stuck in command prompt... 

which command to type in so that the process stops and my normal ubuntu screen loads

---

### Post by ubudog on 2011-05-05
Try typing:

```
startx
```

and see what happens.

If it gives you any errors, post them here.

:-)

---

### Post by tubunu on 2011-05-05
What process are you talking about? Are you trying to boot Ubuntu? Type: startx

---

### Post by Dr. div11 on 2011-05-05
> **ubudog said:**
> Try typing:

```
startx
```

and see what happens.

If it gives you any errors, post them here.

:-)



FATAl server error:
no screens found

please consult ..wiki...

ddxSigGiveUp : closing log
giving up
xinit: no such file or directory(errno 2) unable to connect to x server

xinit : no such process (errno 3): server error
..



i can also post pictures if u want me to .. of the whole screen..

---

### Post by ubudog on 2011-05-05
A picture would be nice, so that we can see everything that's going on.

Did you recently do updates, or an upgrade or something?

---

### Post by tubunu on 2011-05-05
I'm just guessing here, but do you have xorg installed?

---

### Post by Dr. div11 on 2011-05-05
> **ubudog said:**
> A picture would be nice, so that we can see everything that's going on.

Did you recently do updates, or an upgrade or something?



check this out ..i  ...donno what to do..

---

### Post by Dr. div11 on 2011-05-05
> **tubunu said:**
> I'm just guessing here, but do you have xorg installed?

what is xorg... and how to install it..

---

### Post by ubudog on 2011-05-05
You did install the Ubuntu Desktop Edition, not the server edition, right?

---

### Post by Dr. div11 on 2011-05-05
> **ubudog said:**
> You did install the Ubuntu Desktop Edition, not the server edition, right?

i dont know...and what is the difference ...and how do we differenciate..

---

### Post by ubudog on 2011-05-05
Well, the Desktop edition comes with GNOME/Unity (the desktop interface).  The server edition comes without a desktop interface, because it is designed for servers, not laptops and desktops.

---

### Post by lykwydchykyn on 2011-05-05
Xorg is definitely installed, otherwise "startx" would just return "command not found".


The problem here is either that X is not able to auto-configure the video hardware, or there is an xorg.conf file with the wrong driver specified.


Can  you post the output of 'lspci'?

Also, can you give some background on this situation: is this a new install?  Did you change hardware? upgrade?

---

### Post by Telengard C64 on 2011-05-05
> **lykwydchykyn said:**
> Xorg is definitely installed, otherwise "startx" would just return "command not found".

Exactly. Does the Ubuntu Server include Xorg?

> The problem here is either that X is not able to auto-configure the video hardware, or there is an xorg.conf file with the wrong driver specified.

That being the case, this may help fix or troubleshoot the problem.

```
$ sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.old
$ sudo start gdm
```

---

### Post by ubudog on 2011-05-05
No, I don't believe Xorg comes with Ubuntu Server.  I can log in to my server and check, brb.

---

### Post by ubudog on 2011-05-05
Hmm, I do have an X11 directory on my server, and I never remember installing X... so, I guess it does.  However, if I run startx on my server, it returns:
The program 'startx' is currently not installed.  You can install it by typing:
apt-get install xinit

---

### Post by Dondermans on 2011-05-05
> **Dr. div11 said:**
> i dont know...and what is the difference ...and how do we differenciate..

> **ubudog said:**
> Well, the Desktop edition comes with GNOME/Unity  (the desktop interface).  The server edition comes without a desktop  interface, because it is designed for servers, not laptops and  desktops.

Further to these messages, the screen shot you posted in [_message #7_]("http://ubuntuforums.org/showpost.php?p=10774290&postcount=7") states on line 11:
```
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
```I suppose that indicates you installed the server version by mistake.

---

### Post by Dr. div11 on 2011-05-05
> **lykwydchykyn said:**
> Xorg is definitely installed, otherwise "startx" would just return "command not found".


The problem here is either that X is not able to auto-configure the video hardware, or there is an xorg.conf file with the wrong driver specified.


Can  you post the output of 'lspci'?

Also, can you give some background on this situation: is this a new install?  Did you change hardware? upgrade?

..

what does output of lspci mean.??

yes it is a new install..
no i did not change the hardware... i tried upgrading.. but heres the thing..

check this post..
[http://ubuntuforums.org/showthread.php?t=1750346](http://ubuntuforums.org/showthread.php?t=1750346)

---

### Post by lykwydchykyn on 2011-05-05
> **Dr. div11 said:**
> ..

what does output of lspci mean.??

yes it is a new install..
no i did not change the hardware... i tried upgrading.. but heres the thing..

check this post..
[http://ubuntuforums.org/showthread.php?t=1750346](http://ubuntuforums.org/showthread.php?t=1750346)

It means to type "lspci" at a command prompt and tell us or post a picture of the output of that command.

Basically I want to know what your video hardware is, and that command lists the make and model of all PCI devices (including onboard stuff, of course).

If you know what your video card is, you can just tell us that instead.

---

### Post by ubudog on 2011-05-05
Yep, it appears that you're using Ubuntu server.  If you already have your data on it, then you probably want to copy that off, and install the Desktop edition.

---

