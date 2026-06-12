---
title: "automating processes at startup/shut down?"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by stresslog on 2009-09-01
Hi 
I'm figuring up how to do stuff as I go (and mostly enjoying ubuntu) but there are a couple of things I'm stuck on

1. My ethernet card (atheros ar8131)wasn't supported so I downloaded the driver and set that up but it doesn't seem to activate at start up and at the moment I'm having to manually start it at login using the following:
$ sudo insmod atl1e.ko
$ ifconfig eth0 up
$ dhclient eth0

2. My laptop (Asus U81A) is refusing to shut down properly if there is an active internet connection when i shut down - It goes through the shut down processes and then instead of powering down i get a black screen with a white underscore prompt. If I close the internet connections before shut down it works perfectly. 
I have seen a couple of treads related to similar issues and people seem to be suggesting closing the internet connections manually. However I was hoping the might be a way to automate turning off the internet connections at shut down.

I'm sure there is some easy way to get these command automated but nothing I've tried so far has worked.
Any suggestions would be greatly appreciated

Laptop: Asus U81A - 64 bit
Ubuntu: Jaunty 9.04 
Kernel: Linux 2.6.28.11-generic
Gnome: 2.26.1
Dual boot: Vista (because I unfortunately need it for work)

---

### Post by matsuzine on 2009-09-01
You could add a startup script to be run when the system in loading.

Check this out for a start:

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by nothingspecial on 2009-09-01
You need to add the module to /etc/modules/

```
sudo nano /etc/modules/
```

Add the driver to the bottom of that file.

---

### Post by Paddy Landau on 2009-09-01
Also have a look at update-rc.d. Use the man command to find out more.
```
man update-rc.d
```This forum has threads explaining more about it.

---

### Post by stresslog on 2009-09-03
my net went down so I couldn't check these

I tried adding the sh to startup applications

I also tried adding it to modules 

moving it to init.d & using update-rc.d didn't work either - but I can see that it should so I'll keep playing until it behaves

thanks

---

### Post by Paddy Landau on 2009-09-03
> **stresslog said:**
> moving it to init.d & using update-rc.d didn't work either - but I can see that it should so I'll keep playing until it behaves
I'm not much experienced with these, but I do know that you have to follow the instructions precisely. I seem to remember that there are threads in this forum giving more detail; in any case, read the manual carefully.

---

