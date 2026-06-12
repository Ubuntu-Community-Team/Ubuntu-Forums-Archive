---
title: "Help With GRUB"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by TheStagesmith on 2009-02-27
So this morning I installed Ubuntu 8.10 in a dual-boot configuration alongside XP. Now, I'm not the only one using this computer, but I am by far the most tech-savvy. The others using the computer don't want to muck around with a bootloader, so my question is this:
How does one configure GRUB to boot into XP by default and boot into Ubuntu only if a button is pressed during the boot sequence? Or is there any other way to make XP the default OS?

Thanks a ton.

---

### Post by taurus on 2009-02-27
You can either edit /boot/grub/menu.lst by hand (from a terminal) 

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
or you can install startupmanager and use it to configure which OS is the default.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install startupmanager
gksudo startupmanager
```

---

### Post by sleepyjon on 2009-02-27
> **taurus said:**
> You can either edit /boot/grub/menu.lst by hand (from a terminal) 

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
or you can install startupmanager and use it to configure which OS is the default.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install startupmanager
gksudo startupmanager
```

That doesn't fully explain what to edit.

To get XP to boot by default, change this line:

```

 # is the entry saved with the command 'savedefault'.
 # WARNING: If you are using dmraid do not use 'savedefault' or your
 # array will desync and will not let you boot your system.
 default   0

```

to

```

 # is the entry saved with the command 'savedefault'.
 # WARNING: If you are using dmraid do not use 'savedefault' or your
 # array will desync and will not let you boot your system.
 default   0

```

Then put 
```

savedefault

```

Under your xp entry.

---

### Post by TheStagesmith on 2009-02-27
Thanks a ton, guys. I used the startupmanager method, mainly because I don't trust myself mucking around in files like that yet... :P

But anyway, everything is working now, so thanks again. You'll probably be seeing more of me around here soon. Thanks!

---

### Post by stchman on 2009-02-27
> **TheStagesmith said:**
> So this morning I installed Ubuntu 8.10 in a dual-boot configuration alongside XP. Now, I'm not the only one using this computer, but I am by far the most tech-savvy. The others using the computer don't want to muck around with a bootloader, so my question is this:
How does one configure GRUB to boot into XP by default and boot into Ubuntu only if a button is pressed during the boot sequence? Or is there any other way to make XP the default OS?

Thanks a ton.

Yes StartUpManger is the best way.  If you hand edit and make Windows the first entry in the GRUB list the next kernel update will wipe out that entry.

---

