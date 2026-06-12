---
title: "Cant mount .ISOs"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by LostMagix on 2009-03-03
Gmount returns with...

"An error occured
 could not find any free loop device"

So i dropped to the terminal...

```
:~$ sudo modprobe loop
FATAL: Error inserting loop (/lib/modules/2.6.27-13-generic/kernel/drivers/block/loop.ko): Cannot allocate memory

```

Any idea how to fix this?

---

### Post by starcannon on 2009-03-03
Just reread your post, are you already using gmountiso? If so perhaps running it as super user would do the trick?


```
sudo apt-get install gmountiso
```Then open up the utility in Applications>System Tools>Gmount-iso

Enjoy

---

### Post by ddixonr on 2009-03-03
Try this post: [http://ubuntuforums.org/showthread.php?t=953118]("http://ubuntuforums.org/showthread.php?t=953118")

---

### Post by LostMagix on 2009-03-03
I have Gmount...

its not working

---

### Post by LostMagix on 2009-03-03
> **ddixonr said:**
> Try this post: [http://ubuntuforums.org/showthread.php?t=953118]("http://ubuntuforums.org/showthread.php?t=953118")

```
:~$losetup /dev/loop0
loop: can't open device /dev/loop0: No such device or address
:~$ losetup loop_device 
loop: can't open device loop_device: No such file or directory


```

---

### Post by ddixonr on 2009-03-03
How are you attempting to mount this file? Are you not using the graphical interface? Typing 'Gmount-iso' into a terminal brings up the interface, right? I'm asking because I'm now unsure where you are getting that error message.

---

### Post by LostMagix on 2009-03-03
Gmount GUI comes back with...

```

An error occured
could not find any free loop device
```

When I drop down to the terminal to load the loop module in order to mount the ISO i get this...

```
:~$ sudo modprobe loop
FATAL: Error inserting loop (/lib/modules/2.6.27-13-generic/kernel/drivers/block/loop.ko): Cannot allocate memory

```

---

### Post by ddixonr on 2009-03-03
I found this site that may help release loop devices: []("http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt")[http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt](http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt)

---

### Post by LostMagix on 2009-03-03
> **ddixonr said:**
> I found this site that may help release loop devices: []("http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt")[http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt](http://svn.rpmforge.net/svn/trunk/tools/mrepo/docs/loop-devices.txt)

This one fixed it

Thank you very much!

---

