---
title: "liberal perms - escaping permission hell"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by LewRockwellFAN on 2010-04-08
I'm setting up a multiboot system with Ubuntu and Sabayon, both 32 and 64 bit versions, on two SATA drives and W2k on an IDE.  For data storage I have 2 FAT 32 partitions and one NTFS partitions on each of SATAs and will make 1 or 2 FATS and a NTFS on the IDE. Please, let's not get into "Why do you want to make it so complicated? Just do it MY way ..."

How can make it so I can read, write, delete, add, execute, or in general do anything I darn well please, with any of my data on any of my data partitions, no matter how I'm logged in? I'd like to have the same privileges on the partitions for the other OSs too, at least if I deliberately mount them, but I can live without that.

If I screw up, that is what partition images, data backup, and installation disks are for. I'm getting very frustrated with permission related "no, you can't do that" error messages. Just now Brasero refused to check the validity of a DVD against an md5 with the message:

"The file integrity check could not be performed.
You do not have the required permissions to use this drive."

My system is physically secure. I'm the only one that turns it on. All users are ME. I keep the plans for global conquest on another machine. If I wanted to be uberparanoid I'd install OpenBSD. I'm really missing DOS & 4dos right now.

Suggestions?

---

### Post by Steven_S on 2010-04-08
> **LewRockwellFAN said:**
> Suggestions?

Yes... Actually, I am bumping into the same set of problems because I have a dual boot XP / Ununtu (that works fine) and three ntfs storage disks (that causes trouble). The problem seems to be that - and I will quote:

"The NTFS filesystem does not support Linux permissions or ownership per se. You can't successfully change ownership with the Linux command chown and you can't successfully change permissions with the Linux command chmod. Ownership and permissions are set only in the mount command.

The permissions and ownership properties that are available for NTFS under Linux are not written into the individual files to be retained when the filesystem is unmounted or the computer is turned off. Permissions and ownership obtained under Linux are temporary artifices imposed via the mount command and maintained temporarily by the operating system. They are transient properties that last only until the NTFS partition is unmounted."

The same seems to go for FAT, but I can't tell you for sure because I have not looked into FAT permission issues myself.

This comes from [http://ubuntu.swerdna.org/index.html](http://ubuntu.swerdna.org/index.html), where there are some tutorials on the matter (also for FAT). They are quite detailed, so that you can understand what is going on exactly.

I would like to tell you that I have figured it out completely myself, but the truth is that I first need to understand, and then need to implement. Right now, my time-spending priorities are on other things. I'm quite confident though that the site I refer you to has everything you need to pin-point your own issues, and to hand you the solutions.

---

### Post by LewRockwellFAN on 2010-04-08
Steven_S:

Thanks. I'll study that link. It is my present understanding that setting or unsetting the read-only attribibute persistently in association with a particular file on a FAT is old hat for linux but that it can't be done with the present state of the art for NTFS files. I hope that is correct because I just went through days of work to change over the bulk of my files to FAT 32 partitions for that very reason.

---

### Post by LewRockwellFAN on 2010-04-08
The Brasero error message turns out to be a bug in Brasero. I did install MountManager but the support page isn't online atm and the options are fairly Greek. I marked some partitions "everyone" and that may have solved the problem or maybe it was already solved and I jumped to conclusions because of the Brasero message. Possibly all the permission problems I've ever had have been specific problems with specific programs and, because they are so common, I assumed they were fundamental to Linux itself.  I'm not sure. I need to do some experimenting. Not quite ready to mark this solved. If somebody wants to post a link to FSTAB FOR DUMMIES that'd be appreciated.

---

