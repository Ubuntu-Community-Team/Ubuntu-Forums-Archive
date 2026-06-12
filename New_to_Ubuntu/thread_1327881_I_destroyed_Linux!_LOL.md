---
title: "I destroyed Linux! LOL"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-15
I was trying to fix a bug and did 'aptitude remove dbus' and then I was going to install it after it uninstalled. Now that didn't go so well as you might imagine!

Since I don't know what dbus is or what Im doing I just woke up to a world of hurt! LOL!
Well this is good learning, I had a LOT setup but I really want to figure out how this stuff works. 

I personally prefer to use the Terminal, but I better be careful.

So for future learning, if I remove something like that is there a way to get it back? Because I once I was in the 'full-screen, non-GUI terminal' I couldn't access the internet so I figured I was out of luck. (No ethernet cable either).

---

### Post by Meskarune on 2009-11-15
This might be of some help. I would suggest learning how to restore backups via command line on top of the GUI version. This way if things get messed up, you have a way to restore them. 

[http://backintime.le-web.org/](http://backintime.le-web.org/)

---

### Post by sandyd on 2009-11-15
> **JREAM said:**
> I was trying to fix a bug and did 'aptitude remove dbus' and then I was going to install it after it uninstalled. Now that didn't go so well as you might imagine!

Since I don't know what dbus is or what Im doing I just woke up to a world of hurt! LOL!
Well this is good learning, I had a LOT setup but I really want to figure out how this stuff works. 

I personally prefer to use the Terminal, but I better be careful.

So for future learning, if I remove something like that is there a way to get it back? Because I once I was in the 'full-screen, non-GUI terminal' I couldn't access the internet so I figured I was out of luck. (No ethernet cable either).
grab dbus of another computer (download links below)

32 bit : 
```

http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.2.16-0ubuntu9_i386.deb
http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.2.16-0ubuntu9_i386.deb

```
64 bit: [http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.60-6ubuntu8.4_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_0.60-6ubuntu8.4_amd64.deb)
[/code]
p.s. too lazy to list all of them. their all here
[http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/](http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/)
copy onto cd and bring it over to the computer
```

sudo mount /dev/cdrom0
cd /media/cdrom*
sudo dpkg -i *.deb

```

---

