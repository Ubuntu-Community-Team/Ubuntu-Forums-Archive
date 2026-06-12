---
title: "Trouble with Broadcom wireless"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by resistor2004 on 2007-04-02
I'm having trouble with  getting my Broadcom wireless card to work.  It's using BCMWL5 under Windows, and I've tried all the suggestions I could find on this forum to get it set up in ndiswrapper to no avail.

Here's the 'lspci | grep Broad' output:

```
0f:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

'ndiswrapper -l' outputs:

```
Installed ndis drivers:
bcmwl5       driver present, hardware present
```

But, even after a restart, it's not showing up as a network interface.  Any suggestions?

---

### Post by resistor2004 on 2007-04-02
OK, I downloaded the newest ndiswrapper debs on another computer and installed them, and now wlan0 is showing up as a network interface.  It even works if I do "sudo dhclient wlan0" from the command line.  However, activating it from the Gnome network manager in the system tray doesn't seem to work.  Any suggestions?

---

### Post by racin on 2007-04-02
Install Fiesty and do the following it is listed under a Howto for Broadcom by compwiz918. I had the same problem with Edgy and could never get it to work. Doing it like this it was going in 5 minutes. You'll need a wired connection.
Good Luck! 

Feisty

Download [http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb](http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb) 
and double click it to install. Reboot. Enjoy wireless.

---

### Post by ioxer on 2007-04-05
> **racin said:**
> Install Fiesty and do the following it is listed under a Howto for Broadcom by compwiz918. I had the same problem with Edgy and could never get it to work. Doing it like this it was going in 5 minutes. You'll need a wired connection.
Good Luck! 

Feisty

Download [http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb](http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb) 
and double click it to install. Reboot. Enjoy wireless.

As a side note, something with that link is messed up. Here's the URL of the file:

[http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)

---

### Post by yzargari on 2007-05-13
Hey Guys,

Did anyone succeed with that? I tried it on my HP dv5084 (Broadcom 4318) and it didn't make much difference. It detects the available wireless network, but is unable to connect to it.

Any ideas?

---

### Post by corytoneill on 2007-05-16
same problem i see the things but cannot connect

---

