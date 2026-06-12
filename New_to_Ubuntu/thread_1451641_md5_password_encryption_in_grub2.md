---
title: "md5 password encryption in grub2?"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Tidus0515 on 2010-04-10
Hello! I am running grub 1.97 beta 4 with 9.10 karmic. I have a mutliboot usb that is running grub4dos and I have it protected with a generated md5 encrypted password for the usb grub4dos. However, when I use this same encryption code for my grub 2 header_00 and update-grub....it does not work. I messed up my password and had to boot a live cd to force edit the grub.cfg (even though we are not supposed too I know!) in order to revert my password. So..i guess my question is how does one use md5 encryption with grub 2? Is it different from the legacy and grub4dos versions? I cannot figure it out. In the meantime I reverted to the revealing text entry...

---

### Post by Didius Falco on 2010-04-10
Have a look at this **Grub 2 Password Protection guide**:

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

Regards,

Didius

---

### Post by Tidus0515 on 2010-04-10
> **Didius Falco said:**
> Have a look at this **Grub 2 Password Protection guide**:

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

Regards,

Didius
This is still very vague......confused....

---

### Post by Didius Falco on 2010-04-11
Then you should ask specific questions for others to answer. I'd suggest you mark this thread as solved and post your questions to the linked thread - that way you're more likely to get help from people who have done the same thing already.

I still haven't made the jump to Grub 2, so I've no actual experience, I'd just ran across that tutorial and thought I'd pass along the link.

Regards,

Didius

---

