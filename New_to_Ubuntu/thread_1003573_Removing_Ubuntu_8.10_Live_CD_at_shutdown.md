---
title: "Removing Ubuntu 8.10 Live CD at shutdown"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by w5aack on 2008-12-06
I am running Ubuntu 8.10 as a "live CD", in other words, I have not installed Ubuntu to a hard drive but am booting from the Ubuntu CD by using the startup option "Try Ubuntu without any change to your computer."  

I am unable to remove the Ubuntu CD during shutdown and also when prompted by the message "Please remove the disc, close the tray (if any) and press ENTER to continue."  The CD tray opens but immediately shuts (maybe after 1/4 second).  Pushing the tray open button has no effect.  I have tried removing the CD prior to selecting Shutdown which does not work (and which I did not think would work) but only get the message "Cannot eject volume".  I am unable to open the CD tray at any time during Shutdown process and while booting Ubuntu from the CD, despite repeatedly pressing the open tray button.  

I did a CD integrity check and as I expected it reported "no errors".  

My workaround:  When I am finished using Ubuntu, I restart the computer with the CD still in the tray (since I could not remove it during Ubuntu shutdown) but I pick the option from the boot menu "Boot from the first hard disk."  I boot into Windows, get the login screen for Windows (but still cannot open the tray and remove the CD) and then log in into Windows.  After logging in I can remove the Ubuntu 8.10 CD.  

So for me this is a minor annoyance, and I offer the workaround in case any other newbies running with a live CD are having the same problem. 

I looked for postings on this problem in the Absolute Beginner Talk area of the forum, but could only find suggestions to use commands to eject/open the CD tray, but the suggestions seemed to be only for those that had previously installed the OS and were not trying to remove the live CD.  My guess is that there is no way to use a command to open the CD tray at the point during the shutdown process that you are seeing the message "Please remove the disc, close the tray (if any) and press ENTER to continue."  

Hope this info helps you if you are having the same problem as me.  Have a good day.

---

### Post by marshall.robert on 2008-12-06
I had this problem too, on a very very old cd drive.

But there is another way to open a cd drive.

On the cd drive there should be a really small hole, just big enough to fit the end of a paper clip, you can put a straightened paperclip into this hole and push, this will force the cd drive open.

You can now take the disc out and push the tray back in.

This will work regardless of the computer being on or off.

---

### Post by kansasnoob on 2008-12-06
That is a known bug. Once installed and updated the bug is fixed, but they've yet to incorporate it into the Live CD.

I always have to wait until the system just passes BIOS and hit the eject button to get the CD ejected. I know it's a pain.

Look at my post #7 here:

[http://ubuntuforums.org/showthread.php?t=934230](http://ubuntuforums.org/showthread.php?t=934230)

That was during testing! I keep hoping for a 8.10.1.

---

