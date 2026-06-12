---
title: "Routine Check of Drives [FAIL]"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by ecmatter on 2009-06-03
During Start up, the routine drive check hangs at 8%, and then gives the following:

> 

Error reading block 2326632 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck died with exit status 4
[FAIL]

*An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.

bash: no job control in this shell
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

root@abc-laptop:~#



Advice?  Should I run fsck from the prompt at the end of all of that, or [boot from a recovery disk and run fsck](http://www.linuxquestions.org/questions/linux-newbie-8/problem-every-start-up-routine-check-for-drive-errors-684410/#post3347883)?

What's the exact command I should use?  fsck /dev/sda1?

---

### Post by ecmatter on 2009-06-03
bump

---

### Post by ptsubin on 2009-06-03
When i got the problem, my system was not booting and i was just getting a busybox shell. So i booted from an ubuntu 9.04 live cd and used gparted to check the partition. After 2-3 failures, it fixed the filesystem.

---

### Post by ecmatter on 2009-06-04
I have no idea what I just did, but I did it anyway.  I ran fsck from the command line with the hard-drive in read-only mode and kept answering yes whenever it asked for permission to rewrite (40 or 50 times).

Everything seems to work, so I guess I fixed it.  Maybe.

---

### Post by hovzio on 2009-06-04
A good place to check out would be your lost+found folder\s. Somtimes when the hd messes up things will be put there. You will need root privledges to access these folders. (theres a lost and found for every partition)

---

