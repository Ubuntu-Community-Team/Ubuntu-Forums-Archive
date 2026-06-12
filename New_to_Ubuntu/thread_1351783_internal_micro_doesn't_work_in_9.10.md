---
title: "internal micro doesn't work in 9.10"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by newbeonlinux on 2009-12-10
Hello 
I just installed ubuntu 9.10 on my Acer Aspire One a110-Bp and the internal microphone is not working, neither on the sound recorder nor on Skype. Output is fine, but Input doesn't work at all.

lspci gives me:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Can somebody help? Pleeeeease!
Thanks in advance

---

### Post by Geoff918 on 2009-12-10
I'll take a quick stab. No guarantees...

Alt-F2 (box will appear)

Enter the following:

alsamixer (check the box that says Run In Terminal)

make sure your mixer levels are up for recording.

I hope that works for you and it's not more serious.

---

### Post by LeifAndersen on 2009-12-10
Okay, maybe this is a dumb suggestion, but it has bitten me in the but so many times, did you make sure that the level was all the way up?  Also, just as a reminder, just because a tab that says Microphone is turned on, does not mean that that tab actually controlled the mic you wanted.

---

