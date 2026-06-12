---
title: "Dangerous Nautilus file operations bug"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-19
Just wondering if anyone else has this issue.

If during a session, you force quit nautilus, it is possible to re-create this issue:

Start a file operation from nautilus (transfer a big file from one place to another), now closing nautilus will also cancel and close the file operation leading to potential data loss as most people expect the file operation to have continue on to completion. So if you closed you window and then deleted the file from its source, the file is now completely off your system as opposed to being in the target location.

Quite dangerous IMO

---

### Post by dnRoyston on 2009-01-19
First of all, if you're talking about using *xkill*, then I don't think that terminates the process, it simply closes the window. For example, in Xfce, there is no file operations menu, it just copies over and you have to look at the file size yourself.

Second of all, I think that what happens is that it copies over the file, then deletes the original. I could be wrong though.

---

### Post by mcduck on 2009-01-19
I wouldn't call it a bug that closing a program makes it stop whatever it was doing. Even less so if you *force* the program to stop.

The opposite, program *not stopping* when you close it, would be a bug.

---

### Post by Andy06 on 2009-01-19
I'm sorry I should have been more clear while explaining. It is indeed a bug (there is even a bug report on it but no resolution).

> 
I wouldn't call it a bug that closing a program makes it stop whatever it was doing. Even less so if you force the program to stop.

The opposite, program not stopping when you close it, would be a bug. 

Let me try again. I open a nautilus window and look through my videos located in an external hard drive, I now select a 1 GB files and select copy, then goto pictures in my local filesystem and hit paste. It starts copying. Now closing the file broswer window should NOT close the file operation as well. I understand the file operation terminating if I hit stop or terminated the operation itself but not if I close the file broswer window.

I also understand if it stops the operation if I Force Quit Nautilus, but I didn't. Force quitting a PREVIOUS nautilus window sometime during the session helps re create this problem. So basically this does not always happen, only when you have force quit a nautilus window sometime in the session (could be days back too). This then changes the future behaviour confirming buggy behaviour (since its an inconsistency).

Its very dangerous because it can cause a user to inadvertently lose data because the user will assume that the file operation is complete when he sees the file operation dialog disappear, if he then goes and deletes the file from where he copied it (assuming at this time that it is now safely in its target location), the file will be gone totally. Its not there now in the source or target. This "file" could potentially be ALL of your data or a little bit of critical data.

---

### Post by redseventyseven on 2009-01-19
I haven't experienced this myself - it behaves as it should on my system. But if it's something you can reproduce then please contribute to the bug reporting on launchpad.

It's good to see that you're enthusiastically contributing to the reporting of bugs, but I don't think *Absolute Beginners Talk* is the right place for this.

---

### Post by Andy06 on 2009-01-19
Will do, it's just that the community here is far far more helpful in finding solutions.

I've had a bad experience and seen others being frustrated at launchpad.

Furthermore, when people google for these issues, now they have a thread in ubuntuforums that will turn up as opposed to launchpad which no newbie will go within 10 miles of:)

---

### Post by bPawn on 2009-02-03
I can confirm it. It is CATASTROPHIC .-

copy a 3GB file from a window or tab of nautilus to another location (can be sftp also). The file operations progress bar pop ups. If I close the nautilus windows, poom! the progress bar disappears (also disappears from the taskbar icon). The file copy is terminated without notice.

This gives you the false impression that your copy has done and you can "safely" delete your original copy...

this exists at least from ubuntu 7.10 as far as I can remember.

---

### Post by afeasfaerw23231233 on 2009-07-12
Yes, I have just encountered this problem. I was copying a big file from samba. While I closed the nautilus windows the window of "file operations" also closed. But I thought it was copying so I left my room. Then I checked the gkrellm disk chart and found out there was no activity. This is dangerous. 

I don't remember it well but it seems that this bug didn't exist while it was in 7.04 - 8.04.

---

