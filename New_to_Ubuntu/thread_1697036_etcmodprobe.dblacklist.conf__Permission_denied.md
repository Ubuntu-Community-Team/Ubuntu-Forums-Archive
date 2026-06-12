---
title: "/etc/modprobe.d/blacklist.conf : Permission denied"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by NationUpNorth on 2011-02-28
I'm trying to install an Nvidia driver and I can't go any further unless I blacklist the Nouveau kernel. Trying to do so gives me *permission denied*, and I am already logged in as root. 

I found a different command somewhere on the net, but that didn't help. Something about gksudo gedit /etc/modprobe.d/blacklist.conf. It says GTK-WARNING cannot open display.

---

### Post by seawolf167 on 2011-02-28
gksudo opens a graphical version of whatever you are calling as the super user

i.e. 

```
gksudo gedit
```

opens gedit as the super user

you'll want to use sudo instead for staying inside a terminal

```
sudo *<command>*
```

---

### Post by philinux on 2011-02-28
> **NationUpNorth said:**
> I'm trying to install an Nvidia driver and I can't go any further unless I blacklist the Nouveau kernel. Trying to do so gives me *permission denied*, and I am already logged in as root. 

I found a different command somewhere on the net, but that didn't help. Something about gksudo gedit /etc/modprobe.d/blacklist.conf. It says GTK-WARNING cannot open display.

try

```
sudo nano  /etc/modprobe.d/blacklist.conf
```

---

### Post by NationUpNorth on 2011-02-28
Okay great.

> you'll want to use sudo instead for staying inside a terminal
But If I'm already logged in as root it's no need to write sudo, right? If I understand you correctly, that is.

> sudo nano  /etc/modprobe.d/blacklist.conf
Isn't nano a text editor? I'll have to go apt-get install nano first?

I will try this when I get the chance. Thank you.

---

### Post by philinux on 2011-02-28
> **NationUpNorth said:**
> Okay great.

But If I'm already logged in as root it's no need to write sudo, right? If I understand you correctly, that is.


Isn't nano a text editor? I'll have to go apt-get install nano first?

I will try this when I get the chance. Thank you.

nano and gedit are both text editors. nano is installed by default.

nano is a terminal based text editor gedit is a gui text editor.

---

### Post by seawolf167 on 2011-02-28
If you are already logged in as root then sudo and gksudo won't change anything.

Though, you should never log in as root, only as a normal user, then use sudo or gksudo to preform admin tasks

nano is a text editor, you can just as easily use vi, gedit, etc.

```
sudo vi *<filename here>*
gksudo *<filename here>*
```

---

### Post by NationUpNorth on 2011-02-28
Okay that helped. I got into the list and wrote; 

> blacklist nouveau

at the bottom, but it doesn't seem to help. It tells me the Nouveau kernel is still in use by the system.

---

### Post by sandyd on 2011-02-28
> **NationUpNorth said:**
> Okay that helped. I got into the list and wrote; 



at the bottom, but it doesn't seem to help. It tells me the Nouveau kernel is still in use by the system.
you have to restart.
for instant effect.
```

sudo rmmod nouveau
```

---

### Post by deconstrained on 2011-02-28
> **NationUpNorth said:**
> I found a different command somewhere on the net, but that didn't help. Something about gksudo gedit /etc/modprobe.d/blacklist.conf. It says GTK-WARNING cannot open display.
FFR: It's not working because root is not permitted to use X11. Do gksudo as yourself (your own user account) instead of root and it should then work; it will open a dialogue for entering your password and then start up a gedit session with superuser permissions.

---

### Post by NationUpNorth on 2011-03-01
> **sandyd said:**
> you have to restart.
for instant effect.
```

sudo rmmod nouveau
```

I did a reboot after adding the line. For one because I read I had to do it, and because I wanted to make sure I saved it. So after the reboot I went back in to see I had succesfully added it. What does rmmod nouveau do compared to a reboot of the whole machine?

>  	Quote:
 	 	 		 			 				 					Originally Posted by **NationUpNorth** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10504563#post10504563") 				
 				*I found a different command  somewhere on the net, but that didn't help. Something about gksudo gedit  /etc/modprobe.d/blacklist.conf. It says GTK-WARNING cannot open  display.*
 			 		 	 	 
FFR: It's not working because root is not permitted to use X11. Do  gksudo as yourself (your own user account) instead of root and it  should then work; it will open a dialogue for entering your password and  then start up a gedit session with superuser permissions. 	

Mmh, but doesn't root mean you have access to everything? Also as written above the gk command will open a graphical view, so that wouldn't be possible since I've closed down the gdm? 

Or am I confused?

---

### Post by NationUpNorth on 2011-03-01
I did the rmmod nouveau and it actually worked. It told me the nouveau kernel was not active, and then I went ahead and installed the driver. That was so much fun to finally see it happen.

Anyway, I didn't actually expect it to work. I tried the driver recommended by the ubuntu developers, but that didn't work. It just booted in the terminal. Disabling the driver made Ubuntu work just fine, however I wanted to try Nvidia's own. Now It just won't even boot. All I see is the Ubuntu purple screen and the dots loading.... And then it stops... 

I'll have to reboot in recovery mode and somehow remove the driver. I did make a backup of an important file. I will have to recover that. I got it on a sheet at home, and I'll tell you what file it was I made a backup of and maybe you can help me again.

---

### Post by deconstrained on 2011-03-02
> **NationUpNorth said:**
> Mmh, but doesn't root mean you have access to everything?
Root can modify any part of the system or run any program, but for security purposes, certain services like xorg and ssh are by default configured to not allow *access through them* as root, which is an entirely different matter.

It's generally a good idea to limit the *ways* in which the superuser can access the system, because each way in as root is a potential security hole. Once the system is accessed, regardless of what service or protocol is used in the breach, anything is possible to an attacker.

---

### Post by beew on 2011-03-02
I used additional driver to install my nvidia driver and then updated it with the xswat ppa, there is no need to remove the nouveau driver (but I could remove it and its related stuffs). It works great.

If you install the driver by downloading from Nvidia you will have to reinstall it each time you upgrade the kernel (that's what I read, never did that though) I don't think it is worth the trouble.

---

