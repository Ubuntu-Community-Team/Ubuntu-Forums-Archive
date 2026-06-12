---
title: "error that wont let me install linux"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by spadhawk on 2008-12-27
Hi everyone. im reposting this error cuz i think there was some misinformation in the last thread(bad error i think my hard drive is done)
i have replaced the hard drive and ram and still get this error when i try to install ubuntu. this is a friends laptop he brought it to me because it had a couple of hard crashes while watching movies on battery and the battery died. and then ubuntu wouldn't load.
this is a 64 bit system and using the 64bit ubuntu version. the live cd runs fine. when you do a full install this is the message that is generated.


```
Boot from (hd0,0) ext3 4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
Starting up ...
[ 0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (Did the system wait long enough?)
-Check root= (Did the system wait for the right device?)
-Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/disk/by-uuid/4391e1d9-a5ee-4e31-ad73-8a2cec42a48b does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 35.733317] 8139cp 0000 :08 :02.0: This (id 10ec : 8139 rev 10) is not an 8139c+ compatible chip
[ 35.733366] 8139cp 0000 :08 :02.0: Try the "8139too" driver instead
```


has anyone encountered this or can anyone help me solve this please

Frustrated Harry

---

### Post by damis648 on 2008-12-27
EDIT: Sorry, I misread your post. Try this: At the GRUB menu (Press ESC to get to it if you have a timeout set), highlight the default Ubuntu option and press 'e'. Then, go down to the Kernel line and press 'e' again. Scroll over to
```
UUID=4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
```
and replace that with
```
/dev/sda1
```
(or whatever the device is). Then press enter, followed by 'b'. See if that works.

Also, is this a SATA drive? Is the mode set to AHCI or ATA?

---

### Post by Bucky Ball on 2008-12-27
Hmm. Is there anything on that drive? Is it still operational? Has it been operational since the crash? Is the battery still ok or are you using mains power? I would stick to mains power for the installation.

---

### Post by spadhawk on 2008-12-27
this is a 80 gb ide drive
have reformatted the drive and reinatalled ubuntu fresh with a new drive and still same error. the system will run the live cd fine

---

### Post by damis648 on 2008-12-27
> **spadhawk said:**
> this is a 80 gb ide drive
have reformatted the drive and reinatalled ubuntu fresh with a new drive and still same error. the system will run the live cd fine

Try what I suggested, see if it works.

---

### Post by spadhawk on 2008-12-27
ok I tried what you said and this is the error now

```
Boot from (hd0,0) ext3 4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
Starting up ...
[ 0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (Did the system wait long enough?)
-Check root= (Did the system wait for the right device?)
-Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/sda1 does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

when the code says please wait.....  the ubuntu splash comes up with the bar going back and forth and never stops.  then the rest of the code comes up

---

### Post by Bucky Ball on 2008-12-27
okay, when you drop to shell, could you type in:

```
nano /boot/grub/menu.lst
```and find the section which refers to your boot at the bottom of the file. In there, you will have a line that looks like this:

```
root (hd0,0)
```or something like that (hd *,*), where * could be another number, not just 0. Make a note of what this is. Then, could you type:

```
blkid
```and check the UUID of /sda1. It is a long, alpha-numeric. Note that and post both pieces of information here.

Now, type in:

```
nano /etc/fstab
```and find the entry for /dev/sda1. Could you also post that here?

If you are getting to the grub menu, you could boot into recovery and see what error, if any, gets thrown. Also, if you can get to the grub menu from boot, you may be able to massage the grub entry for your boot easily from there (choose the kernel, hit 'e' to edit, choose the kernel line and 'e' again.

When you are booting, make sure you have no USB dongles or external drives or devices of any kind plugged in for the moment.

---

### Post by spadhawk on 2008-12-27
after typing the first line it says ```
/bin/sh: nano: not found
```
and the same for the second line you wanted

---

### Post by unutbu on 2008-12-27
Substitute the command 'cat' in place of 'nano'.

---

### Post by spadhawk on 2008-12-27
Cat instaed of nano generates

```
/boot/grub/menu. 1st: no such file or directory
(initramfs)
```

---

### Post by Bucky Ball on 2008-12-27
> **spadhawk said:**
> Cat instaed of nano generates

```
/boot/grub/menu. 1st: no such file or directory
(initramfs)
```

menu.lst 

No gap as you have above. It is a little L, not a one (1). Easiest to just copy and paste to your terminal ...

cat /boot/grub/menu.lst

---

### Post by spadhawk on 2008-12-30
I guess with the lack of posts on this problem nobody has seen this before.
could it be the ide plug on the motherboard? im at my wits end. could it be fried processor?i kinda doubt the processor as it runs the live cd no problem. any suggestions will be tried

---

### Post by spadhawk on 2008-12-30
when i use cat/boot/grub/menu.lst  at the shell this is the error generated

/bin/sh: cat/boot/grub/menu.lst: not found

---

### Post by Bucky Ball on 2008-12-30
Can you run recovery from the grub list? Sorry, can't remember where we were at with this.

ps: okay, here's something else that comes to mind ... you are running a full install from the hard drive? Not wubi or live cd?

You need to be:

root@yourcomputer

etc etc Not:

/bin/sh

Terminal for these commands and just paste 'em in.

---

### Post by spadhawk on 2008-12-30
i can run the recovery from grub
i am running a full install not wubi or live
when i have been typing in terminal i have to run the live cd
but typing in the shell for the cmds you asked for
i ran the recovery and it gets down to the last line 

[  35.800761] Uniform CD-ROM driver Revision: 3.2

---

### Post by Bucky Ball on 2008-12-30
Well, spadhawk, something is seriously wrong. If you have a full install, how come you need to run a live CD to get to a terminal? You should find that from:

Applications->Accessories->Terminal

?

Did you by any chance do a wubi install or something equally as exotic?

---

### Post by spadhawk on 2008-12-30
because it only gets to the error i posted after grub:

Boot from (hd0,0) ext3 4391e1d9-a5ee-4e31-ad73-8a2cec42a48b
Starting up ...
[ 0.004000] Aperture beyond 4GB. Ignoring.
loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (Did the system wait long enough?)
-Check root= (Did the system wait for the right device?)
-Missing modules (cat /proc/proc: Is /dev)
ALERT! /dev/disk/by-uuid/4391e1d9-a5ee-4e31-ad73-8a2cec42a48b does not exist. Dropping to shell!


Busy box v1.10.2 (ubuntu 1:1.10.2-ubuntu6) built-in shell(ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 35.733317] 8139cp 0000 :08 :02.0: This (id 10ec : 8139 rev 10) is not an 8139c+ compatible chip
[ 35.733366] 8139cp 0000 :08 :02.0: Try the "8139too" driver instead

---

### Post by Bucky Ball on 2008-12-30
Yea, because the other message was saying you don't have a:

```
 menu.lst
```That is problematic. Can you check out:
```

cat /boot/grub/menu.lst

```... after booting the recovery kernel and then dropping to a root shell? I am not sure what is going on here at this point. :)

The other thing that worries me is that this command doesn't work:

```

nano /boot/grub/menu.lst

```

---

### Post by spadhawk on 2008-12-30
how do you get to the root shell from the recovery kernal?
cuz the last line the recovery gives me is:
[ 35.800761] Uniform CD-ROM driver Revision: 3.2
and then to 
(initramfs) with flashing cursert 

when i try  
```
cat/boot/grub/menu.lst
```
after grub recover

i get:
```
/bin/sh:cat/boot/grub/menu.lst not found
```

---

### Post by Bucky Ball on 2008-12-30
Okay. Don't get me wrong here, but you need to be really precise and specific with your commands in the terminal. 

```
 cat/boot/grub/menu.lst
```is not the same as:

```
 cat /boot/grub/menu.lst
```You left out a space. That is probably why your 'nano' didn't work either.

Try this. Just copy it from this page and paste it (ctl/shift/v) into a terminal:

```
 nano /boot/grub/menu.lst
```

Let us know how you go. :)

---

### Post by spadhawk on 2008-12-30
i tried both with the space and without the space after nano and cat
both still say not found
im on a different computer talking to you because the other one wont boot into ubuntu so i have no way to copy and paste

---

### Post by Bucky Ball on 2008-12-30
[http://ubuntuforums.org/showthread.php?t=963892](http://ubuntuforums.org/showthread.php?t=963892)

[https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaq6715b#The%20AMD64%20related%20bug%20in%208.10%20%20-%20%22Aperture%20beyond%204GB%22%20/%20IOMMU%20message%20when%20booting%20ubuntu](https://wiki.ubuntu.com/LaptopTestingTeam/HPCompaq6715b#The%20AMD64%20related%20bug%20in%208.10%20%20-%20%22Aperture%20beyond%204GB%22%20/%20IOMMU%20message%20when%20booting%20ubuntu)

There is a start. You have upgraded to 8.10?

---

### Post by spadhawk on 2008-12-30
yes i loaded the new ubuntu but the error was there before loading the new ubuntu.

there is only 1gb ram

when i went to look at the bios i found that under information
the uuid# was different from the one listted in the error
i also found that i am not getting into the full recovery mode  it only gets to [  35.802255]uniform cd-rom driver revision: 3.20
and then (initramfs) with flashing curser
so im not getting to the root shell

---

