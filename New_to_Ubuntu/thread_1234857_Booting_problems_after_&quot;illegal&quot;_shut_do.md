---
title: "Booting problems after &quot;illegal&quot; shut down"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by OllieGab on 2009-08-08
Coming home after a 2 week holiday I discovered that my computer wouldn't boot up. It told me that the system hadn't shut down properly; which is likely as there were people here having access to the machine. 

The start up sequence told me it had come across a file system with errors and was going to check the disc (hard drive?).
After checking about 6% it stopped and told me I need to do a manual 'fsck'.
I did this, answered yes to all questions coming up, and finally re-booted.
This worked and my machine is back and behaving as before I went away.

Question 1.
How dangerous is it to just go ahead and carry out these suggested actions? I have no idea what I answered 'yes' to but as I was asked to do a manual fsck, I just did it without questioning anything.

Question 2.
Should a system totally stop to function just because someone turned the machine off without shutting it down 'the proper way'?

I don't miss Windows for a second but sometimes I just feel a bit weary when Ubuntu does things I don't really understand. I just want things to work!

---

### Post by Liolikas on 2009-08-08
> 
Question 1.
How dangerous is it to just go ahead and carry out these suggested actions? I have no idea what I answered 'yes' to but as I was asked to do a manual fsck, I just did it without questioning anything.

fsck just scan file system for errors and try to fix them.
Y is good option.

> 
Question 2.
Should a system totally stop to function just because someone turned the machine off without shutting it down 'the proper way'?

There is small risk this can happen both on windows and Linux.

---

### Post by mcduck on 2009-08-08
1. You really don't have much options except accepting them. But no, it's not usually dangerous, more like the opposite since fsck is *repairing* your filesystem.

Sometimes it might not be able to fully fix some file system issues, in that case fsck moves the fels into /lost+found, and you'll be able to check afterwards if there's anything important. Usually it's just some temporary files that you can safely delete anyway.

2. Any modern operating system made after the days of DOS might break if it's shut down incorrectly. This includes all Windows and Mac OS versions, so it's nothing special. That's why all operating systems have shutdown functions instead of just relying on the user to simply switch off the power button.

---

