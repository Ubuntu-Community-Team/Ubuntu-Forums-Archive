---
title: "Floppy drive all of the sudden"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Kevin_a_b on 2010-11-13
I updated my system today and all of the sudden a floppy drive appeared in Computer. I opened the fstab file but no floppy drives appear. Why did this appear and how can I delete it?

---

### Post by Mike3 on 2010-11-21
Try looking around in /media. Do you see anything resembling a floppy folder there? If so, delete it, but make sure you're browsing Nautilus as root first:
```
gksu nautilus
```

---

### Post by Kevin_a_b on 2010-11-22
No, there's no floppy folder there. But when I open the Disk Utility, appears to be located at /dev/fd0. If I click on "Erase the contents of the device", an error pops out saying "Error creating file system: helper exited with exit code 1: cannot open device: Read-only file system", which I guess is because I'm not logged as a SU. Should I delete fd0 manually? how can I run the disk utility as a SU?

---

### Post by Mike3 on 2010-11-23
Before we do anything, try & make sure that this is an actual empty drive, not the system confusing it with another drive. To be on the safe side, open a terminal & input the following:
First to go to the directory of fd0 (Floppy Drive Zero):

```
cd /dev/fd0
```

Then type in the following command just to make sure there's nothing in it:

```
ls -a
```

If nothing shows up, then please continue. Just **do not** delete /dev/fd.

To answer your question, to get the disk utility running as root so that you won't run into file permission problems, enter in:

```
gksu palimpsest
```
NOTE: The command "gksu" will run an application as root with a GUI. 

On their there should be an option to unmount the floppy. (Bottom part of the windows with buttons, it's the top-left one). Unmount it, & then go to the bottom-right button & press "delete partition"

    An alternative option would be to use the terminal. It may work if all else fails. **Make sure you do it exactly right. You don't want to delete the wrong folder when doing a recursive (deletes folder contents) remove operation ****in the terminal!**:
```
sudo rm -rf /dev/fd0
```

This should solve your problem. Otherwise, I can continue on about possibley removing it from "/etc/fstab" so that it never attempts to mount a deleted partition on start-up later. I've had the mounting a deleted partition problem before, which indeed is a nuisance & it slows down boot-up time.

---

### Post by Kevin_a_b on 2010-11-23
I tried everything but nothing worked. cd /dev/fd0 returns "/dev/fd0 is not a directory", the Disk utility kept showing the same error--even as a SU--, and neither sudo rm -rf nor sudo rm -r did anything. Well, almost, sudo rm -r deleted it, but after restarting /dev/fd0 reappered.

---

### Post by Mike3 on 2010-11-24
Do you see any evidence of the floppy in GParted? There's a drop down list that may show a different location in /dev. Could have a floppy drive in it. First, try to unmount it. Then, attempt to delete it. Try to delete it or format it off through there. What if you type in:

```
sudo umount /dev/fd0
```

Does it unmount? If it does, then I may be actually getting on to the right track. I do have an idea for a work around...

Try this. Go to the menu bar. System>Preferences>Startup Applications.Click the "add" button. Type in a name such as "unmount fake floppy" Enter in the code:

```
sudo umount /dev/fd0
```

Press "add" again. Then create another. Enter in a description like "remove fake floppy". Type in the code:

```
sudo rm -r /dev/fd0
```

And then add that. I hope that at least hampers it until a fix is released.

---

### Post by oldfred on 2010-11-24
We have seen boot issues where BIOS showed a floppy drive when the system had no floppy drive. Some system updates seem to now follow BIOS where before they did not.

I would check BIOS and see if floppy is listed as a device.

---

### Post by Kevin_a_b on 2010-11-24
Yes, it was listed in BIOS. After disabling it, it stopped appearing. Thank you both.

---

