---
title: "ejecting of cdrom"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by liedan on 2010-01-03
Hi guys. I really need your quick help:)
Simple silly question. How do I force cdrom to eject? 
I am installing a longman dictionary through wine and now i am at the stage when i need to insert CD2. However, linux won`t let me, since wine is using it.:(

---

### Post by LowSky on 2010-01-03
there a 'glitch' with Karmic, go through the file sytem (nautilus) and unmount from there

---

### Post by liedan on 2010-01-03
> **LowSky said:**
> there a 'glitch' with Karmic, go through the file sytem (nautilus) and unmount from there

Well, i am not sure if i am doing it right but it is not helping.
Through nautilus, i enter filesystem -->media then right click on cdrom0 and unmount but it is still complaining.

Isn` t there any simple command which i could run from terminal??

---

### Post by @B6Mwu8fN9M on 2010-01-03
There was another thread about this before: [http://ubuntuforums.org/showthread.php?t=242999](http://ubuntuforums.org/showthread.php?t=242999)

@wenuswilson says
> wine eject d:

Replace "d:" with whatever drive letter Wine assigns to your CD drive.

---

### Post by liedan on 2010-01-03
> **vlad003 said:**
> There was another thread about this before: [http://ubuntuforums.org/showthread.php?t=242999](http://ubuntuforums.org/showthread.php?t=242999)

@wenuswilson says

Replace "d:" with whatever drive letter Wine assigns to your CD drive.

Thanks, but again, not working for me for some reason. I got this:
```
wine eject
No CD drive found

```
or
```
wine eject d:
Drive d: is not a CD or is not mounted

```

Now I cant even stop the installation, which is not nice:( I`ll probably have to kill it.

---

### Post by tgalati4 on 2010-01-03
You could try it from the terminal:

sudo eject /dev/cdrom

---

### Post by liedan on 2010-01-03
> **tgalati4 said:**
> You could try it from the terminal:

sudo eject /dev/cdrom

Already tried. Not working, device is busy:(

---

### Post by @B6Mwu8fN9M on 2010-01-03
Read [http://ubuntuforums.org/showthread.php?t=242999](http://ubuntuforums.org/showthread.php?t=242999)

The person there seems to have the same problem. Try out the sugestions there.

---

### Post by liedan on 2010-01-03
> **vlad003 said:**
> Read [http://ubuntuforums.org/showthread.php?t=242999](http://ubuntuforums.org/showthread.php?t=242999)

The person there seems to have the same problem. Try out the sugestions there.
Alright, thanks. Don`t have time now, I will try tomorrow.
Good night:)

---

### Post by llamabr on 2010-01-03
> **liedan said:**
> Already tried. Not working, device is busy:(

If it's busy, it's likely because you're in the directory, either with an open app, or more likely, in a terminal.

---

