---
title: "Help Please - loading stuck @ fsck, then no access to drives"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by luckylucky on 2008-12-19
Please help.  

I don't know why but spontaneously after a crash booting my machine it stops at doing an fsck check.  I could let it sit there for hours but nothing is happening (no hard drive activity).  To bypass it I hold control & alt & delete, after which the computer boots up.  But then when it boots up I don't have access to my other drives, saying "Cannot mount volume.  You are not privileged to mount this volume."  I use my other drive as my primary storage space for my files, but now I'm effectively locked out.

Please help me to fix this.  I simply don't have any clues.

---

### Post by Michael.Godawski on 2008-12-19
> **luckylucky said:**
> Please help.  

I don't know why but spontaneously after a crash booting my machine it stops at doing an fsck check.  I could let it sit there for hours but nothing is happening (no hard drive activity).  To bypass it I hold control & alt & delete, after which the computer boots up.  But then when it boots up I don't have access to my other drives, saying "Cannot mount volume.  You are not privileged to mount this volume."  I use my other drive as my primary storage space for my files, but now I'm effectively locked out.

Please help me to fix this.  I simply don't have any clues.

First have a look at this guide how to access your drive from the Live CD. Perhaps you wanna to safe some of your files:

[http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)

But let's see what we can do...

If you are able to login into the normal ubuntu session (not the live session) run these commands and post the output please:

```
sudo fdisk -l
cat /etc/fstab
df -h
cat /boot/grub/menu.lst
```I can only guess because I cannot say what the crash you told about had caused to your machine.

---

### Post by ohzopants on 2008-12-19
Do you dual boot, by any chance?  I had this problem once when windows exited uncleanly.  The solution was to boot back into windows and shut down cleanly.

If not, you can always access a command line by hitting Ctrl-Alt-F1.  From there you can run fsck manually.  Check the man pages or the forum for which switches you should use to solve your problem.

Ubuntu will run an fsck check every 30(?) times the filesystem is mounted.  You can hit Esc to cancel it.

---

