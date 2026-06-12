---
title: "/host/ubuntu/disks/root.disk does not exist :("
date: 2009-01-16
forum: New to Ubuntu
---

### Post by pete-the-meat on 2009-01-16
Hi - a little bit of a saga here - I have a brand spanking new Advent 4213 netbook and, since it has no CD drive and I didn't have any appropriate USB media to make a starup disk with, I installed Ubuntu through Wubi and then followed the guide here: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) to use UNetBootIn and LVPM to move the install to it's own partition and remove the Window$ partition.
+ records in

It worked fine for about a day but now it won't boot and it seems that it's the menu.lst that's the problem. The UUID's are all wrong but I can edit these at the menu.lst screen pending a permanent edit once I can actually boot the damn thing, ()/ubuntu/disk also has to be replaced with (hd0,2).

The problem is w-fith the loop=/host/ubuntu/disks/root.disk line, which I'vfe never seen in a menu.lst before. When I boot it goes to the splash screen for a while and then drops to BusyBox.

There's an output of what the screen says below. I haveno idea what to do to get past this - please help!?!?!

```
Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/76993912-8b4b-4c64-a438-f99cb563f319) = dev(8,3)
kinit: trying to resume from /dev/disk/by-uuid/76993912-8b4b-4c64-a438-f99cb563f319
kinit: No resum image, doing normal boot...
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter 'help' for a list of built-in commands.

(intrafms)

```

---

### Post by abn91c on 2009-01-16
at the prompt type ```
exit
```then hit enter

---

### Post by pete-the-meat on 2009-01-16
just like magic - thx :)

---

### Post by Aiolos on 2010-10-25
> **abn91c said:**
> at the prompt type ```
exit
```then hit enter

"exit" ----> ENTER does not execute an exit for me.

In addition to 
   "Alert! /host/ubuntu/disks/root.disk does not exist." 

I see
   "Dropping to a shell! 
   "Busy Box v1.15.3 (ubuntu 1:1.15.3-lubuntu5) built-in shell (Ash)   (initramfs)"

The foregoing malfunction always occurs when I shift from Windows 2K to Ubuntu 10.10, which was installed by Wubi, but only about 1 boot attempt in 4 and unpredictably. Adapting the fix for malfunctioning Grub in 10.04, I have found copying wubldr from the Ubuntu partition to C:\ causes Ubuntu to boot properly.  Any ideas?

---

### Post by megatronous on 2010-12-12
```
ALERT! /host/ubuntu/disks/root.siak does not exist. Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

(initramfs)
```

same problem help required..................:(

---

### Post by kyral210 on 2011-02-18
> **megatronous said:**
> ```
ALERT! /host/ubuntu/disks/root.siak does not exist. Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

(initramfs)
```

same problem help required..................:(

I am having the same problem

---

### Post by Rubi1200 on 2011-02-18
Hi kyral210,
to help you with this we need more information.

Is Windows booting normally?

What version of Wubi are you using?

Can you boot the computer with either a LiveCD or LiveUSB?

Thanks.

(by the way, it would be better to start your own thread for this; the original is quite old. You can ask a moderator to move this to its own thread)

---

