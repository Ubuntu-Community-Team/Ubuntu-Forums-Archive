---
title: "Grub rescue"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Tierehl on 2010-01-09
When starting my netbook (ASUS EEE PC 1005HAB) I hit somthing that looked like it was ment for starting windows xp but instend it told me that it would "ovewrite the disk are you sure you would like to continue?".     There was a button that said yes and a button that looked like a man running through an exit door so I clicked the man running. The computer restarted and now I am stuck at a screen that says 

GRUB loading.
Error: no such partition
grub rescue>

How do I get back to the normal boot screen. Thanks

---

### Post by Tierehl on 2010-01-09
Please help.

---

### Post by Linktwo on 2010-01-09
Sounds like you did a overwrite over that operative system....
did you run some diagnostics afterwards?
However this problem is for Windows... did you contact them?

---

### Post by Tierehl on 2010-01-09
I cannot do anything because the laptop is stuck there

---

### Post by charlier653 on 2010-01-09
You have a very short list of commands available from the grub rescue prompt. I cannot recall what they are right now, but mr google is your best friend here. search for a rescue command list, then try to repair your grub install from there.

---

### Post by mk1w86 on 2010-01-09
Type

```
help
```

at grub prompt for list of commands.

Your best bet would be to boot a Ubuntu live system from a USB flash drive or external CD-ROM so you can see what partitions are still on the machine (if any).  You can also reinstall grub from here if necessary.

Also I assume you are running Ubuntu on your Eeepc because grub is installed, if so what version of Ubuntu are you using. :-s

---

### Post by Tierehl on 2010-01-09
> **mk1w86 said:**
> Type

```
help
```

at grub prompt for list of commands.

Your best bet would be to boot a Ubuntu live system from a USB flash drive or external CD-ROM so you can see what partitions are still on the machine (if any).  You can also reinstall grub from here if necessary.

Also I assume you are running Ubuntu on your Eeepc because grub is installed, if so what version of Ubuntu are you using. :-s

I am running 9.10, I tried the help command and it said Unknown Command I do not have an external CD-ROM drive But I did use a USB how would I do a boot from that?

---

### Post by mk1w86 on 2010-01-09
> I tried the help command and it said Unknown Command

You might have to press tab twice or something. :confused:

With regards to creating a bootable flash drive there are many methods of doing it but this is a page on the Ubuntu website (although they don't look like the easiest of instructions to follow:|): 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

To boot the Eeepc from the flash drive on my Eeepc 701 you press ESC at boot which brings up a boot menu.  You then select your flash drive.

---

### Post by Tierehl on 2010-01-09
> **mk1w86 said:**
> You might have to press tab twice or something. :confused:

With regards to creating a bootable flash drive there are many methods of doing it but this is a page on the Ubuntu website (although they don't look like the easiest of instructions to follow:|): 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I have a bootable USB but I don't know how to boot it because when I start up the computer It goes stright to that screen I guess because it has somthing to do with dual booting

---

### Post by mk1w86 on 2010-01-09
You may not have seen my last post edit:

> To boot the Eeepc from the flash drive on my Eeepc 701 you press ESC at boot which brings up a boot menu. You then select your flash drive.

If that does not work you may have to change to boot order in the BIOS.  I think it is F2 you have to press to get in to it then F10 to save the changes you have made.

---

### Post by Tierehl on 2010-01-09
Ok, I have it booted and now I want to install but it is going to make me delete everything on here but I would like to dual boot with the xp that the computer came with.... What now?

---

### Post by mk1w86 on 2010-01-09
Could you please post the output of

```
sudo fdisk -l
```

so I can see what partitions are on your drive?  It may be possible reinstall grub without having to reinstall Ubuntu assuming you had a working Ubuntu installation before the boot problems. :)

---

### Post by Tierehl on 2010-01-09
> **mk1w86 said:**
> Could you please post the output of

```
sudo fdisk -l
```so I can see what partitions are on your drive?  It may be possible reinstall grub without having to reinstall Ubuntu assuming you had a working Ubuntu installation before the boot problems. :)
I finally got it to get back to dual booting, I had to delete the old ubuntu partitions so the new one would fit and Window XP is working fine :D thanks for your help

---

### Post by mk1w86 on 2010-01-09
Glad you got it working. :D

---

