---
title: "can't figure out how to boot"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by rickandsuch on 2009-05-24
Hi all, I have a fresh install of 9.04 but after the first time shutting it down it wont reboot properly.  It runs through GRUB and stops after the ubuntu progress bar, right around the the time it should be playing the 'question' sound.  All I have is a black screen with a mouse on it.  So, I push ctrl+alt+F1 to go to the terminal, but this is where I'm stuck.  I don't know what the problem is or what to type.
thanks

---

### Post by Uzi304 on 2009-05-24
Try typing in ```
sudo startx
``` and see what happens.

---

### Post by rickandsuch on 2009-05-24
It tells me
X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
if this server is no longer running, remove /tmp/.X0-lock and start again

ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Resources temporarily unavailable (errno 11): unable to connect to xserver
xinit: No such process (errno 3): Server error

but other than that nothing happens...

---

### Post by whoop on 2009-05-24
boot in recovery mode, type
```

gksudo nano /boot/grub/menu.lst

```
remove "quiet splash" from the kernel line you are booting from. reboot. Then we have a chance of seeing what goes wrong.

---

### Post by rickandsuch on 2009-05-24
it says 
(gksudo:2202): Gtk-WARNING **: cannot open display

Did you mean to go to the root shell recovery mode from grub?

---

### Post by rickandsuch on 2009-05-24
Dang it!! I can't figure out how to get X to start! Can someone assist?

---

### Post by rickandsuch on 2009-05-24
bump

---

### Post by whoop on 2009-05-24
> **rickandsuch said:**
> it says 
(gksudo:2202): Gtk-WARNING **: cannot open display

Did you mean to go to the root shell recovery mode from grub?
Oops, sorry about that, my mistake... It should be:
```

nano /boot/grub/menu.lst

```
gksudo only works when X is running. you can use normal sudo in cli. But in this case I guess you won't need it cause you are already root when you enter recovery mode.

Yes I meant root shell recovery mode, but only to change the menu.lst, after that boot in normal mode and see if you get an error...

---

### Post by rickandsuch on 2009-05-25
> **whoop said:**
> Oops, sorry about that, my mistake... It should be:
```

nano /boot/grub/menu.lst

```
gksudo only works when X is running. you can use normal sudo in cli. But in this case I guess you won't need it cause you are already root when you enter recovery mode.


OK that clears it up a bit!  I got rid of quiet and splash, now how are you supposed to read the output?  Is there a way to capture it or scroll back through it?

---

### Post by rickandsuch on 2009-05-25
```

bump

```

---

### Post by dunbrokin on 2009-12-12
I am at this point....where do I go now? I can see the errors in my xorg.conf.....but how do I change that file?

---

### Post by running_rabbit07 on 2009-12-12
For best results, start a new thread.

---

