---
title: "Ubuntu froze up, had to power down, now won't boot"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by swarup on 2009-12-18
I am on the phone with my friend in India, whose laptop has just experienced the problem indicated by this thread's title.

He has gutsy installed as a dual boot with Win XP. He was booted into Gutsy and was installing a new application using Wine, and the install was going fine. But then, while still in the middle of the install the computer froze up. At that point nothing worked except the screen's shut-down icon. So he clicked the icon, selected to shut down the computer, and the computer shut down normally. But since then, when he starts the computer, it goes to the grub screen just fine. If he selects Win XP, it boots fine. If he selects Gutsy, it gives the first two screens (starting..., etc), but then just yields a blank screen and doesn't boot. 

What is the solution? I have a feeling that at the grub screen if he selects "c" for command line, that some command can be given there which will repair the problem. But I don't know what the command is.

---

### Post by swarup on 2009-12-18
I had a [similar thing]("http://ubuntuforums.org/showthread.php?t=452738") happen to me two years ago. But at that time, although it would not boot up, still it was coming to a terminal window-type prompt (root@swarup-laptop:~#). That time, someone told me to type there "e2fsck -y /dev/hda2". I tried it, and it fixed the problem. But that terminal window-type prompt was different from the command prompt. We tried typing the same command at my friend's command prompt (grub>), and it did not accept the command. Does anyone know how to adapt the terminology of the command I gave two years ago, so it will work at my friend's command line? Or perhaps is something different needed?

---

