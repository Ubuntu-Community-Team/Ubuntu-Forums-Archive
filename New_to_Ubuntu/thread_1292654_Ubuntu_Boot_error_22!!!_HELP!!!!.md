---
title: "Ubuntu Boot error 22!!! HELP!!!!"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by ratman1 on 2009-10-16
Hi,

I am REALLY new to linux so please be 'basic' with me...
okay, this is the problem:

I have a windows vista and windows 7 rc1 32bit dual boot on my laptops hard drive, each on a separate partition. I tried to install ubuntu 9.04 on my 500gb portable external hard drive and all went well. It installed fine but it seems to have moved the boot loader or something onto the portable hd because i can only boot if the portable hd is plugged in. If it isn't it says

"Loading grub stage 1.5"
"error 22"

All i want to do is get rid of ubuntu 9.04 without breaking my computer because i know enough that if i delete the partition on my phd i will lose the grub thingy and nothing will boot.


Thanks in advance,
Ratman

---

### Post by wobin77 on 2009-10-16
This would help. Restore Grub.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikechant on 2009-10-16
> This would help. Restore Grub.

They don't want to restore grub. They want to get rid of Ubuntu/grub and just be left with windows booting without grub.

I've read various posts about restoring the mbr to a normal windows one using the windows recovery console (if you have a suitable recovery disc) or using non-windows utilities. But this is not something I've ever done myself and there are various warnings associated with some of the methods like 'this doesn't work with vista' so I'll leave it to someone who has (hopefully) actually restored a Vista mbr sucessfully to advise on the best method!

---

### Post by wobin77 on 2009-10-16
Indeed, but grub can also boot windows... 
For fixing the mbr, use a vista/xp dvd. From there go to repair (or simular). 
When in command prompt just type 'fixmbr'

---

### Post by ratman1 on 2009-10-16
> **mikechant said:**
> They don't want to restore grub. They want to get rid of Ubuntu/grub and just be left with windows booting without grub.

Yeah, that's right. Thanks:grin:

---

### Post by ratman1 on 2009-10-16
> **wobin77 said:**
> Indeed, but grub can also boot windows... 
For fixing the mbr, use a vista/xp dvd. From there go to repair (or simular). 
When in command prompt just type 'fixmbr'

what will fixing the mbr do? all i want is to get ubuntu fully off my portable hard drive as well as the grub.

I now have supergrub thing and a vista recovery disk.

---

### Post by AliSajidImami on 2009-10-16
> **ratman1 said:**
> what will fixing the mbr do? all i want is to get ubuntu fully off my portable hard drive as well as the grub.

I now have supergrub thing and a vista recovery disk.
If you run the "FIXMBR" command, it will set the MBR to correct setting for windows. After that, GRUB will load if it is there, otherwise it'll just boot normally.

---

### Post by Niko Johnson on 2009-10-16
maybe this will help ```
 sudo grub-reinstall 
``` i dont know if that will even work im just throwing it out there.. i may be wrong but i do know that grub-install works... so i kinda makes since.

---

### Post by nexes128 on 2009-10-16
if you have a windows recovery disc (windows XP I am not too sure about vista) you can just boot into the recovery console and do the following:

```
fdisk /mbr
```

this will wipe grub from the master boot record and should rest the windows bootloader

---

### Post by ratman1 on 2009-10-16
> **AliSajidImami said:**
> If you run the "FIXMBR" command, it will set the MBR to correct setting for windows. After that, GRUB will load if it is there, otherwise it'll just boot normally.

YES!!! That is what i *tried* to do!! Thanks for pointing that out!!:grin:

---

