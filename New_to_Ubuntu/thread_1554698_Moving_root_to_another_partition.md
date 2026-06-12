---
title: "Moving root to another partition"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Alan.Brown on 2010-08-17
I am running Ubuntu 10.04.

I created the root partition some time ago and it is now bursting at the seams.   I have a spare partition that is much larger.

How can I move the complete root partition to the other partition on the secondary hard drive without losing system integrity.   The system now works perfectly.

TIA

Alan

---

### Post by earthpigg on 2010-08-17
hrm...

i'm not positive. however, i wonder if you could compress the current root partition into a tarball, toss that onto the new partition, update grub, update fstab, and be done?

i suspect someone is going to pop in and point out some critical step i left out.

alternatively, i wonder if you could do some clever stuff with [remastersys]("http://www.geekconnection.org/remastersys/") in backup mode and restoring it? the .iso would potentially be huge, so i suppose you'd want to use an external hard drive and ubuntu's usb startup disk creator.

i'd definitely test either method in vbox prior to doing it live.

---

### Post by Gone fishing on 2010-08-17
If you copy all the files to the new partition it should work obviously you will need then to fix fstab and then fix grub from a start up disk. Remember however, if you copy over all the root files you will need to preserve all the permissions. You will need to use the -p switch whilst copying.

However, would it not be as easy to do a fresh install or are you running a complex configuration?

---

### Post by gandaran on 2010-08-17
have you cleaned the packages downloaded cache? if you haven't run the clean command, this will release a lot of root disk space back.
```
sudo apt-get clean
```

---

### Post by Alan.Brown on 2010-08-18
Hi gandaran

I ran apt-get clean and it released 600MB of space which will do for now - thanks for your replay.

Thanks to the other replies - I wont try your suggestions because I am afraid of losing the system and I am too lazy to do a re-install - thanks anyway.

Alan

---

