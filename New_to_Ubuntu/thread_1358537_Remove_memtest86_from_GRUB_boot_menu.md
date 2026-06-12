---
title: "Remove memtest86 from GRUB boot menu?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by N_L on 2009-12-18
Hi, new to ubuntu hence my posting here.
I installed ubuntu from livecd and all went well. Dual booting with Window 7 on other partition.

Now, when I turn on PC I have like 5 options, 2 memory tests, ubuntu and ubuntu recovery and windows 7.
Is there any way to remove memory tests(can't even run them), and is there reason to have them?

/boot/grub/menu.lst, is empty.

---

### Post by audiomick on 2009-12-18
I would suggesting leaving them there. Memtest is for checking your RAM. It is very easy to use. You just set it running and watch the results. Basically, a healthy RAM should show no errors.

Hopefully you will never need it, but if you ever do, you really need it.

---

### Post by N_L on 2009-12-18
Hi, I know what memtest is, and I have hirens bootCD which beside memtest got bunch of other test tools, and since I like things minimal 2 memtest86 options when booting(and they don't work, says memory too low) annoy me :/

---

### Post by OrangeCrate on 2009-12-18
If you install the "startupmanager" package, I believe under the "Advanced" tab, there is a check box to either show, or not show, memtest86 in the grub menu.

(I've never chosen to get rid of it, but it looks like the option exists.)

---

### Post by plucky on 2009-12-18
> **N_L said:**
> Hi, new to ubuntu hence my posting here.
I installed ubuntu from livecd and all went well. Dual booting with Window 7 on other partition.

Now, when I turn on PC I have like 5 options, 2 memory tests, ubuntu and ubuntu recovery and windows 7.
Is there any way to remove memory tests(can't even run them), and is there reason to have them?

/boot/grub/menu.lst, is empty.

Read [Grub2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Good Luck

---

### Post by audiomick on 2009-12-18
OK, I can relate to that.
If you are using 9.10, it will be grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If it is an earlier Ubuntu, it will be grub
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Instructions for editing the boot options are in there.

Hope that helps.

---

### Post by Wiebelhaus on 2009-12-18
Old way , Edit that config file.

New way , Remove it in the same fashion you would multiple kernel revisions in Synaptic.

Then run:

```
sudo update-grub
```

P.S.

Nevermind those errors it's that 100mb partition from Win 7.

---

### Post by kansasnoob on 2009-12-18
> **plucky said:**
> Read [Grub2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Good Luck

+1!

Specifically:

# Omitting memtest86+: To prevent "memtest86+" entries in your Grub 2 menu, remove the "executable" bit from /etc/grub.d/20_memtest86+. You can do this via a file browser by selecting "Properties (right click), Permissions", or via the command line:

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

---

### Post by N_L on 2009-12-18
So many replies so fast, wow, thanks, I'll try it now.

But I have another question, 
since I'm using ubuntu on laptop when I close the lid and it goes to standby(I guess) once I try to get back into ubuntu screen just stays black and I can't do anything beside holding power button and shutting it down.
Anyone know why this is happening?
Got Nvidia 9600M GT graphic card if that matters.

---

### Post by audiomick on 2009-12-18
One of the prerequisites for suspend to work properly is that your swap partition is at least as big as your RAM.

---

### Post by N_L on 2009-12-18
I have 4 GB of ram and my swap partition has 6.3 swap space.
Type: Linux swap (0x82)

---

### Post by egalvan on 2009-12-18
> **N_L said:**
>  2 memtest86 options when booting(and they don't work, **says memory too low**) 

> I have **4 GB of ram**
swap partition has 6.3 swap space.
Type: Linux swap (0x82)

If you have 4GB of RAM, and memtest86 throws a ¨low memory¨ error,

then something is seriously wrong.

---

### Post by joes7 on 2009-12-18
Leave it alone! You may need it, and it is unsafe to remove it.

---

### Post by N_L on 2009-12-18
Thanks guys, I fixed everythign I needed and set up most of stuff the way I like it, all works now, and I'm loving it so far. :)

---

### Post by Zimrie on 2010-12-07
for removing memtest
sudo chmod -x /etc/grub.d/20_memtest86+
then sudo update-grub

from
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by N_L on 2010-12-07
Necro much :D

---

### Post by ImDougy on 2010-12-07
thank u [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG] wanted to do this 4 about 10 months but never knew how

---

