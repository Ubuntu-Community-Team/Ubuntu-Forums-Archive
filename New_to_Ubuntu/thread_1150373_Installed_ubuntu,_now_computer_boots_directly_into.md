---
title: "Installed ubuntu, now computer boots directly into windows"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by skaught78 on 2009-05-06
Boots directly to windows. Doesn't give me the option to choose my OS when I start my computer up. Tried pushing f8, but it only lists windows...

---

### Post by pastalavista on 2009-05-06
Need a little more information. Boot with the live CD, open terminal and post the output of
```
sudo fdisk -l
```

---

### Post by skaught78 on 2009-05-06
Dont have the live cd, I used the alternate install cd because it is the only one that would work on my POS computer. Can I do what you say with that cd? If so, How do I get to the terminal?

---

### Post by nhasian on 2009-05-06
no you cant liveboot from the alternate cd.  instead try the supergrubdisk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Zeedok on 2009-05-06
It might be the GRUB menu settings that need some adjustment (GRUB is the menu that allows you to choose which OS you want to use).  Maybe it has defaulted to "wait 0 seconds before booting last OS" or something like that.  

It would probably best easiest to get your hands on a LiveCD so that you can boot into a linux environment and try to edit your GRUB config file (called /boot/grub/menu.lst).  [Here is a website that may help]("http://www.linuxmigration.com/quickref/kernel/grub.html#config").

---

### Post by skaught78 on 2009-05-06
What is this GRUB anyway???

---

### Post by pastalavista on 2009-05-06
Don't know, never used an alternate install. You could download and burn a live CD of either Ubuntu or [SuperGrub]("http://www.supergrubdisk.org/").

---

### Post by Zeedok on 2009-05-06
> **nhasian said:**
> no you cant liveboot from the alternate cd.  instead try the supergrubdisk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Hey that looks pretty cool.  Have to check it out.

---

### Post by nhasian on 2009-05-06
GRand Unified Bootloader command shell

it lets you choose which operating system to boot.  :)

It is the standard bootloader in ubuntu.  there are others like LiLo and NTLoader (from msft)

> **skaught78 said:**
> What is this GRUB anyway???

---

### Post by skaught78 on 2009-05-06
> **nhasian said:**
> GRand Unified Bootloader command shell

it lets you choose which operating system to boot.  :)

It is the standard bootloader in ubuntu.  there are others like LiLo and NTLoader (from msft)

Tried it. No luck. I give up :( at least for tonight. Maybe I will dive again into the insanity of getting ubuntu on my machine in the morning. If I don't first smash the ******* with an industrial sledge hammer first.

---

### Post by Zeedok on 2009-05-06
Don't give up forever - it is worth it, promise.  If it is a clean install, you could just start again tomorrow?

Good luck.

---

