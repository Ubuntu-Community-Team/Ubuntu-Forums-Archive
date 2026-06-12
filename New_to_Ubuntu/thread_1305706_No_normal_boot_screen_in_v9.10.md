---
title: "No normal boot screen in v9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by bandy on 2009-10-30
I have installed v.9.10 and it has been working well and impressed me, however the computer has now lost the normal boot screen leaving a command line type login instead.

Has anyone any suggestions to help rectify this please

---

### Post by ikt on 2009-10-30
> **bandy said:**
> I have installed v.9.10 and it has been working well and impressed me, however the computer has now lost the normal boot screen leaving a command line type login instead.

Has anyone any suggestions to help rectify this please

Are you able to type out some of the error messages that come before it or does it just leave you at the command line login?

---

### Post by Edg165 on 2009-10-30
I don't know if it's the same problem but after instalation ubuntu instead of booting straight into the os just ops for a command style prompt saying "press tab for available commands" and from there I'm lost, whenever I try to boot it says something like " no kernal slected".

---

### Post by bandy on 2009-10-30
Thanks for the question

There are no messages - just the command style log in screen

---

### Post by anewguy on 2009-10-30
Was this an upgrade or did you do an install?  It sounds to me like you just lost the video driver.  If it's asking for a log in, use your normal userid and password.

At the command prompt, type in the following and post the output back here:

lspci | grep VGA <press enter>

Dave :)

---

### Post by ranch hand on 2009-10-30
I would try booting to recovery mode first.  You should get a menu with options.

Pick the one having to do with broken packages.  When that is finished try "return to normal boot".

If that takes you to a terminal;
type <your user name> hit enter
type <your password> hit enter
type gdm start
type your pasword

If this does not take you to the normal login screen then I would try the video driver ordeal.

the reason for this is that the GDM is still new and still has some quirks.

---

### Post by bandy on 2009-10-30
The output of lspci show:


vga compatible controller: nVidia Corporation G73 [GeForce 7600GS] (reva1)

---

### Post by bandy on 2009-10-30
tried the repair broken padkages route but that didnt work

---

### Post by anewguy on 2009-10-30
Well, I still think it's the video driver, but here's the rub - I haven't gotten 9.10 installed yet, and I don't know if they changed any of the xorg stuff around or not, so for 9.10 I can't really say how to get your video driver going.  Hopefully someone more knowledgeable about xorg in 9.10 will see your post and help you out.

Sorry I couldn't be of more help!  I only have dialup so I am waiting for a CD before I can install 9.10.

Dave :)

---

### Post by anewguy on 2009-10-30
It might be worth checking the xorg log file for any errors.  *IF* that hasn't changed in 9.10, you could try the following:

cat /var/log/Xorg.0.log | more  (that's the piping symbol - it's about the "\" on my keyboard)

See if there are any three star errors or fatals in it.

Dave :)

---

### Post by bandy on 2009-10-30
thanks for the advice but Ican find no errors or changes to the file.

I'm beginning to think that if I can get a backup of some files I might just do a complete re-install.   Although doing that wouldn't really teach me anything

---

### Post by bandy on 2009-10-30
Thanks everyone for your help.

Needed to get the system working quickly so I did a complete re-install and all is well now.

---

### Post by ranch hand on 2009-10-30
Mark the thread as solved so folks know (under thread tools at top of page).

---

