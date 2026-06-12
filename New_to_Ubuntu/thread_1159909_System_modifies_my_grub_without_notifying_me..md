---
title: "System modifies my grub without notifying me."
date: 2009-05-15
forum: New to Ubuntu
---

### Post by powel212 on 2009-05-15
Sometimes after an update my grub gets modified. On some of the machines I administer I don't use the "default 0" as as my default boot kernel. 

So, on these ocassions after running an update and my grub gets modified. I will shut down the machine without knowing the grub has been modified. Then the next person to use the machine may end up booting into "MemTest" or something else.

You can imagine if I spend an afternoon running updates on 10 different machines ,this can lead to some very confused employees when they can't boot into a windowed OS and end up staring at a blue MemTest screen. 

I would love it if when the grub is modified I got some kind of small notification perhaps on shutdown. 

Anyone one else experience anyting like this or have feedback or sugestions.

powel

---

### Post by bruno9779 on 2009-05-15
As far as I am aware, this happens only when you update Kernerls and Kernel-images

---

### Post by muteXe on 2009-05-15
Yeah this happens when i update to a new kernel, but i only have one machine so it's not too much hassle for me.

Although, the updater *does* prompt me during installation, asking me if i want to keep my old menu.lst.  If you say yes to this would it not keep your old menu.lst as well?

---

### Post by louieb on 2009-05-15
Can think of ways to handle it. 1.) use **default saved **and add savedefault to the desired entry. Also set the **lockold  **to what you want. 

or if you want MS windows or some other (not Ubuntu) OS
put its entry between these lines
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```
and use defaut 0

---

### Post by powel212 on 2009-05-15
> or if you want MS windows or some other (not Ubuntu) OS
put its entry between these lines
Code:

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST

and use defaut 0 

So I should end up with something like this?

```

default		0

timeout		4

#hiddenmenu

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-24-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-24-386 root=UUID=a326b458-cd37-4bba-a385-3903a70f0bae ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-386

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		Win
root		(hd0,1)
kernel		default

### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by radiocognition on 2009-05-15
Another quick trick you can do:

For my systems, I usually install a customized kernel, so you can imagine it usually is very bad when Ubuntu tries to install the latest kernel version to add support for hardware I don't even care about.  I use aptitude to hold my current version of the kernel, so that when software updates are applied, I never install a new version (Unless I want to do that, and I manually install the update on my own).
```

sudo aptitude hold linux-image-`uname -r`

```

---

