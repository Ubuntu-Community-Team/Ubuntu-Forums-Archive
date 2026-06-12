---
title: "Remote Desktop ?"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by dtrot55 on 2009-08-04
I currently setup a Ubuntu computer but I want to be able to throw the computer in a corner and just access it with my windows machine through remote desktop....anyone know how I could go about doing this?

---

### Post by Paddy Landau on 2009-08-04
I would try VNC.

Check out the following, which are more efficient versions of VNC:
[http://www.tightvnc.com/](http://www.tightvnc.com/)
[http://www.uvnc.com/](http://www.uvnc.com/)

There's also [EchoVNC]("http://echovnc.sourceforge.net/fom-serve/cache/1.html"), which may help with routing problems.

I haven't used VNC for a long time, so perhaps someone can show an even newer and more efficient version.

*EDIT*
Also see [GoToMyVNC]("http://www.gotomyvnc.com/").

---

### Post by dtrot55 on 2009-08-04
Thanks...got it to work

---

### Post by bodhi.zazen on 2009-08-04
Just take care to use a strong password, VNC is easily cracked.

Better, tunnel vnc over ssh.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

---

### Post by dtrot55 on 2009-08-06
If I decide to go with Xubuntu will this all work the same?

---

### Post by Paddy Landau on 2009-08-07
> **dtrot55 said:**
> If I decide to go with Xubuntu will this all work the same?
Yes. Xubuntu uses the same kernel as Ubuntu. Only the interface and choice of certain programs differ.

---

### Post by 3rdalbum on 2009-08-07
I thought the simplest way, if you're using Ubuntu, is to go to System > Preferences > Remote Desktop and just click "Allow other users to view your desktop" and "Allow other users to control your desktop".

---

### Post by Paddy Landau on 2009-08-07
> **3rdalbum said:**
> I thought the simplest way, if you're using Ubuntu, is to go to System > Preferences > Remote Desktop and just click "Allow other users to view your desktop" and "Allow other users to control your desktop".
Forgive my ignorance... How would that allow a Windows machine to access the Ubuntu machine? AFAIK, the Windows Remote Access function would not access anything other than another Windows machine.

---

### Post by 3rdalbum on 2009-08-07
> **Paddy Landau said:**
> Forgive my ignorance... How would that allow a Windows machine to access the Ubuntu machine? AFAIK, the Windows Remote Access function would not access anything other than another Windows machine.

Hmm now that you mention it, I don't know for sure if Windows supports VNC natively (Gnome's "Remote Desktop" is just VNC anyway). You could always get a Windows VNC client.

---

### Post by Kazade on 2009-08-07
XRDP will run a Windows-style RDP server on Ubuntu - allowing you to access it using the Windows Remote Desktop client. It's in the repositories but it isn't completely stable and if it doesn't work out of the box, can be tricky to fix.

Try:

sudo apt-get install xrdp

and then try connecting from Windows.

---

### Post by snek on 2009-08-07
To everyone here, keep an eye out on [http://www.amahi.org/](http://www.amahi.org/)
This seems to be the ultimate homeserver package and they are currently working on the Ubuntu version. Currently it is only available for Fedora, but check it out.. It will fullfil almost all my wishes.

---

