---
title: "Installing Ubuntu 8.10 not"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-02-24
booting up.  I've installed this O.S. several times and the installation went very well, but when the CD comes out it goes to a black screen with a functioning cursor.  E Machine 512MB.  The system is good enough to handle it, no internet connection, was running XP Home, lots of bugs.  I wiped the HD using Acronis  and used the CD I always use for this installation. The first installation didn't work, so I wiped the HD again and reinstalled ubuntu 8.10 with the same result.

---

### Post by pickarooney on 2009-02-24
functioning cursor? Is it a prompt after which you can type commands or just a blinking line on an empty screen?

---

### Post by Yed Ied on 2009-02-24
Black screen with just the cursor, arrow, pointer, no line or anything, but you can move the pointer as in normal operation.

---

### Post by pickarooney on 2009-02-25
Try hitting Ctrl-Alt-F1, Ctrl-Alt-F2.... until you get a prompt. If you manage to get that far you'll probably just need to configure your graphics card. 

**sudo apt-get install envyng-core**

then run **envy** and follow the on-screen instructions.

---

### Post by swoll1980 on 2009-02-25
try the text mode installer, or if you have a partitioner laying around add a swap to your drive that could help.

---

### Post by HittingSmoke on 2009-02-25
> **Yed Ied said:**
> booting up.  I've installed this O.S. several times and the installation went very well, but when the CD comes out it goes to a black screen with a functioning cursor.  E Machine 512MB.  The system is good enough to handle it, no internet connection, was running XP Home, lots of bugs.  I wiped the HD using Acronis  and used the CD I always use for this installation. The first installation didn't work, so I wiped the HD again and reinstalled ubuntu 8.10 with the same result.

What graphics card are you using? I had a similar problem lately installing Kubuntu Intrepid. These instructions solved my problem for an **Nvidia** card. If you're using Nvidia it couldnt hurt to try this.

Press Ctrl+Alt+F1

type
```
/etc/init.d/gdm stop
```
Then
```
sudo apt-get install nvidia-glx-177
```
Then
```
sudo reboot
```

And see if that boots you into Gnome properly. I'm not sure how this works for non-Nvidia cards but I'm sure there's a way.

---

