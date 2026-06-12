---
title: "Xorg.conf"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Goldline on 2009-12-02
Could someone pass along the original xorg.conf file
which can be found in: etc/x11/xorg.conf. Screwed up the 3d settings 
and now my only option is to login through a shell. But if someone passes 
me the file then i can log onto windows vista and replace the file on my 
linux ext4 partition.

---

### Post by coffeecat on 2009-12-02
It's even easier in Karmic, 9.10. There **is** no xorg.conf file by default. Simply rename your xorg.conf to xorg.conf.backup and reboot. Then the system will use whatever open source graphics driver is appropriate and you can start over.

---

### Post by Goldline on 2009-12-02
Okay right but im total noob how can i rename that specific file through the console.

---

### Post by coffeecat on 2009-12-02
My apologies. I forgot this was the beginners forum.

Login to the shell and then:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```You'll be prompted for your password. It doesn't appear to be going in when you type it, but it is, and the command will be done when you press ENTER.

Renaming the file is better than deleting it, because you can still view it if you want to try again with different options.

By the way - you would have had difficulty reading an ext4 partition from Vista. :wink:

**Edit:** take care with your capitals and lower-case - Linux is case-sensitive, unlike Windows. It's /etc/**X**11/**x**org.conf

---

### Post by QIII on 2009-12-02
> **coffeecat said:**
> By the way - you would have had difficulty reading an ext4 partition from Vista. :wink:

Without some work before hand (it can be done, apparently), Vista would wet its pants and run away in terror...

---

