---
title: "Newbie emergengy with grub"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by copracr on 2010-02-01
OK,  so I'm at work and got the bright idea to install ubuntu 9.10 on a 4gb jump drive.  I thought having my own OS with no filters to the net and being able to write/save homework on the go would be cool.  

My problem is I loaded grub on the HD of the work computer!  Now the PC doesn't boot when I pull the thumb drive out.  It says something like:
Starting GRUB
Disk not found

Then it starts some kind of command prompt.  I can get the exact error message if needed.

Seriously screwed if IT has to come out and fix this.  What can I do?

---

### Post by Leppie on 2010-02-01
most probably you can restore things from your ubuntu install (on the jump drive).
what os is installed on the work computer?
and what device reference does the jump drive have (e.g. /dev/sdb, /dev/sdc, etc.)?

---

### Post by copracr on 2010-02-01
Windows XP is on the work PC (Dell Optiplex 760).
According to the Palimpsest Disk Utility, the jump drive is dev/sdb and the 80gb HD that windows is on is dev/sda.

I'm booted up in ubuntu right now if that matters.

---

### Post by copracr on 2010-02-01
I dont know what this means either,  but when I try to mount the c: and explore it i get an error message with these details:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by Leppie on 2010-02-01
in ubuntu, issue the following commands in a terminal:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```this will restore the mbr of the work computer. ignore the warning if you receive one installing lilo.
then install grub2 to the mbr of your jump drive:
```
sudo grub-install --recheck /dev/sdb
```

note that there are no numbers in these commands as you are installing to the mbr's and not to some partitions.

---

### Post by copracr on 2010-02-01
OK,  I cut and pasted so I would get it exactly right.  Should I reboot and see if all is well?

---

### Post by Leppie on 2010-02-01
> **copracr said:**
> OK,  I cut and pasted so I would get it exactly right.  Should I reboot and see if all is well?
could you first [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?
this way we can double check if everything went well before rebooting ;)

---

### Post by copracr on 2010-02-01
SUCCESS!!!!  I haven't been this happy to see a windows logo since 3.11.  You are awesome man,  if you need anything I got you covered.  This is why I run Ubuntu at home,  I don't even know what sudo is but you guys help me through all kinds of weird issues.

UBUNTU rocks!!! and now it rocks from a thumb drive!

---

### Post by Leppie on 2010-02-01
> **copracr said:**
> SUCCESS!!!!  I haven't been this happy to see a windows logo since 3.11.
glad windows is booting, though 3.11 was pretty bad... c'mon...

> **copracr said:**
> You are awesome man,  if you need anything I got you covered.  This is why I run Ubuntu at home,  I don't even know what sudo is but you guys help me through all kinds of weird issues.
you're welcome, glad to have been of help :)

> **copracr said:**
> UBUNTU rocks!!! and now it rocks from a thumb drive!
sure does, but have you tried the thumb drive as well after this operation?

---

### Post by copracr on 2010-02-01
I should mention for future newbies that read this I messed up on my first try and put this in as one command:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
It didn't work like this.
I was getting nervous until I tried again by running the second line all by itself.

---

### Post by copracr on 2010-02-01
Leppie -
I went from DOS to windows,  that was a whole different machine for me.  

I'm typing from ubuntu thumb drive at work right now!

---

### Post by Leppie on 2010-02-01
> **copracr said:**
> Leppie -
I went from DOS to windows,  that was a whole different machine for me.
3.11 was a bit more like linux... as the gui had to be loaded on top of the base os (dos). 

> **copracr said:**
> I'm typing from ubuntu thumb drive at work right now!
perfect, glad it's all working :)

---

