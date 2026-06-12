---
title: "memory stick wont mount"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by VickiM on 2010-12-29
[SIZE=5]Just installed Unbuntu netbook remix to Acer Aspire One netbook.  All went well, but I am unable to mount any of my flash drives.  It will auto mount my Jensen mp3 player, which I also use as a memory stick.  But all others show up in storage devices but when I click mount, I get an error code that says:  Error mounting: mount exited with exit code 1: helper failed with[/SIZE]: [SIZE=5]mount: according to mtab, /dev/ sda1 is already mounted on/ mount failed.    This is the same pendrive that I used to boot/installl ubuntu with.  It also works in my husbands windows machine.   Any ideas would be appreciated.  By the way, KISS (keep it simple st*p*d) as I am having a time getting used to navigating 10.10.  Other flash drives behave the same.  Thanks[/SIZE]

---

### Post by MoebusNet on 2010-12-29
This may or may not be relevant, but in Hardy Heron (8.04) after updates the desktop icon for CD's and thumb drives stopped showing up on the desktop. However if I went to Places>Computer from the taskbar, they would show up as drives in the Nautilus window that popped up. I could double-click on the thumb drive or CD to open it, and proceed from there. 

The message you get seems to say that your thumb drives are already mounted, so perhaps trying to access them from Places>Computer might work. Just right-click on the icon and choose Open.

Worth a try, anyway.

---

### Post by VickiM on 2010-12-29
[SIZE=4]the error message does seem to indicate that they are already mounted, but in disk services you can see the "properties" of the unit and they are NOT mounted, if I click to mount, that is when the error code appears.  Since posting, I have found that my camera does work also.  So it seems I can use media devices, just not plain vanilla memory????[/SIZE]

---

### Post by VickiM on 2011-01-04
[SIZE=4]so, i found that I needed to change my boot sequence back to HDD first, not usb.and i needed to have a login password for some reason.  Then if I boot the netbook with the stick in the usb it will find it and let me read/write to it.   [/SIZE]

---

### Post by ppv on 2011-01-04
The boot order of devices is unrelated with this...it is probably the reboot that solved it. Either you might have had a corrupted mtab or a missing mtab that would have been causing it.

---

### Post by nm_geo on 2011-01-04
> **VickiM said:**
> [SIZE=4]so, i found that I needed to change my boot sequence back to HDD first, not usb.and i needed to have a login password for some reason. Then if I boot the netbook with the stick in the usb it will find it and let me read/write to it. [/SIZE]
 
If you boot without a usb connected you will need the (password) because you are booting into the installed OS. It can be disabled if you are the only user. You should be able to keep the BIOS with USB, CD then HD normally (unless you have a usb or cd connected) it will default to the HD. 
 
I have caught myself many times with a USB still stuck in the machine when booting and that was not what I wanted.

---

