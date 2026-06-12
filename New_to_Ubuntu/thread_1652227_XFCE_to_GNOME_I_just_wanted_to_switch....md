---
title: "XFCE to GNOME: I just wanted to switch..."
date: 2010-12-24
forum: New to Ubuntu
---

### Post by Nebelhom on 2010-12-24
Hi guys,

right, all I wanted to do was switch from xfce to gnome since I realised that it doesn't quite float my boat.

So I tried installing gnome ubuntu desktop with

```
sudo apt-get install ubuntu-desktop
```

according to [this thread]("http://ubuntuforums.org/showthread.php?t=350262"). To the best of my knowledge, there were no error messages and it installed fine.

unfortunately, now when I am booting up my laptop a bunch of IOerrors are shown in rapid succession and xfce is started afterwards. when I would like to start gdm from the terminal (not sure if this is a good idea), I get the following error message:

```
nebelhom@nebelhom-laptop:~$ gdm

** (gdm-binary:1773): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.53" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:1773): WARNING **: Could not acquire name; bailing out
```

Since I actually wanted to only install Gnome GUI and not all applications (didn't realise that it would install those as well. A schoolboy error, I guess), I would like to know how to best get rid of the ubuntu-desktop and also I would be grateful to know why I am not able to start the GNOME GUI. Can anyone of you guys help me out with this?

Thanks a lot and Merry Christmas.

Nebelhom

---

### Post by arochester on 2010-12-24
To start Gnome. On the page where you sign in. Where you put your username and password. It gives you the Option for "Session Type". Just use Gnome. You might have to "Log Out" to get to it.

You can get rid of Gnome by following:  [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by Nebelhom on 2010-12-27
@arochester: Thanks a lot for helping me out. This solved all my problems.

---

