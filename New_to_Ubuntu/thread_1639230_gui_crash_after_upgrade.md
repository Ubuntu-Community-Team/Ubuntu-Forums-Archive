---
title: "gui crash after upgrade"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by what_vale on 2010-12-06
Hi,

I recently upgraded from 10.4 to 10.10 and most of the time everuthing ran OK for a week then gnome crashed and will only run on the command line. I think it maybe something to do with x.org but I get fatal server error. I have heard that 10.4 to 10.10 was not a good thing to do. Unfortunately I only heard this after the crash. Is there anyway of solving this without a fresh install as I have family photos I forgot to backup.

I tried running failsafe low-graphics mode but got the following:
screen, graphics card, input device settings could not be detected correctly followed by screen(s) found, but none have a usable configuration.

I have tried running an older version on live CD but I am not allowed access to some areas. One being where the photos are (Message: You do not have permission to read it). Am I able to change to root to get access while using the live CD? I need to copy them over to either a flash drive or an external drive using a usb port but from the command line I don't know how to get them working as when they are plugged in I cannot see them. I have been told they should show up in /media but all I get is cdrom and cdrom0.

Can anyone help me get the photos off the PC so I can re-install or help me fix the gnome problem.

Thank you

---

### Post by Hippytaff on 2010-12-06
You could try reinstalling ubuntu-desktop
```

sudo apt-get remove ubuntu-desktop && sudo apt-get install ubuntu-desktop

```or you might need to reinstall the x server
re the usb, you might need to manually mount it. When it's plugged in can you see it with
```

lsusb

```and what is the output of 
```

mount

```

---

### Post by sikander3786 on 2010-12-06
Welcome to the forums :-)

> I tried running failsafe low-graphics mode but got the following:
screen, graphics card, input device settings could not be detected correctly followed by screen(s) found, but none have a usable configuration.

After reading that, I would suggest to try and reconfigure your graphics from command line.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

> I have tried running an older version on live CD but I am not allowed access to some areas. One being where the photos are (Message: You do not have permission to read it). Am I able to change to root to get access while using the live CD? 

You need to run Nautilus as super user from Live CD to gain root previleges.

```
gksudo nautilus
```

---

