---
title: "trying to open folders in &quot;Places&quot; requires GParted?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Phosphoric on 2009-12-28
I've just upgraded from 8.04 to 9.10 reusing my home partition.  The first job was to set up networking with Mrs Phosphoric's Vista laptop.  Failed badly there but in frigging around with Samba I have trashed my own installation.

I can no longer open any folders or drives from"Places".  I get an error message "Root privileges are required for running GParted"

I can open the folders normally from "Computer" but it's a pain and obviously not right.

I found a thread elsewhere that suggested right clicking on the folders and selecting open with Nautilus, but on clicking on Home, Desktop etc I still get the error message.

Any ideas please?

---

### Post by HarrisonNapper on 2009-12-29
Try adding a new user (from terminal: adduser) and using that user account. Sounds like you might have botched permissions (I have a lot of first-hand experience with that :)), so adding a new user should work. Keep in mind that not everything in your old home folder will work smoothly at that point and you might have to do some tweaking. The other option I'm thinking is just a fresh reinstall then rsync your homefolder when complete. If you don't want to do that just yet, there might be others with more experience who jump on the thread and make suggestions.

Cheers.

---

### Post by oldfred on 2009-12-29
Is home mounted correctly in fstab?

backup  your fstab 
sudo cp /etc/fstab /etc/fstab.backup

copy & paste from here
gksudo gedit  /etc/fstab

sudo mount -a
should come back with no errors

my home entry:
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0       2

---

### Post by Phosphoric on 2009-12-30
Hi Folks, thanks for the replies.

In my haste, I gave up trying to fix these problems and re-installed as I hadn't got very far anyway.

I saved my home directory elsewhere and am in the process of moving various bits back to the new home directory.  It's very laborious and fraught with problems but I'm slowly getting there.

---

### Post by HarrisonNapper on 2009-12-30
No worries. Though, as a general rule, if it's haste you're going for, I'd hold off on a complete reinstall :)

---

