---
title: "dual boot mac and ubuntu - and possible share folder?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by littlboz on 2010-05-28
Hi I want to dual boot ubuntu Karmic Koala 9.10 and my Macbook OS X. I feel pretty confident as I have already done this for my desktop, windows and ubuntu.

If there are any drastic things that I should know before doing this feel free to mention them but I have researched it and didn't find to many people with problems.

My main question though is can I create a share folder, or I guess a share partition? Just simply someway to share folders between my Mac operating system and my ubuntu operating system. I know that I would need different programs for each and what not but some files such as .odt files or .doc files would be nice to share.



[FONT="Arial Black"]Not necessary to read:[/FONT]
You might be wondering why I want to do this and my logical reason is that I want to learn both operating systems. My stronger and purely non-logical, emotional reason is that I love the video game Ultima Online and I just recently got back into video games and stopped playing WoW. Mac OS X can't install the stable version of wine (vs1.0.1) and it has to install the developing version. Razor, which I use to boot up UO will not run on the developing version. :-p

---

### Post by srs5694 on 2010-05-28
Yes, you can do this. I recommend non-journaled HFS+ for the job. (Ubuntu can't write to journaled HFS+ by default.) Note that you may have permissions issues, which you can overcome by setting appropriate ownership and permissions on the files and folders or by synchronizing your user IDs (UIDs) between OS X and Ubuntu.

---

