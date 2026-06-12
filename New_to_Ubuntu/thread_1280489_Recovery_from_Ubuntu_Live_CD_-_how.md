---
title: "Recovery from Ubuntu Live CD - how?"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by flameproof on 2009-10-02
My Ubuntu doesn't boot anymore after removing Python (that's another story)

Is there a way to recover from the Live CD? I can't see any "recovery" function when booting.

Help is greatly appreciated.

---

### Post by pmlxuser on 2009-10-02
have you tries pressing escape on th boot menu.. happen quickly i think by default its 3 second.

anyway recovery can be done on the system boot menu, if that is also not working then try reinstalling the system but not formatting the home directory.

---

### Post by wobin77 on 2009-10-02
Just reinstall grub? A little more info would be handy...  ;-)

---

### Post by flameproof on 2009-10-02
I tried "esc" when HDD boot. That brings me to some DOS type option menu with different Kernel version - non of them get me out of that DOS type mode.

What now?

---

### Post by Paqman on 2009-10-02
> **flameproof said:**
> 
Is there a way to recover from the Live CD?

Yep!

Boot into the LiveCD, then mount your normal Ubuntu root partition by clicking on it "Places". Check what mount point in your system this has mounted at (should be in /media). Go to Applications > Accesories > Terminal and enter:
```

sudo chroot /mount/point/of/your/system
sudo apt-get update
sudo apt-get install python

```

If Python is the cause of your problem, that will fix it. You can install any other package you need that way, too. For instance you could reinstall ubuntu-desktop, gdm, linux-generic, and xorg, which would reinstall pretty much anything you need for a healthy Linux desktop.

---

### Post by flameproof on 2009-10-02
> **Paqman said:**
> Yep!

Boot into the LiveCD, then mount your normal Ubuntu root partition by clicking on it "Places". Check what mount point in your system this has mounted at (should be in /media). Go to Applications > Accesories > Terminal and enter:
```

sudo chroot /mount/point/of/your/system
sudo apt-get update
sudo apt-get install python

```

When I but the Live-DC I see the HDD is "/media/disk" I get:


```

sudo chroot /media/disk" 
chroot: cannot run command '/bin/bash': Exec format error

```

soooooo......?

PS: Mount point I got from: desktop > click HDD > Media Properties > Volume > Mount Point: /media/disk

If that matters, File System is ext3(1.0)

PPS: I don't know if that Ubuntu 9.04 is 32 or 64 type

PPPS: That PC has internet and it works.

---

### Post by pmlxuser on 2009-10-02
> **Paqman said:**
> Yep!
For instance you could reinstall ubuntu-desktop, gdm, linux-generic, and xorg, which would reinstall pretty much anything you need for a healthy Linux desktop.

+ 1


when you are in the dos like thing and gets to the $ prompt

you can then do ```

sudo apt-get install ubuntu-destop

```

dedfinately this will work, YOU Should however have internet connection ;)

---

### Post by Paqman on 2009-10-02
> **flameproof said:**
> 
soooooo......?


Sorry, my fault, i'm trying to do this form memory while at a non-Linux machine,and skipped some stuff Unmount your partition and try

```
sudo mount /dev/sdaX /mnt
```

Where X is the number of your root partition.

```

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt

```

And that should get you chrooted into your broken install so that you can repair the packages.

---

### Post by flameproof on 2009-10-02
I went back to a boot to command line with net support and did:

```
sudo apt-get install ubuntu-desktop
```

That got me 1 hour files to d/l, another 20 Minutes with some sort of updates, a new boot - and Bingo - a desktop.

Looks all back to normal now.

Reason for all the trouble was that I wanted to downgrade to Python 2.5.* since OpenERP can't work with Python 2.6 . I probably skip on OpenERP now, or install the server on Xp.

---

### Post by Paqman on 2009-10-02
> **flameproof said:**
> I went back to a boot to command line with net support and did:

```
sudo apt-get install ubuntu-desktop
```

That got me 1 hour files to d/l, another 20 Minutes with some sort of updates, a new boot - and Bingo - a desktop.

Looks all back to normal now.


Ah right, glad you got that sorted.

For future reference though, there's a huge difference between "my computer won't boot" and "my computer won't boot to a graphical desktop". If i'd known you were able to boot to the command line i'd have told you to try that straight away.

But your machine is fixed now, so woo! :P

---

