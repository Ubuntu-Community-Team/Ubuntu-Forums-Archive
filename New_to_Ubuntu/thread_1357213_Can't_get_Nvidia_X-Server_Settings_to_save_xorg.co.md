---
title: "Can't get Nvidia X-Server Settings to save xorg.conf"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Sugi on 2009-12-17
I can't get a Nvidia X-Server Setitng to show me the xorg.conf settings for my current display setup or save it.  How do I get this to work?

PS: When I try to apply the current set-up to my  xorg.conf.  I get this message:
Failed to parse existing X config file '/etc/X11/xorg.conf'!

Spec:
Ubuntu 9.10 64bit
Dual-Monitor Setup
Nvidia GTX 260
Nvidia Driver 185.18.36

Thanks,
Sugi

---

### Post by staf0048 on 2009-12-17
Yeah, I get that problem too.  You have to run it as root for it to save properly.  

I don't remember the command for the nVidia x-server, but if you check out Preferences/Main Menu, find the program and click properties it will give you the correct command.

---

### Post by Sugi on 2009-12-17
sudo nvidia-settings

There it is.  Why don't ubuntu change it, so when you try to save it just ask you for your password.  Sigh.

PS:  This has been an issue with nvidia settings for the past couple of updates, if not since they started including nvidia settings for ubuntu.

Thanks for the tip,
Sugi



UPDATE:
Actually, I lied.  I still can't get it to save to the xorg.conf with sudo nvidia-settings.  Any clue now?

---

### Post by bhaverkamp on 2009-12-17
You could also just change the permission on xorg.conf

---

### Post by Sugi on 2009-12-17
Changing the premission on xorg.conf is doesn't work. :(

This is kinda bumming me out.

Sugi

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
Try to move the xorg.conf to a backup file first
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
Then run gksudo nvidia -settings

---

### Post by lexfati on 2009-12-17
I had a problem like this when I was getting set up.

I remember nvidia-settings having trouble saving an xorg.conf if there was already an xorg.conf present, so I renamed my file to a backup:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

and then I ran nvidia-settings again with gksudo (gksudo gives superuser privilege like sudo, but it is to be used with graphical programs, like nvidia-settings (unless you use KDE, then there is a different command).

```
gksudo nvidia-settings
```

---

### Post by lexfati on 2009-12-17
Looks like ST3ALTHPSYCH0 beat me.  Took me too long to type it up.

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
Ya win some, ya lose some.... at least that confirms what I was thinking... I am a n00b after all!

---

### Post by Sugi on 2009-12-17
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

That kinda worked for me after running nvidia-settings.

I still wasn't able to save to xrog.conf even with gksudo nvidia-settings, BUT I was able to see the preview and then just save it manually.

Thanks guys,
Sugi

---

### Post by Elfy on 2009-12-17
First thing I do after I have installed nvidia is change the command in the menu to include gksudo then it runs properly.

---

### Post by Linuxforall on 2009-12-17
After installing driver, gksudo nvidia-xconfig then gksudo nvidia-settings

Select your resolution and save to X.

---

### Post by Sugi on 2009-12-17
> **forestpiskie said:**
> First thing I do after I have installed nvidia is change the command in the menu to include gksudo then it runs properly.

Nope, I tried that.  Didn't work for me.

Sugi

---

### Post by ST3ALTHPSYCH0 on 2009-12-17
I forgot about just cutting and pasting the xorg they generate. That is what I had to do (even though it still didn't allow me greater than 800x600).

---

