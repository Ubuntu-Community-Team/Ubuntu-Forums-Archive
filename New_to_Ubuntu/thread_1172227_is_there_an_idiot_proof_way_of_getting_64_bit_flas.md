---
title: "is there an idiot proof way of getting 64 bit flash?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by w.g.hanna on 2009-05-28
i just installed jaunty - for the second time.  the first time i did a full install and got flash to work by:

1.  downloading the compressed folder from adobe
2.  extracting it to my desktop
3.  copying and pasting it in the mozzilla plugin folder

very easy, and it worked. 

then i tried to create a seperate home partition and broke everything - so i did a fresh install, and created the seperate home partition with the live cd.

so i try to repeat the above process and i get an error.  apparantly, i have to be logged in as root to change the permissions of the system folders or to copy and paste things in them.  so i log out and try to log bac in as root, but it tells me that i can't log in as root from that screen (without telling me how to do it).  

another thing i tried was to use the live cd and mount the two partitions - then i tried to do the copy and paste thing again with the same result:  i lack permission and lack the authority to change the permissions.

---

### Post by philinux on 2009-05-28
Just install it from synaptic.

Or this.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract the libflashplayer.so, create a folder in .mozilla called plugins, copy this file into the plugins folder. Restart firefox.

---

### Post by jokerejoker on 2009-05-28
click this link [apt://flashplugin-nonfree]("apt://flashplugin-nonfree")

---

### Post by regala on 2009-05-28
> apparantly, i have to be logged in as root to change the permissions of the system folders or to copy and paste things in them.  so i log out and try to log bac in as root, but it tells me that i can't log in as root from that screen (without telling me how to do it).

no, not apparently, it has always been. you just forgot to use sudo like the first time ("having to be logged as root" doesn't mean "having root type his password" -- which doesn't exist by the way -- but "being root", which is what sudo is for)

br, mathieu

---

### Post by XCan on 2009-05-28
IIRC the one in synaptics is 32bit and runs through nspluginwrapper. To summarize it, it SUCKS on a 64bit system.

---

### Post by zika on 2009-05-28
> **w.g.hanna said:**
> i just installed jaunty - for the second time.  the first time i did a full install and got flash to work by:

1.  downloading the compressed folder from adobe
2.  extracting it to my desktop
3.  copying and pasting it in the mozzilla plugin folder

very easy, and it worked. 

then i tried to create a seperate home partition and broke everything - so i did a fresh install, and created the seperate home partition with the live cd.

so i try to repeat the above process and i get an error.  apparantly, i have to be logged in as root to change the permissions of the system folders or to copy and paste things in them.  so i log out and try to log bac in as root, but it tells me that i can't log in as root from that screen (without telling me how to do it).  

another thing i tried was to use the live cd and mount the two partitions - then i tried to do the copy and paste thing again with the same result:  i lack permission and lack the authority to change the permissions.
try [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964) ...

---

### Post by LowSky on 2009-05-28
> **XCan said:**
> IIRC the one in synaptics is 32bit and runs through nspluginwrapper. To summarize it, it SUCKS on a 64bit system.

are you sure? even in 9.04?

---

### Post by zika on 2009-05-28
> **LowSky said:**
> are you sure? even in 9.04?
I, sadly, think yes. I'm not sure, but I recall that I had to un-install it and install it alternative way.

---

### Post by XCan on 2009-05-28
> **LowSky said:**
> are you sure? even in 9.04?

Unfortunately, yes. :( I had all kinds of random problems with it until I got the 64bit from adobe labs.

---

### Post by pme 72 on 2009-05-28
If all else fails head over to the x86 64-bit Users Forum. There are numerous posts on this topic.

---

### Post by Dougie187 on 2009-05-28
> **pme 72 said:**
> If all else fails head over to the x86 64-bit Users Forum. There are numerous posts on this topic.

Even a sticky detailing how to do it. It is very easy. The 32-bit one works fine. It's just not as high quality as the native 64-bit one. But the native one isn't hard to install either, you just can't use synaptic. Because it is still in alpha.

---

### Post by Paqman on 2009-05-28
> **Dougie187 said:**
> The 32-bit one works fine.

+1

I've never really had any trouble with it, tbh. I did switch to the 64-bit one from Adobe on Intrepid, but i'm just using the one from the repos on Jaunty and it's fine.

---

### Post by w.g.hanna on 2009-05-30
> **jokerejoker said:**
> click this link [apt://flashplugin-nonfree]("apt://flashplugin-nonfree")


worked - and totally idiot proof.  at any rate, i paradoxically found the 64 bit version worked slower and i switched back.

---

### Post by WatchingThePain on 2009-05-31
This worked for me.

Plugins were there but not showing in Firefox so..

> # chmod -R 755 /usr/lib/mozilla


Did the trick.

---

