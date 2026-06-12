---
title: "Using Live CD To Recover"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by spikoley on 2009-07-26
My Jaunty install will not let me boot properly.  I am trying to back it up with the Live CD to a USB drive.  When trying to transfer files over I have permission issue.  Some files copy over fine, but other with permissions for the user do not.  I have tried using chmod and chown to change the permissions.

Any ideas?

---

### Post by marshmallow1304 on 2009-07-26
Try
```
gksudo nautilus
```

and copy from there.

---

### Post by spikoley on 2009-07-26
> **marshmallow1304 said:**
> Try
```
gksudo nautilus
```

and copy from there.

Tried that already and it did not work.  Also, I tried using Nautilus as root.

---

### Post by aysiu on 2009-07-26
Can you be more specific than *did not work*?

Did you get an error message of some kind? And did the message pop up while trying to launch Nautilus as root (which, by the way, is what the command *gksudo nautilus* does)? Or did the message show up while copying the files?

It's possible something is wrong with the flash drive.

---

### Post by s3a on 2009-07-26
Try:

sudo cp -r */home/username/Desktop/* /home/username/other_folder*

The two italic pieces of text are examples of two different directories (=locations). That command will copy paste every single file and folder from the first directory to the second if I am not mistaken.

---

### Post by spikoley on 2009-07-26
> **aysiu said:**
> Can you be more specific than *did not work*?

Did you get an error message of some kind? And did the message pop up while trying to launch Nautilus as root (which, by the way, is what the command *gksudo nautilus* does)? Or did the message show up while copying the files?

It's possible something is wrong with the flash drive.

This is the error I get when coping.  I am trying to move some .config files.

> The folder ".local" cannot be handled because you do not have permissions to read it.

The drive is fine, it transfers the other files.  It's a permissions issue.

> **s3a said:**
> Try:

sudo cp -r */home/username/Desktop/* /home/username/other_folder*

The two italic pieces of text are examples of two different directories (=locations). That command will copy paste every single file and folder from the first directory to the second if I am not mistaken.

Tried that command with sudo and under sudo -i.

I usually do this booted from the hard disk.  The problem is when I boot into the desktop I cannot use the keyboard and I am trying to back up before I tried to fix the issue.

---

### Post by spikoley on 2009-07-26
I got it fixed.  The solution was to copy the files to the Live CD desktop then copy them to the USB drive.  I have no idea why there was a permissions error copying from the hard drive to the USB drive directly.

---

