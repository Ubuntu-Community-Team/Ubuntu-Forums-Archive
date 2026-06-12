---
title: "Wiping XP partition on a dual-boot"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by nathan28 on 2009-02-28
Since my 1.4 celeron laptop was getting long in the tooth, I bought a new one last night. What this means, though, is that now I have a machine that my fiancee can use to interface with the Windows world and i have an old one sitting idle, waiting for me to go all mad science.

The old one is a xp/ubuntu 8.10 dual-boot. I want to wipe the XP partitions out, and, ideally, install a three-partitioned / root, a /home and raise the size of the swap. Is there a way to do this reliably without re-installing linux? I'd like to retain the current configuration if possible. i'm willing to do command line jiu-jitsu

On edit, the hard disk is partitioned as:

/dev/sda1 ntfs (XP)
/dev/sda2 fat32 (the default windows backup partition)
/dev/sda3 extended to /dev/sda4 ext3 and /dev/sda5 linux-swap (600 meg)

---

### Post by Nielsoerbaek on 2009-02-28
Do you have an /home partition now?

If yes, then you could try [http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2) , though it is a re-install, but you can get stuff back to normal.

I did this without having a /home partition and just copied all the hidden files from my home folder into the new one, but it brought some less than entertaining problems. But you could easily just install all your packages again.

edit:
Ha! I'm good at reading posts, huh... You are welcome to ignore this.

---

