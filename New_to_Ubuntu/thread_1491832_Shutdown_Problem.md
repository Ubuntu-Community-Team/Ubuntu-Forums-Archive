---
title: "Shutdown Problem"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by djmac on 2010-05-24
I am having problems shutting down my computer. The screen just hangs on the maroon/pink/purple ubuntu splash screen, (with two out of the three dots coloured red, if that is any use!)

Does the same for:
```
sudo shutdown now
```

I have recently upgraded to 10.04 (about a week ago?), however the problem only just started occuring (i.e. since yesterday).

Thankyou.

---

### Post by da burger on 2010-05-24
Try:```
sudo shutdown now -P
``` that tells it to power off and not just stop the operating system.

---

### Post by djmac on 2010-05-24
> ```
sudo shutdown now -P
```

This did work. However, it is kind of annoying to do that every time I want to shutdown the computer (as opposed to the normal/graphical way).

 Also, can I restart the computer using this it all??

---

### Post by schtufbox on 2010-05-24
You can do a reboot with..


sudo reboot

---

### Post by da burger on 2010-05-24
This will remove the extra options but as an interim solution try the following. Right click on a panel and select add to panel. Select custom application launcher. For name, picture and comment put what you want and for command put ```
gksudo shutdown -P
```

You will still have to enter you password but as I say this should only be a temporary solution until someone more experienced gives you a better one. 

As well as the method posted above you can change -P to -r to make it reboot. For a full list see ```
man shutdown
```

---

### Post by djmac on 2010-05-25
I am familiar with using:

```
sudo shutnow now -r
```

I use it a bit actually.

The problem is, if I use -r, I cannot use -P, and the computer doesn't shutdown properly (and therefore doesn't restart). That is, it does the same as before (hangs on the splash screen).

---

### Post by arrange on 2010-05-25
Does```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```shut down the computer or produce any output?

Is the situation the same when you boot into an older kernel (if you have one)?

---

### Post by sbergman on 2010-05-25
> **djmac said:**
> (as opposed to the normal/graphical way)....

Somewhere on your screen, mine's on the top right, you'll see your Username. If you click on it, you'll get the options for restarting, shutdown etc. Is that what you mean by "as opposed to the graphical way" ?

---

### Post by philinux on 2010-05-25
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/576204)

See the last comment first. And there's an error in the fix post #9 gedit should be used with gksudo

```
gksudo gedit filename
```

---

