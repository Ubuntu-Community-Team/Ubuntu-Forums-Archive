---
title: "Ubuntu Server Graphical Remote Connection"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by akkad on 2009-04-20
i like the idea of ubuntu server being with no GUI, but am wondering if a graphical remote connection from another machine is possible, is there such feature in ubuntu server?

---

### Post by Cypher on 2009-04-20
You can always use VNC with your server. At work, I have a Linux machine that I use exclusely remotely since I have to use my XP laptop as well. The Linux machine is running Kubuntu and is the desktop version, but KDM is disabled and on boot-up it just gets to a regular text login prompt just like the Server edition.

I login through SSH into the server as my username and run a script that executes:
```

DISPNUM=2

tightvncserver :$DISPNUM -depth 24 -name Orion -nevershared -geometry 1500x950 &

```
I've setup a password for tightvncserver using **tightvncpasswd**, so when I connect to my machine "Orion" on display #2 using, Orion:2, I get prompted for the password and then I'm taken to the full KDE desktop.

I used KDE because back in the Fesity/Hardy days, the Gnome desktop had an issue with being used in this manner in that the keyboard mapping was getting messed up. KDE was immune to this issue, not sure if the newer versions of Gnome have resolved this issue.

So on your server, install the ubuntu-desktop or kubuntu-desktop packages, but disable GDM or KDM appropriately and you're all set..

---

### Post by lykwydchykyn on 2009-04-20
I usually just forward graphical apps through SSH rather than bringing up a whole desktop, but sometimes I use freenx.  It was a little tricky to install and setup, but if you don't need more than 2 concurrent connections you can use the proprietary nxserver from nomachine.

---

### Post by Malalo on 2009-04-20
Well your server must have an Xserver installed on it, or else locally or remotely, you wont get any GUI from the server. If it has an Xserver, running or not, you can connect through SSH to access graphical commands (for example, Nautilus) with this command :

```
ssh -X -Y user@remote_server /usrbin/nautilus
```

---

### Post by Cypher on 2009-04-20
> **Malalo said:**
> Well your server must have an Xserver installed on it, or else locally or remotely, you wont get any GUI from the server. If it has an Xserver, running or not, you can connect through SSH to access graphical commands (for example, Nautilus) with this command :

```
ssh -X -Y user@remote_server /usrbin/nautilus
```
The idea of the Server version of Ubuntu is that it is missing the X components entirely..:)

---

### Post by lykwydchykyn on 2009-04-20
> **Malalo said:**
> Well your server must have an Xserver installed on it, or else locally or remotely, you wont get any GUI from the server. If it has an Xserver, running or not, you can connect through SSH to access graphical commands (for example, Nautilus) with this command :

```
ssh -X -Y user@remote_server /usrbin/nautilus
```

You do not need an X server installed on the server to forward X11 over ssh.  You need an Xserver running on the CLIENT, which means you either need to be running Linux on your client, or have installed an X11 server for Windows/OSX (whatever you're running).

---

### Post by ugm6hr on 2009-04-20
If you want a web GUI, ebox or webmin are worth looking at.

I have tried the former, which seems pretty good, as long as you use their repo for Hardy (Intrepid less good), or just use their Live CD to install.

---

