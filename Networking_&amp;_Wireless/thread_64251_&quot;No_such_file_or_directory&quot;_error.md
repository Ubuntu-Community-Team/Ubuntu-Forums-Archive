---
title: "&quot;No such file or directory&quot; error"
date: 2005-09-10
forum: Networking &amp; Wireless
---

### Post by Nicoscot on 2005-09-10
I'm afraid this is probably a really silly problem, nut I'm a n00b to linux, please bear with me...
I'm running Ubuntu Hoary Hedgehog and have a Thomson Speedtouch 330 rev. 4.00, so unsurprisingly I
couldn't get to the net. I followed line for line the instructions at

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html)

and everything went fine, until I got to the instruction:

sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets

I entered the instructions and got this back:

install: cannot stat `secrets': No such file or directory

I had saved "secrets" as a .txt file in my home directory, so I'm not sure what I'm doing wrong.
I tried saving it as .sxw but it didn't make any difference.

Help with this please?
Thanks in advance,
Nico.

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=Nicoscot]I'm afraid this is probably a really silly problem, nut I'm a n00b to linux, please bear with me...
I'm running Ubuntu Hoary Hedgehog and have a Thomson Speedtouch 330 rev. 4.00, so unsurprisingly I
couldn't get to the net. I followed line for line the instructions at

[http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html](http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html)

and everything went fine, until I got to the instruction:

sudo install -m 600 secrets /etc/ppp/chap-secrets &&
sudo install -m 600 secrets /etc/ppp/pap-secrets

I entered the instructions and got this back:

install: cannot stat `secrets': No such file or directory

I had saved "secrets" as a .txt file in my home directory, so I'm not sure what I'm doing wrong.
I tried saving it as .sxw but it didn't make any difference.

Help with this please?
Thanks in advance,
Nico.[/QUOTE]
File extensions are not the determining factor for file types in Unix-like systems.  If the your command is looking for a file called "secrets", it should literally be named "secrets" (without the .txt extension).

---

### Post by Nicoscot on 2005-09-10
D'oh! So THAT's what it was... I'll try as soon as I get home. Guess the linux learning curve is still ahead of me then.

Thanks for the tip.

---

