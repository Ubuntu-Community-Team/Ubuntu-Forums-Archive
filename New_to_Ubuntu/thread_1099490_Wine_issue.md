---
title: "Wine issue"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Bastun on 2009-03-18
Hi,

I have installed Wine and have managed to run a Windows app called Steganos MainLockNote (a simple encrypted file) without any problems. Setup a Program launcher on the desktop etc - all fine. However, I have tried to install a further two Windows apps and got various messages about files like MSCOMCT2.OCX, and  others, missing. I copied these as required from Windows Syystem32 folder on an XP box and pasted them into System32 folder in Wine. Finally I got to stage where Wine attempts to run the programs and am getting:

Runtime error 429. Active X component cant create object.

I have configured Wine as XP. There has been no probs running these progs on an XP box.

Any ideas?

Regards,

Bastun

---

### Post by 3rdalbum on 2009-03-18
Wine is not a perfect Windows compatibility layer. So much so, that I'd recommend you use Wine as an absolute last resort when you need a program that has no Linux equivilant.

Have you tried checking the Wine HQ site? They have a section called "AppDB" that tells you what works, what doesn't work, and what works with some tweaking. Look up your applications there and see what you can find; if they're not listed, then please add them to the list with your report.

---

### Post by Bastun on 2009-03-18
Thanks for that :D will follow up

---

