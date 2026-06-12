---
title: "cant clean GRUB"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Kocrachon on 2010-12-12
So right now I have a bunch of kernels showing up on my GRUB, and I have tried many methods of removing them but I having issues right now...

First, I removed them from the Package Manager
Restarted, and they are still there.
I then attempted the following method

```
kocrachon@kocrachon-desktop:~$ uname -r
2.6.35-23-generic
kocrachon@kocrachon-desktop:~$ cd/boot
bash: cd/boot: No such file or directory
kocrachon@kocrachon-desktop:~$ cd /boot
kocrachon@kocrachon-desktop:/boot$ ls vmlinuz*
vmlinuz-2.6.32-21-generic  vmlinuz-2.6.32-22-generic  vmlinuz-2.6.35-23-generic
kocrachon@kocrachon-desktop:/boot$ ^C
kocrachon@kocrachon-desktop:/boot$ cd
kocrachon@kocrachon-desktop:~$ sudo apt-get remove linux-image-2.6.32-21-generic
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package linux-image-2.6.32-21-generic
E: Couldn't find any package by regex 'linux-image-2.6.32-21-generic'
kocrachon@kocrachon-desktop:~$ cd /boot
kocrachon@kocrachon-desktop:/boot$ sudo apt-get remove linux-image-2.6.32-21-genericReading package lists... Done
Building dependency tree      
Reading state information... Done
E: Unable to locate package linux-image-2.6.32-21-generic
E: Couldn't find any package by regex 'linux-image-2.6.32-21-generic'
kocrachon@kocrachon-desktop:/boot$ sudo apt-get remove linux-image-2.6.32-22-generic
```

So even though they are not installed, I cannot remove them for some reason. I also attempted the following method with a base file.


```
#/bin/bash
ls /boot/ | grep vmlinuz | sed 's@vmlinuz-@linux-image-@g' | grep -v `uname -r` > /tmp/kernelList
for I in `cat /tmp/kernelList`
do
aptitude remove $I
done
rm -f /tmp/kernelList
update-grub

```


Still there, anyone able to help me out?

---

### Post by karthick87 on 2010-12-12
This thread will help you,

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

### Post by owiknowi on 2010-12-12
Wow, don't know if I can help you.

I usually correct or remove entries manually from /boot/grub/menu.lst if they give trouble.
This is after i removed the software properly through synaptic like you also did.

Do you perhaps use grub 2? Heard of more troubles with that loader.

---

### Post by Kocrachon on 2010-12-12
Here is an example of my grub folder...


[IMG]http://brandonandjolene.com/miscimages/Screenshot.jpeg[/IMG]

---

### Post by Kocrachon on 2010-12-12
> **karthick87 said:**
> This thread will help you,

[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Doesn't help, the Startup-Manager doesn't allow me to edit it, just set the default.

I also tried the gksu gedit /boot/grub/menu.lst method but it broguht up a blank menu.lst file.

---

### Post by karthick87 on 2010-12-12
Remove the un-used kernels then,

```
sudo apt-get purge <package_name>
```

---

### Post by Kocrachon on 2010-12-12
> **karthick87 said:**
> Remove the un-used kernels then,

```
sudo apt-get purge <package_name>
```


same thing...

E: Unable to locate package linux-image-2.6.32-22-generic
E: Couldn't find any package by regex 'linux-image-2.6.32-22-generic'

---

### Post by amjjawad on 2010-12-12
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Kocrachon on 2010-12-12
> **amjjawad said:**
> [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Used it, it only found 2.6.35-22, it did not find any of the 2.6.32-xx which are the ones I want to get rid of.

---

### Post by karthick87 on 2010-12-12
Open up a terminal type in **apt-get remove linux** and press tab a few times, all matching entries will be shown..Post that ouput here.

---

### Post by amjjawad on 2010-12-12
Have you done:

```
sudo update-grub

```

The last line in that guide was: > then update grub.

---

### Post by Kocrachon on 2010-12-12
linux-firmware 
linux-image-2.6.35-22-generic
linux-headers-2.6.35-23          
linux-image-2.6.35-23-generic
linux-headers-2.6.35-23-generic 
 linux-libc-dev
linux-headers-generic            
linux-sound-base

---

### Post by amjjawad on 2010-12-12
> **Kocrachon said:**
> linux-firmware 
linux-image-**2.6.35-22-generic**
linux-headers-2.6.35-23          
linux-image-**2.6.35-23-generic**
linux-headers-2.6.35-23-generic 
 linux-libc-dev
linux-headers-generic            
linux-sound-base

If I were you, I would never remove these two and always keep at least two entires.

---

### Post by Kocrachon on 2010-12-12
> **amjjawad said:**
> If I were you, I would never remove these two and always keep at least two entires.

I am running 2.6.35-23...


But when I boot up my GRUB list shows the following instead

2.6.35-23
2.6.32-22
2.6.32-21

I want to get rid of the 32-xx

and yes, i perfomred update-grub after each attempt

Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

---

### Post by karthick87 on 2010-12-12
I think the only old kernel you have is,

> **Kocrachon said:**
> linux-firmware 
linux-image-2.6.35-22-generic


I suggest you to have atleast one old kernel,if you get any problems later.You can use your old kernel in that case..

---

### Post by Kocrachon on 2010-12-12
> **karthick87 said:**
> I think the only old kernel you have is,



I suggest you to have atleast one old kernel,if you get any problems later.You can use your old kernel in that case..

I plan to upgrade my kernel to another kernel, but right now I am trying to clear out these other 2 older ones from GRUB...

---

### Post by amjjawad on 2010-12-12
> **Kocrachon said:**
> I am running 2.6.35-23...


But when I boot up my GRUB list shows the following instead

2.6.35-23
2.6.32-22
2.6.32-21

I want to get rid of the 32-xx

and yes, i perfomred update-grub after each attempt

Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1

If you have 3 then try to remove the oldest one and keep the other two. In that case, it would be: **2.6.32-21-generic**

Point is: Keep minimum two.

---

### Post by karthick87 on 2010-12-12
You can edit/remove the **entries** manually (gksu gedit /boot/**grub**/**grub**.cfg), but they will be re-generated when you update to a newer kernel.


Post the output of,
```
 gksudo gedit /boot/grub/grub.cfg
```

---

### Post by Kocrachon on 2010-12-12
> **amjjawad said:**
> If you have 3 then try to remove the oldest one and keep the other two. In that case, it would be: **2.6.32-21-generic**

Point is: Keep minimum two.

I get that, but right now the issue I am running into is I have tried to remove them, even just the one, but they are not removing from GRUB. I have performed many many steps, and they are still there.

---

### Post by amjjawad on 2010-12-12
> **Kocrachon said:**
> I get that, but right now the issue I am running into is I have tried to remove them, even just the one, but they are not removing from GRUB. I have performed many many steps, and they are still there.

So when you remove them, you restart and these entries are still there and can't be removed, right?

If yes, then I'm afraid I can't be much help.

---

### Post by Kocrachon on 2010-12-12
> **karthick87 said:**
> You can edit/remove the **entries** manually (gksu gedit /boot/**grub**/**grub**.cfg), but they will be re-generated when you update to a newer kernel.


Post the output of,
```
 gksudo gedit /boot/grub/grub.cfg
```

That did exactly what I wanted, thank you sir. I didn't want to get rid of them persay, but I wanted to clean up the view of my GRUB.

---

### Post by Kocrachon on 2010-12-12
> **amjjawad said:**
> So when you remove them, you restart and these entries are still there and can't be removed, right?

If yes, then I'm afraid I can't be much help.

That was exactly the issue, even though I removed them in so many ways (synaptic, apt-get remove, etc etc) they still showed up in GRUB, but his tip helped me so I am all good to go, thanks everyone.

---

### Post by amjjawad on 2010-12-12
> **Kocrachon said:**
> That was exactly the issue, even though I removed them in so many ways (synaptic, apt-get remove, etc etc) they still showed up in GRUB, **but his tip helped me so I am all good to go, thanks everyone.**

Great :)

Sorry, wasn't so much help to you!

---

### Post by owiknowi on 2010-12-12
Maybe helpful for future times (ran in the same troubles several times):

1. purge the unused kernels using synaptic
2. reboot
3. go to the folder/boot/grub/ and delete the unused kernels manually.
4. remove all unnecessary entries from the menu list manually

You can do this by using sudo or root (yes, the latter I have always enabled).
This works for me but can be a risk when for example having a multi boot system.

---

### Post by Quackers on 2010-12-12
There is more than one entry per kernel in Synaptic. If you just remove one the entry will still appear. Enter the number of the kernel into synaptic search and mark for complete removal. Then scroll down for further entries with the same number and mark those for removal.
What you have done now, will be over-written when grub is updated and the menu entry will return.

---

### Post by oldos2er on 2010-12-12
As well as linux-image-xxx, you need also to mark for removal linux-headers-xxx.

---

