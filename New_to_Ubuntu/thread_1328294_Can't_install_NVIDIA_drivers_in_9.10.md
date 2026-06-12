---
title: "Can't install NVIDIA drivers in 9.10"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by Indigo340 on 2009-11-16
I am using UBUNTU 9.10 on a SONY VAIO laptop with a GEForce GO 7400

I am having trouble installing NVIDIA drivers (NVIDIA-LINUX-x86-190.42-pkg1.run) which I have saved to desktop. 

The problem is when I enter the line in brackets, I get an error message saying 'command not recognised'. 

I have been following the instructions here
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I am obviously missing something, can anyone please advise ?

I am a complete noobie so simple language please

---

### Post by realzippy on 2009-11-16
Have you typed:

sudo sh NVIDIA-LINUX-x86-190.42-pkg1.run

(no brackets)

---

### Post by philinux on 2009-11-16
> **Indigo340 said:**
> I am using UBUNTU 9.10 on a SONY VAIO laptop with a GEForce GO 7400

I am having trouble installing NVIDIA drivers (NVIDIA-LINUX-x86-190.42-pkg1.run) which I have saved to desktop. 

The problem is when I enter the line in brackets, I get an error message saying 'command not recognised'. 

I have been following the instructions here
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I am obviously missing something, can anyone please advise ?

I am a complete noobie so simple language please

It's much easier to use system>admin>hardware Drivers. If you really need the latest then installing by hand will do it. However when there is a new kernel you'll have to do it by hand each time.

---

### Post by ukripper on 2009-11-16
As philinux suggested. The best way to do it is through Hardware drivers.

---

### Post by -=hazard=- on 2009-11-16
Well I just went here [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) and yes its explained howto but I dont see the part where that guy must explain that for newest nvidia drivers you must install kernel headers too. Anyway I agree with the other guys here that the best way is from Ubuntu repo' by installing the recomended drivers. I use Nvidia too and belive me there is not such a big differences with the new drivers suggested by Nvidia, at least in general.

---

### Post by Indigo340 on 2009-11-16
OOOPSS done it again, ha ha ha figured it out on my own ha ha ha ! 

I'm really getting to like this new system and getting closer to deleting the Windows partition for good !

Thanks for your advice guys, you are right that is the easiest way, guess I was just thinking too hard !

---

### Post by -=hazard=- on 2009-11-16
> **Indigo340 said:**
> OOOPSS done it again, ha ha ha figured it out on my own ha ha ha ! 
 
I'm really getting to like this new system and getting closer to deleting the Windows partition for good !
 
Thanks for your advice guys, you are right that is the easiest way, guess I was just thinking too hard !
 
 
Ah so, if you are new in linux then to install nvidia drivers do like this:
 
Go here: System > Administration > Hardware Drivers
On the window that will open select the driver that says [COLOR=red]Recomended[/COLOR] and then click on [COLOR=red]Activate. [/COLOR][COLOR=black]Then just wait drivers downloading and installing. After install is finished just reboot your pc and everything would be fine.[/COLOR]

---

### Post by philinux on 2009-11-16
> **Indigo340 said:**
> OOOPSS done it again, ha ha ha figured it out on my own ha ha ha ! 

I'm really getting to like this new system and getting closer to deleting the Windows partition for good !

Thanks for your advice guys, you are right that is the easiest way, guess I was just thinking too hard !

+1. ;)

It's probably best to ask on here before making things too hard. Or borking your nice new install.

---

