---
title: "Failure to boot: Kernel must be Loaded"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by POF59 on 2009-09-26
Everything is running fine and good, talking on skype, ECT.

I turn off my computer to go do something.

I come back later, boot it up, choose ubuntu, and it starts to load.

It stops suddenly.

It gives me a command line, giving me standard instructions like esc to exit and tab to list commands. I type boot.

It tells me I have to load the kernel first.

Am I screwed?

---

### Post by POF59 on 2009-09-26
Still no luck, No clue what to do...

---

### Post by philinux on 2009-09-26
Can you post the errors messages it gives?

---

### Post by POF59 on 2009-09-26
> GRUB4DOS 0.4.4 2009-04-21, Memory: 64k/510M, MenuEnd: 0x43492
[Minimal BASH-like line editing is supported for the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits]

grub>boot
Error 8: Kernel must be loaded before booting.
grub>That's everything.

---

### Post by hfranz on 2009-11-11
Same here. I have been running Wubi with Ubuntu 08.04, 08.10 and 09.04 with no problems. With 09.10 i have now already lost 3 wubi installations due to unability to boot.

My conclusion is that Wubi for Ubuntu 09.10 has at least on showstopper bug.

I have not yet performed a detailed analysis of the causes of the failure but I suspect that it is related to installing packages that rebuild the ramdisk or upgrade the kernel or otherwise change the grub configuration. That would be plausible because the major version change of grub.

---

### Post by kmestay on 2009-12-28
I am getting the same errors on a new install of Ubunto GNU GRUB V1.97~Beta4
After the install, I get prompted to boot Windows XP or Ubuntu
Ubuntu selection does not give a menu.
Instead it gives a command screen with a

sh:grub> prompt
Pressing TAB shows the allowable list of commands which include boot and ls
ls does not show a /grub or /boot directory

Entering the boot command generates the following error

error: no loaded Kernel

I have installed twice, both times with identical results

---

### Post by JoJerome on 2010-01-10
Wading through the same issue here. I seem to have solved it with the instructions at:

[https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode

Am having other boot issues now, but that one seems fixed. Good luck!

---

### Post by zonegrise on 2010-01-12
> **kmestay said:**
> I am getting the same errors on a new install of Ubunto GNU GRUB V1.97~Beta4
After the install, I get prompted to boot Windows XP or Ubuntu
Ubuntu selection does not give a menu.
Instead it gives a command screen with a

sh:grub> prompt
Pressing TAB shows the allowable list of commands which include boot and ls
ls does not show a /grub or /boot directory

Entering the boot command generates the following error

error: no loaded Kernel

I have installed twice, both times with identical results
Hi,did you get a fix for that problem?
I have the same problem but I don't want to re-install.

Thanks

---

### Post by warfacegod on 2010-01-12
I think you need this. Wubi installs have been getting fragged by the last batch of updates.

---

### Post by robtoth on 2010-01-12
Not sure if this will help people, but [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode) worked like a charm.

For Wubi, make sure you follow the specific instructions for Steps 3 & 7.  

You also have to figure it out for your own computer, but mine was as follows:
[LIST]
[*]For my setup, I only needed steps 7-9
[*]As I had a Windows Recovery partition located at sda1 (came with my lenovo R61), my partition was sda2
[*]Typing the following at the GRUB prompt got Ubuntu up and running:
```

linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot

```
[/LIST]

I will now probably reinstall GRUB just to make sure everything is good for my next boot.

---

### Post by warfacegod on 2010-01-12
My apologies, I forgot to put the link in my last post.

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by CaCtUs2003 on 2010-04-14
> **warfacegod said:**
> My apologies, I forgot to put the link in my last post.

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

Dude, thanks!  You're a life saver!  This bug fix worked for me!

---

