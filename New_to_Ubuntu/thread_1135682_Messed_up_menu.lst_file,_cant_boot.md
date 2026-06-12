---
title: "Messed up menu.lst file, cant boot"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-04-24
So I took the plunge and updated from 8.10 to 9.04

During the installation process it asked if I wanted to change or keep the menu.lst file, being on the safe side I chose to keep the original file.

When Ubuntu reloaded I noticed in my grub list (*dualing with winxp, on xp to type this message*) that it said ubuntu 8.10, I selected it anyway and it booted into ubuntu 9.10.

I figured I should fix the fact that the grub menu says 8.10 and opened menu.lst and using the new menu.lst that the upgrade wanted to install I added those 9.10 lines to menu.lst, I commented out the 8.10 lines, this was a mistake.

When I reboot the 9.04 lines didnt have the right info to boot up and I was sent to a terminal prompt and have no idea what to do next.

So, any ideas how I can access my menu.lst file from windowsxp would be good OR ideas how I can access it from a command prompt would be good ...

Any other ideas are very welcome ...

Thanks in advance ...

---

### Post by Melk79 on 2009-04-24
Couple of things:

Try another line on grub and see if you can start in recovery mode.  If so, you can start a terminal session and edit menu.lst with ```
sudo nano /boot/grub/menu.lst
```... so long as you know what to put back to make it right again.

Failing that you can also download [SuperGrub]("http://www.supergrubdisk.org/") and use it to repair your mbr.

---

### Post by VitaminBB on 2009-04-24
> **Melk79 said:**
> Couple of things:

Try another line on grub and see if you can start in recovery mode.  If so, you can start a terminal session and edit menu.lst with ```
sudo nano /boot/grub/menu.lst
```... so long as you know what to put back to make it right again.

Failing that you can also download [SuperGrub]("http://www.supergrubdisk.org/") and use it to repair your mbr.

Cant even get that far ...

In the grub list the line for 9.04 is this 

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/PIC-0027.jpg[/IMG]

and this is what it looks like when I load a 9.04 line

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/PIC-0028.jpg[/IMG]

The old 8.10 grub line booted me into ubuntu but I commented those lines out and cant get access to change them.

---

### Post by bodhi.zazen on 2009-04-24
You will need to boot with a live CD.

You then mount your ubuntu partition at asy /mnt

```
sudo mount /dev/sdxy /mnt
```

Change 'sdxy" to your root partition (sda1 ? )

Then edit with :

```
gksu gedit /mnt/boot/grub/ment.1st
```

---

### Post by VitaminBB on 2009-04-24
> **bodhi.zazen said:**
> You will need to boot with a live CD.

You then mount your ubuntu partition at asy /mnt

```
sudo mount /dev/sdxy /mnt
```

Change 'sdxy" to your root partition (sda1 ? )

Then edit with :

```
gksu gedit /mnt/boot/grub/ment.1st
```

So I actually just installed a product that allows windows to edit ext2/ext3 files and I then edited my menu.lst in windows, rebooted and selected the old 8.10 file line so I could at least log into ubuntu.


So what should I change on the 9.04 line ?

---

### Post by ymra on 2009-04-24
I think you probably are running 9.04.  As long as your system works ok what does it matter what the boot line reads.

---

### Post by VitaminBB on 2009-04-24
> **ymra said:**
> I think you probably are running 9.04.  As long as your system works ok what does it matter what the boot line reads.

I dont even know if its loading the right kernel

Its easy to just change the name if thats all I want to do but I want to make sure its loading the right kernel.

Heres a snippet of the menu.lst> 

title 		Ubuntu 9.04, kernel 2.6.24-21-generic
root 		(hd0,0)
kernel 		/boot/vmlinuz-2.6.24-21-generic root=UUID=5fe
initrd 		/boot/initrd.img-2.6.24-21-generic
quiet

title 		Ubuntu 9.04, kernel 2.6.24-21-generic (recove
root 		(hd0,0)
kernel 		/boot/vmlinuz-2.6.24-21-generic root=UUID=5fe
initrd 		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=ask 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

---

### Post by James_Lochhead on 2009-04-24
No, that isn't the right kernel for Jaunty. Jaunty kernel is 2.6.28-11.

---

### Post by James_Lochhead on 2009-04-24
Do the GRUB restoration tutorial in my sig. That should correct the problem.

---

### Post by VitaminBB on 2009-04-24
> **James_Lochhead said:**
> Do the GRUB restoration tutorial in my sig. That should correct the problem.

Is there an easier way?

I dont have a livecd, my burner is broke and im stunned theres not an easier way ...

Is there no short cut here?

No line in the menu.lst i can change?

How would I do this without a livecd?

---

### Post by durand on 2009-04-24
If you have windows, it's possible using the drivers for windows: [http://www.fs-driver.org/](http://www.fs-driver.org/) however they might not work depending on what you used for your partition type.

---

### Post by bodhi.zazen on 2009-04-24
The problem is your kernel lines in 9.04 are truncated

> title 		Ubuntu 9.04, kernel 2.6.24-21-generic
root 		(hd0,0)
**[color=darkred]kernel 		/boot/vmlinuz-2.6.24-21-generic root=UUID=5fe[/color]**
initrd 		/boot/initrd.img-2.6.24-21-generic
quiet

Should look like this :

```
title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
**[color=green]kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=ask quiet[/color]**
initrd		/boot/initrd.img-2.6.27-10-generic
quiet
```

See how your kernel line was truncated ? The green line is all one line in menu.1st ;)

Note: I added "quiet" at the end, it is not critical ;)

---

### Post by VitaminBB on 2009-04-24
> **bodhi.zazen said:**
> The problem is your kernel lines in 9.04 are truncated



Should look like this :

```
title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
**[color=green]kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a ro splash vga=ask quiet[/color]**
initrd		/boot/initrd.img-2.6.27-10-generic
quiet
```

See how your kernel line was truncated ? The green line is all one line in menu.1st ;)

Note: I added "quiet" at the end, it is not critical ;)

You beat me to it.

I was going to say why cant I just put in a new UUID.

---

### Post by Miljet on 2009-04-24
That's still not going to solve the problem of the wrong version kernel. Why don't you check your boot directory to see what kernel you have installed?

```
ls /boot
```

---

### Post by VitaminBB on 2009-04-24
> **Miljet said:**
> That's still not going to solve the problem of the wrong version kernel. Why don't you check your boot directory to see what kernel you have installed?

```
ls /boot
```

Here it is ...

> abi-2.6.24-21-generic                  initrd.img-2.6.27-10-generic
abi-2.6.27-10-generic                  initrd.img-2.6.28-11-generic
abi-2.6.28-11-generic                  memtest86+.bin
config-2.6.24-21-generic               System.map-2.6.24-21-generic
config-2.6.27-10-generic               System.map-2.6.27-10-generic
config-2.6.28-11-generic               System.map-2.6.28-11-generic
grub                                   vmcoreinfo-2.6.27-10-generic
initrd.img-2.6.24-21-generic           vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.24-21-generic.bak       vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-21-generic.dpkg-bak  vmlinuz-2.6.27-10-generic
initrd.img-2.6.24-21-generic.new       vmlinuz-2.6.28-11-generic

---

### Post by bodhi.zazen on 2009-04-24
In the kernel line use "vmlinuz-2.6.28-11-generic"

---

### Post by VitaminBB on 2009-04-25
> **bodhi.zazen said:**
> In the kernel line use "vmlinuz-2.6.28-11-generic"

Ok, that did it, the kernel loading now is 2.6.28.11

Is there anything else I need to check to make sure its implemented?

---

### Post by bodhi.zazen on 2009-04-25
from the command line, enter

```
cat /etc/issue
```

to make sure you are up to date :

```
update-manager
```

---

### Post by Lazy-buntu on 2009-04-25
If you're looking to tweak your boot menu and login window, install StartUp-Manager

```
sudo apt-get install startup-manager
```

I'm not 100% sure on that code, if it doesn't work just find it in synaptic.

---

### Post by VitaminBB on 2009-04-25
> **bodhi.zazen said:**
> from the command line, enter

```
cat /etc/issue
```

to make sure you are up to date :

```
update-manager
```

It says 9.04 and im running the right kernel

I think thats it folks!

Thanks to all!

---

