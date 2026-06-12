---
title: "Fsck failure x won't start"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by 11010110 on 2009-03-13
Hi everyone,

I made the mistake of running flightgear (a flight simulator) and compiz fusion at the same time. My graphics card obviously could not handle this and so the computer locked up and shut down. whenever I try and start it up again it runs through the fsck and tells me there is a failure and that it is starting a maininence shell and logs me in as root. when i hit ctrl alt del during the fsck it tells me that x cannot run and sends me to a terminal screen and asks for my log in. Ihave no idea how to circumvent this. 

Any help would be greatly appriciated. 
Thanks very much in advance.

---

### Post by martrn on 2009-03-13
> **11010110 said:**
> .... when i hit ctrl alt del during the fsck it tells me that x cannot run ... I have no idea how to circumvent this.  Any help would be greatly appriciated. 

fsck is checking your disk and recovering what has been lost or what part of the file system has been lost due to a system crash.  You need to run fsck to check your file system is intact and recover it, uncase there were any pending writes before it crash.

To circumvent being dropped at a terminal ensure you run fsck and do not interrupt it.

---

### Post by 11010110 on 2009-03-13
I do let it run and It says...
*checking root file system...
1075
Fsck 1.41.3 (12-oct-2008 )
/Lib/init/rw/rootdev contains a file system with errors, check forced.
/Lib/init/re/rootdev: unattached inode 286889

/lib/init/rw/rootdev: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
                (i.e., without -a or -p options)
Fsck died with exit status 4

{red colored}* an automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintinence mode with the root filesystem mounted in read only mode.
{green or orange (I'm colorblind)}* the root filesystem is currently mounted in read only mode.
A maintinence shell will now be started.
After performing system maintinence press CONTROL-D to terminate the maintinence shell and restart the system.
Bash: no job control in this shell
Root@ubuntu:~# _

This pops up every time... I am at a loss I have no idea what to do... Again any help is appriciated.

Thank you

---

### Post by taurus on 2009-03-13
At that prompt, run fsck of your root partition.  Assuming your root partition, /, is /dev/sda1, you would do something like

```
fsck /dev/sda1
```
And when that is all done, <Ctrl>d to restart your machine.

---

### Post by 11010110 on 2009-03-13
Ok I type in what u said and it tells me...

Fsck: fsck.ntfs: not found
Fsck: error 2 while executing fsck.ntfs for /dev/sda1
Root@ubuntu:~# _

What should I do now? Should I simply just type in fsck alone?

---

### Post by taurus on 2009-03-13
Did you install Ubuntu to /dev/sda1 because it looks like that partition is ntfs filesystem, not ext3?

When it said checking root filesystem when you boot, did it say which partition?

Not sure if this command work but see if you get any output from running it.

```
/sbin/fdisk -l
```

---

### Post by 11010110 on 2009-03-13
Nothing very helpful came out of that I'm sorry... I am running a wubi boot over windows if that helps... I typed in fsck at that point and it went thru passes 1 2 3 and then at 4 it said

4: checking reference counts
Unnatached inode 286889
Connect to /lost+found<y>?

I think I may have found something because inode 286889 came up before earlier. Or maybe my newbie mind is way off track...

---

### Post by martrn on 2009-03-13
See [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide") and see the section where it says How can I access my Wubi install and repair my install if it won't boot?

You might be able to the the ext2-disc-image file system from another copy of ubuntu. (such as the live CD).  Then again it might of shelf your webi file.

Whats it like running a file as a file system inside another file system ?

---

### Post by 11010110 on 2009-03-13
Thanks for the reply. I'll check that out right now and as for running one filesystem inside of another I haven't really had a problem until now .

---

### Post by 11010110 on 2009-03-16
Awesome! Everything is back up and running! its amazing how Ubuntu can just go in and fix itself like that. 

Thanks to martrn and taurus for helping me with this one!

---

