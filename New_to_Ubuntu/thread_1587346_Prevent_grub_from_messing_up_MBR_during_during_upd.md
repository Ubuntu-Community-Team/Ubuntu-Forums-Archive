---
title: "Prevent grub from messing up MBR during during update."
date: 2010-10-03
forum: New to Ubuntu
---

### Post by xieon on 2010-10-03
I recently upgraded from Ubuntu 10.04 to Ubuntu 10.10. During the installation everything went by itself, and I could just do my work, and let it do it's thing, however, there was one popup asking about grub not being installed, or something like that, and what drives? I

I really don't know what it said, but I'm almost positive that caused my problem. After it installed and restarted I was welcomed with 
```
no such device
grub rescue>
```
I could not use any commands, and was stuck. I tried tons of things, finally I booted with a live cd and used:
```
sudo apt-get install lilo
sudo lil -M /dev/sda/mbr
```

That worked, and I went into windows and had to remove 10.10 and reinstall 10.04, I noticed several people have this issue.

I'm wondering if anyone knows what to do during the 10.10 installation so this doesn't happen again.

Also, I'm using a partition of a drive and running wubu side by side dual boot with windows xp

---

### Post by Sidewinder1 on 2010-10-03
Don't think there's a way of preventing it; however, I seem to remember reading somewhere that after the install:
```
sudo update grub
```
solves the problem after the fact...
HTH,
Side

---

### Post by amjjawad on 2010-10-03
> **xieon said:**
> I recently upgraded from Ubuntu 10.04 to Ubuntu 10.10. During the installation everything went by itself, and I could just do my work, and let it do it's thing, however, there was one popup asking about grub not being installed, or something like that, and what drives? I

I really don't know what it said, but I'm almost positive that caused my problem. After it installed and restarted I was welcomed with 
```
no such device
grub rescue>
```
I could not use any commands, and was stuck. I tried tons of things, finally I booted with a live cd and used:
```
sudo apt-get install lilo
sudo lil -M /dev/sda/mbr
```

That worked, and I went into windows and had to remove 10.10 and reinstall 10.04, I noticed several people have this issue.

I'm wondering if anyone knows what to do during the 10.10 installation so this doesn't happen again.

Also, I'm using a partition of a drive and running wubu side by side dual boot with windows xp

Have you installed your GRUB in sda? the same partition where your Windows is installed? I suggest to have two partitions and install Ubuntu on the other partition and same goes for the boot loader. In that case, you could prevent lots of unnecessary hassle :)

---

### Post by wilee-nilee on 2010-10-03
[http://ubuntuforums.org/showthread.php?t=1586795](http://ubuntuforums.org/showthread.php?t=1586795)

**[COLOR="Red"]Original thread you make no mention in this thread that your using Wubi.[/COLOR]** You upgraded a Wubi install LOL. Wubi is not meant to be run this way and if you want to you have to know what your doing.

If you like Linux dual boot it you would have never had the problems If you had installed Ubuntu in it's own partitioning schema.

It is not the OS that is the problem it is the user understanding it.

---

