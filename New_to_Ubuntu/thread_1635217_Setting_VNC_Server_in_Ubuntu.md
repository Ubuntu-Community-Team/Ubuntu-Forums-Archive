---
title: "Setting VNC Server in Ubuntu"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Avidanborisov on 2010-12-01
Hello Everyone!
I need to set a vnc server on ubuntu for being able to access it with remote desktop connection. i tried many things as vnc4server or tightvncserver from terminal but they didn't work or i was wrong. any suggestions?

---

### Post by pricetech on 2010-12-01
SSH.  It's much more secure and supported natively in *nix.  If you want a GUI, NX from nomachine dot com is what I use.

Just plain works.

There's a Windows client as well.

---

### Post by spiky001 on 2010-12-01
What do you wish to achieve from this is it just file transfer? is it from inside a lan or external ip

---

### Post by Avidanborisov on 2010-12-02
I already have ssh but i need vnc server for my local ubuntu desktop.

---

### Post by Avidanborisov on 2010-12-02
Anyone?

---

### Post by smartmelvin on 2011-02-12
My ip address shows a different public address 59.164.18.33 on whatsmyip.com and in connection information it shows 10.15.242.167 which also shows on the remote desktop preferences how do i get other machines to connect to me on which ip can they remotely access my comp?

I am connected by LAN to the providers server through a webpage which i logon with uid and pwdfor net access. 

Any Help would be appreciated.
Melvin...

---

### Post by HermanAB on 2011-02-12
Howdy,

Please don't use VNC, otherwise you will be back here in a few days complaining that your machine has been hacked.  These forums are full of tales of VNC woe.

Learn how to use the Secure Shell.  It is pretty much all you need:
$ ssh -X -C -c blowfish user@server gnome-panel

That will get you a Gnome menu bar for the remote system.  Anything you click will run remotely and display transparently on the local desktop.

---

### Post by smartmelvin on 2011-02-12
Thanks Herman for the advice still struggling to understand networking [https://help.ubuntu.com/community/VNC#accessing-your-pc](https://help.ubuntu.com/community/VNC#accessing-your-pc)
Guess I will have to get to the basics of it. Ubuntu is amazing but one has to really be a geek to use it.

Melvin...

---

### Post by smartmelvin on 2011-02-12
Teamviewer solves it all!!! 
[http://ubuntuforums.org/showthread.php?t=1580429&highlight=vnc&page=4](http://ubuntuforums.org/showthread.php?t=1580429&highlight=vnc&page=4)

Thank god for ubuntu forums.

---

