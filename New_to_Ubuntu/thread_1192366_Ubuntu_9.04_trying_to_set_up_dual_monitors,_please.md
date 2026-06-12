---
title: "Ubuntu 9.04 trying to set up dual monitors, please HALP"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by 8trackalienoid on 2009-06-20
I have envyNG installed, Nvidia driver installed and i can get it configured the way i want but whenever i go to save the xconf it tells me something about not being able to parse it.  And whenever i restart i have to configure it all over again. 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
EndSection


Stangley this is all i see when i check out my xconfig, i dont really understand it much but i do take instruction well and am willing to learn.  I have been at this for a majority of the day pleae help. And thank you.

---

### Post by 8trackalienoid on 2009-06-20
> **8trackalienoid said:**
> I have envyNG installed, Nvidia driver installed and i can get it configured the way i want but whenever i go to save the xconf it tells me something about not being able to parse it.  And whenever i restart i have to configure it all over again. 

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
EndSection


Stangley this is all i see when i check out my xconfig, i dont really understand it much but i do take instruction well and am willing to learn.  I have been at this for a majority of the day pleae help. And thank you.

Sill looking around online. Have to leave my computer on causing reconfiguring everytime is a pain.

---

### Post by madverb on 2009-06-20
```
gksu nvidia-settings
```

Setup how you want and then save config file.

---

### Post by powel212 on 2009-06-20
you could try

```
sudo nvidia-settings
```

This way when you safe to x-config it will have sufficient rights to save the file.

Powel

---

### Post by 8trackalienoid on 2009-06-20
> **powel212 said:**
> you could try

```
sudo nvidia-settings
```

This way when you safe to x-config it will have sufficient rights to save the file.

Powel

Now its saying failed to parse exsisting X config file '/etc/X11/xorg.conf'

---

### Post by 8trackalienoid on 2009-06-20
> **madverb said:**
> ```
gksu nvidia-settings
```

Setup how you want and then save config file.
Now its saying failed to parse exsisting X config file '/etc/X11/xorg.conf'

---

### Post by powel212 on 2009-06-20
Found this thread;

[http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

Same problem and a solution.

Hope it works for you

Powel

---

### Post by 8trackalienoid on 2009-06-20
> **powel212 said:**
> Found this thread;

[http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

Same problem and a solution.

Hope it works for you

Powel
[http://ubuntuforums.org/showthread.php?t=1101445&page=2](http://ubuntuforums.org/showthread.php?t=1101445&page=2)

Had all my answers. 
Thanks all for the help!
Im a happy little penguin lover now. 



[THREAD CLOSED]

---

