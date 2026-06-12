---
title: "[SOLVED] black screen and cursor only after kernel update"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by weezerisrock on 2008-12-08
Ok, I am still a beginner in Linux when it comes to certain things this being one of them...

I downloaded the latest updates not that long ago which included the 2.6.27-9 kernel.  Since that time when I boot into that kernel I get just a black screen with a blinking cursor.  After a while of waiting (the longest I have waited was 15 minutes) I hit ctrl-alt-del.  Then I get the message Gnome Display Manager is shutting down.

I have an ATI x1300 card in this laptop (HP nc6400) and had the latest drivers from ATI installed (8.11).  I'm assuming the problem may be in there and I may need to reset my xorg.conf?

I can go to the boot menu select the 2.6.27-7 kernel and boot into ubuntu just fine.  In fact that is where I am writing this post from.  So if anyone could give me some help and point me in the right direction I would appreciate it.  If you need any more info please let me know and I will include it.

Thanks in advance,
=w=

---

### Post by gn2 on 2008-12-08
Have you tried to boot the -9 kernel in Recovery Mode and take the Xfix option yet?

---

### Post by weezerisrock on 2008-12-08
Ok, I had thought I had done that but had not. :S

I now can boot to a console login, which I can also log into.  However, once I log in I try to run the command sudo startx and it tells me there was a Saw 11 error, and that it cannot find the command.

The -7 kernel still works, however my compiz no longer works. (I'm assuming this is due to running xfix under -9 recovery, yes?)

Thanks, 

=w=

---

### Post by gn2 on 2008-12-08
Have you tried to re-install compiz in -7 ?

Something else to try would be to select the -9 kernel line and press e at the Grub screen, then add ```
xforcevesa
``` to the boot entry.

This will force use of the vesa driver which hopefully will get it going, then re-install the ATI driver.

You have got a back-up of your /home on another drive.....?
(better safe than sorry)

---

### Post by weezerisrock on 2008-12-08
Thank you good sir!  Your last suggestion made it happen.  I appreciate your time!

---

### Post by snova on 2008-12-08
> **weezerisrock said:**
> I now can boot to a console login, which I can also log into.  However, once I log in I try to run the command sudo startx and it tells me there was a Saw 11 error, and that it cannot find the command.

For future reference, I do not believe sudo is necessary to run this command.

---

### Post by weezerisrock on 2008-12-09
Thank you for the info!  Also marked thread as solved

---

### Post by gn2 on 2008-12-09
> **weezerisrock said:**
> Thank you good sir!  Your last suggestion made it happen.  I appreciate your time!

Glad you're fixed up :)

---

