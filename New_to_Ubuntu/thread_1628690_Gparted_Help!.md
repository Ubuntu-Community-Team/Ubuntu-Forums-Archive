---
title: "Gparted Help!"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by SomedayMorning on 2010-11-23
Okay- first post. Long time lurker + user. I'm having problems with Gparted. I'm trying to make my USB drive into an ext3- I already deleted everything on it and left it all unallocated and shiny. Here's the error it gave me trying to create a new partition.

Any Help is greatly appreciated! Thank you! :KS

PS- I set the partition table to msdos (the default) and I would prefer it to be ext 3. It's an 8 (7.5) GiB Sandisk Cruzer.

---

### Post by mikewhatever on 2010-11-23
Well, it obviously failed to create the ext3 file system, but doesn't seem to indicate why. Can you expand the last line as well and see what it says.

---

### Post by rkham11 on 2010-11-23
[COLOR=#ff0000]mkfs /dev/sdb1

[/COLOR]This command will format the flash drive to ext3 format which is the default.
assuming your usb drive is mounted in /dev/sdb1 you can find that out in GParted i think.

looking at your scrn shoot, it looks like this is how GParted does it, try the command and let us know if this works

---

### Post by SomedayMorning on 2010-11-23
> **mikewhatever said:**
> Well, it obviously failed to create the ext3 file system, but doesn't seem to indicate why. Can you expand the last line as well and see what it says.

It basically explains that it's mounted, so it 'will not make a file system here'.

I think after research that I need to turn automounting of storage devices off. Only problem being that I have no idea how to do that on Ubuntu Netbook Remix.

---

### Post by beew on 2010-11-23
You can unmounted it in gparted by right clicking the partition and choose unmount.

---

### Post by SomedayMorning on 2010-11-23
> **beew said:**
> You can unmounted it in gparted by right clicking the partition and choose unmount.

EDIT: wait- I seem to have done something correctly. I'm waiting and seeing while it seems to reformat it.

---

### Post by SomedayMorning on 2010-11-23
Alrighty- it formatted, but NOW every time I try to move files onto it I'm told that I don't have permission. Whoo hoo.

---

### Post by beew on 2010-11-23
Move file from where?

---

### Post by SomedayMorning on 2010-11-23
I want to move files from my desktop onto the new ext3 formatted drive. My brother uses slackware and he's gently trying to guide me through it, but he's a bit retarded with directions sometimes, so I accept other opinions. :)

---

### Post by Thorondir on 2010-11-23
correct me if i'm wrong, but i believe you need to be the owner of the device in order to do anything.

you could try the "chown" command.

```
sudo chown [your_username] /media/[name_of_device]
```

that should do the trick

---

### Post by beew on 2010-11-23
Well I don't see why he wouldn't be the owner in the first place. There is something wrong if he has to use the chown command.

@OP. how did you format the drive, did you use gparted or the command line with sudo?

---

### Post by Thorondir on 2010-11-23
true.

@Someday Morning:
did you run gparted as root?

EDIT: beew states more correctly :D

---

### Post by oldos2er on 2010-11-23
> **Thorondir said:**
> correct me if i'm wrong, but i believe you need to be the owner of the device in order to do anything.

you could try the "chown" command.

```
sudo chown [your_username] /media/[name_of_device]
```

that should do the trick

I would add the 'group' to that too: ```
sudo chown -R user:user /dev/sdb1
```

---

### Post by Thorondir on 2010-11-23
+1

didn't think of that.

[i'm the only user on this workstation so for me it doesn't matter :D]

---

