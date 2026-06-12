---
title: "Unclean shutdown, checking drives"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by paul2009 on 2009-03-16
I'm new to Ubuntu, and new to these forums. Thanks in advance to anybody who can help me! I seem to have several problems in one - all of them have been raised in other threads but none of the solutions seem to work for me.

This morning my machine hung, and after some frustration I rebooted by removing the battery. Now, when I boot up, I get the message "unclean shutdown, checking drives". The check hits 70%, stops, and  then after around 5 minutes it goes into a check. The check runs, but returns an error message along these lines:

> Unexpected inconsistency. Run fsck manually
> fcsk died with exit status 4
> A maintenance shell will now be started.
> bash: no job control in this shell

and then I get a command line prompt.

If I hit CTRL+ALT+DEL at any point, I get the message "Could not start the X server (your graphical environment) due to some internal error." etc. I then get the command line prompt again.

I have tried a number of things - using the recovery menu to xfix, check disk and so forth; run fsck manually; run badblock (nothing found); used grub to poke around - but nothing works.

EXCEPT:

Twice in this process, when I rebooted, I was able to log in to my profile. However once on the desktop, I was unable to open any documents - the program shells would open but none of the menus or the content was visible. I could open Nautilus and all the data was still there (which is a small mercy); and I was able to shut the computer down again. Booting up - same story,

Does anybody have any ideas as to a) what has happened and b) what the solution is? I am going to try working from a CD boot and see if I can break the back of this, but any other suggestions are welcome.

---

### Post by philinux on 2009-03-16
Reboot and let it get to the command line.

Then use this command

```
fsck -v
```

If it offers to fix any broken files etc etc choose Yes.

For future reference use this next time.
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

---

### Post by paul2009 on 2009-03-18
Philinux - thanks for the quick response. Fsck was one of the first things that I tried when I worked out things weren't right: however it returns the following message:

/dev/sda3 contains a file system wth errors, check forced.
Pass 1: Checking inodes, blocks and sizes

And then - nothing much happens. I've waited around for nearly 20 minutes, but nada. How long should I wait before giving up?

---

### Post by paul2009 on 2009-03-18
Ah. I ran it again just now, and now have a list of Multiply-claimed blocks. I'll see what happens and then report back to this thread. Thanks!

---

### Post by paul2009 on 2009-03-18
Successfully went through checking everything "yes" (after backing up all my data, of course). Now have a message:

FILE SYSTEM WAS MODIFIED
REBOOT LINUX

Rebooted Linux, and booted as usual - no "Unclean shutdown" noted, and I appear to be back in the system with only a few minor problems.

Philinux, thanks for the advice. Will partitioning my drive also help to deal with this sort of thing in future?

---

### Post by philinux on 2009-03-18
> **paul2009 said:**
> Successfully went through checking everything "yes" (after backing up all my data, of course). Now have a message:

FILE SYSTEM WAS MODIFIED
REBOOT LINUX

Rebooted Linux, and booted as usual - no "Unclean shutdown" noted, and I appear to be back in the system with only a few minor problems.

Philinux, thanks for the advice. Will partitioning my drive also help to deal with this sort of thing in future?

Good job. I had this problem a while back on feisty. fsck on it's own seemed to just report without fixing. Thats when I used fsck -v.

Partitions wont make any diff. Hard shutdowns are to be avoided same as on windows. Modern OS's dont like it. Dont forget the REISUB method. That being said I have three. /, /swap and /home. Makes reinstalling a doddle.

---

