---
title: "Mount Authentication"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by beegary on 2009-12-14
I have recently come over from  the dark side (windoze) to Karmic.
 
I installed Ubuntu on my Netbook with a dual boot to windows XP. They are both on the same physical hard drive. also on the same hard drive I have a partition for sharing files between tthe two operationg systems.
It is formatted as NTFS.
 
When I boot Ubuntu this drive appears as a location in Nautilus.
BUT:
 
I have to type in my password every time I try to access it - It seems that the location is stored but it is not automatically mounted. How do I get Ubuntu to automatically mount this share?
 
Cheers
B

---

### Post by Ichtyandr on 2009-12-14
install ntfs-3g , it will mount ntfs automatically, it has a gui as well for setting it that way

---

### Post by beegary on 2009-12-14
Thank you for that! I'll give it a go.
I assume it will not conflict with what Karmic has been automatically using since install?

---

### Post by beegary on 2009-12-14
Warning Confused User:

I thought i would check to see if i already had ntfs-3g:
In a teminal window I type 
```
man ntfs-3g
```I get the man page
In System|Administration|Synaptic Package Manager ntfs-3g is showing as installed.
In Applications|Ubuntu Software Centre the application is there but showing as NOT installed.

How are these three installs related? Is the one in the software centre the GUI? Or is it more complicated than that?

---

### Post by synapsys on 2009-12-14
Here's a nice tutorial from psychocats that should help you. (not the only way, but probably the easiest)

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by beegary on 2009-12-15
Thanks Synapsys
I find all the documentation everywhere very sueful but it is very hard for a newb to trawl through.
 
anyone have an answer to this one:
>  
I get the man page
In System|Administration|Synaptic Package Manager ntfs-3g is showing as installed.
In Applications|Ubuntu Software Centre the application is there but showing as NOT installed.

How are these three installs related? Is the one in the software centre the GUI? Or is it more complicated than that?


---

### Post by mc4man on 2009-12-15
The app you're looking to use is ntfs-config, not ntfs-3g

```
sudo apt-get install ntfs-config
```

Then follow the linked guide or [here]("http://ubuntuforums.org/showthread.php?t=785263")

---

### Post by synapsys on 2009-12-15
> **mc4man said:**
> The app you're looking to use is ntfs-config, not ntfs-3g

```
sudo apt-get install ntfs-config
```Then follow the linked guide or [here]("http://ubuntuforums.org/showthread.php?t=785263")

Think of ntfs-3g as a 'driver' that makes it possible to access ntfs partitions. Think of ntfs-config as an application that tells your partitions to mount using ntfs-3g.

---

### Post by beegary on 2009-12-15
Thank you guys, I couldnt install the ntfs configuration tool via Ubuntu software centre, as stated in the original solution. I got an error: requires installation of untrusted packages: ntfs-config.
I then installed from terminal and have a fully functioning automount! Perfect.

After all that im now contemplating getting rid of my windoze boot anyway!

---

