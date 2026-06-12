---
title: "Unclean shutdown, disc check, complete failure. URGENT."
date: 2009-07-02
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-07-02
Alright, my computer basically crashed. I rebooted it, and it was doing a disk check. It got to 15% and it gives me 

'/dev/sda1: Inodes that were part of a corrpt orphan linked list found

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
       (i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda1: 15% (stage 1/5, 254/1152)

* An automatic file system check (fsck) of the root filesystem failed.
A manual fsck should be performed in the maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently be mounted in read-only mode. 
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell'

I've got 'root@skeletor-laptop:~#' here flashing waiting to go. What the hell do I need to do to get this back??

---

### Post by oldos2er on 2009-07-02
Run **fsck /dev/sda1**

---

### Post by blairpeterson on 2009-07-21
I have a similar problem and after I run fsck/dev/sda1 I get "No such file or directory"
What do I do next?

My original problem started the other day when I went to log on and after loging on nothing happened. It just hung. Today it just shut down and when I restarted I got the following:

   Checking drive /dev/sdal:42% (stage 1/5, 693/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 694/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 695/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 696/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 697/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 698/1147)
  Checking drive /dev/sdal:42% (stage 1/5, 699/1147)
  Error reading block 22904905 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.
   
  /dev/sda1: UNEXPECTED INSCONSISTENCY; RUN fsck MANUALLY.
                  (i.e., without –a or –p options)
  Fsck died with exit status 4
   
  *An automatic file system check (fsck) of the root filesystem failed.
  A manual fsck must be performed, then the system restarted.
  The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
  *The root filesystem is currently mounted in read-only mode. 
  A maintenance shell will now be started.
  After performing system maintenance, press CONTROL-D
  To terminate the maintenance shell and restart the system.
  Bash: no job control in this shell
  root@blair;#

---

### Post by confused57 on 2009-07-22
You can run a filesystem check from the live cd:
[http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem](http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem)

You might want to copy & paste the commands, rather than trying to type them, just replace the example partition with the partition you want checked.

---

