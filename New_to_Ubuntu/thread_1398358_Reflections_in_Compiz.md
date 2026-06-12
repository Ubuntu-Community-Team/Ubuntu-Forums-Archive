---
title: "Reflections in Compiz"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by jbird999 on 2010-02-04
I enabled Reflections in CCSM on my Laptop and Ubuntu froze. I restarted and could only manage to get into the login page but when I login it freezes. So I booted up recovery mode and got up the root prompt and typed in;
 
rm -r /home/username/.compiz
 
To remove compiz settings, obviously replacing username with my username and all I got was "no such file or directory."
 
Is there another way to remove compiz settings?
 
Thank you.

---

### Post by skymera on 2010-02-04
i can confirm mine is

/home/scott/.compiz/

Purge Compiz, it will remove the configuration files, then reinstall?

```
 sudo aptitude purge compiz compizconfig-settings-manager 
```

---

### Post by jbird999 on 2010-02-04
> **skymera said:**
> i can confirm mine is
 
/home/scott/.compiz/
 
Purge Compiz, it will remove the configuration files, then reinstall?
 
```
 sudo aptitude purge compiz compizconfig-settings-manager 
```
 
It ran but Ubuntu still freezes

---

### Post by jbird999 on 2010-02-04
I must be doing something wrong with the above advice, I ran the sudo command, I turned the power off with the power button, I don't know if there is a command to restart in shell, started up Ubuntu, logged in and it froze.

---

### Post by verachion on 2010-02-04
> **jbird999 said:**
> I must be doing something wrong with the above advice, I ran the sudo command, I turned the power off with the power button, I don't know if there is a command to restart in shell, started up Ubuntu, logged in and it froze.

I am a newbie too I don't know if this will help you but you can access shell with networking or just shell, in the repair boot option 2 (I am running 9.10 ubuntu)

---

### Post by jbird999 on 2010-02-04
found the solution, wasn't searching for the right keywords, here it is if anyone is interested
 
[http://ubuntuforums.org/showthread.php?t=1394007&highlight=compiz+reflection](http://ubuntuforums.org/showthread.php?t=1394007&highlight=compiz+reflection)

---

