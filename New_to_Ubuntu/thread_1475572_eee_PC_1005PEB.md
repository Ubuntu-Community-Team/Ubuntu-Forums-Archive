---
title: "eee PC 1005PEB"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by emrooz.farda on 2010-05-07
I just purchased the new eee PC 1005PEB with Intel Atom 450 processor. The computer is replacing my old pre dual-core MAC laptop for college. I am required to have a laptop to take tests / quizes because my college is going completely paperless.

I have always wanted to transition to Ubuntu (Linux). It is my intention to run Ubuntu 10.4, with Open Office and Firefox / Google Chrome. I also need stable wifi access.

However, it seems I can't access my bios in order to partition my hard drive for the purposes of dual booting. F2 and Esc aren't working. I am seeing many issues with Netbooks running Ubuntu.

Has anyone successfully installed Ubuntu in the new PC 1005PEB with Intel Atom 450 processor. If so, can I get some guidance? I plan to dual boot until I am sure Ubuntu can meet my needs for the above listed applications. Any links to a Youtube tutorial would ROCK! Voice Skype is also an option as well.

Help a newbie!!

---

### Post by Paul T. on 2010-05-07
Hi,

I've installed Ubuntu on a Eeepc904 & a 900 with no probs, so if it works on these older models should be fine on your newer 1005.
Not sure how to solve your BIOS prob but you will probably find an answer on here:

[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

Paul.

---

### Post by bredman on 2010-05-07
Have a look at [http://ubuntuforums.org/showthread.php?t=1389772](http://ubuntuforums.org/showthread.php?t=1389772)

It looks like almost everything works if you use Ubuntu Netbook Remix (UNR) and use the latest firmware in the eee. A recent purchase might have the newest firmware already.

Good luck...

---

### Post by anaconda on 2010-05-07
hmm..
I have eee 1005P, and I also had some problems accessing BIOS. Those problems solved themselves, when I updated the bios.  (there is a preinstalled BIOS updater on the windows 7)

Even if you update the BIOS to the same version it already is, the BIOS settings will go back to normal, default settings (which are different than what they vere when you got the machine.) And with those settings you can access BIOS normally..

 
And I recommend you do dualboot, because sometimes the windows7 can be useful.. The HD is big enough. Just resize the windows partition from windows before you install ubuntu..

And by the way. if you make a separate swap partition, you will lose the Quick-boot linux system.. its partition number changes, and the Quick boot won't find its partition any longer. (actually the quick boot linux image is on your windows partition, but it needs something from the one small TEM? partition, which it wont find any longer if the number of partitions changes.. or something..)

PS. IMO normal ubuntu is better than the UNR... Netbook remix is just bigger version of ubuntu witn difficult to use interface. eg. the default thet all programs open fullscreen is really annoying, and in addition to that making them smaller is made difficult.. (but possible)

---

### Post by emrooz.farda on 2010-05-07
I heard about the bios updater on Windows 7.

But where the heck is it?!?!?!?

Emrooz

---

### Post by emrooz.farda on 2010-05-07
> **anaconda said:**
> hmm..
I have eee 1005P, and I also had some problems accessing BIOS. Those problems solved themselves, when I updated the bios.  (there is a preinstalled BIOS updater on the windows 7)

Even if you update the BIOS to the same version it already is, the BIOS settings will go back to normal, default settings (which are different than what they vere when you got the machine.) And with those settings you can access BIOS normally..

 
And I recommend you do dualboot, because sometimes the windows7 can be useful.. The HD is big enough. Just resize the windows partition from windows before you install ubuntu..

And by the way. if you make a separate swap partition, you will lose the Quick-boot linux system.. its partition number changes, and the Quick boot won't find its partition any longer. (actually the quick boot linux image is on your windows partition, but it needs something from the one small TEM? partition, which it wont find any longer if the number of partitions changes.. or something..)

PS. IMO normal ubuntu is better than the UNR... Netbook remix is just bigger version of ubuntu witn difficult to use interface. eg. the default thet all programs open fullscreen is really annoying, and in addition to that making them smaller is made difficult.. (but possible)

Will Normal Ubuntu run on a Netbook?

---

### Post by Paul T. on 2010-05-07
> **emrooz.farda said:**
> Will Normal Ubuntu run on a Netbook?

Yes ;)

---

### Post by 1360 on 2011-03-29
To access your BIOS on the 1005peb you have to use the quick boot (power button on the left), then when you reach the secondary OS select any of the options web,video,chat,etc. After making your selection a browser or chat or video player will appear ignore this and click the button with the power symbol on it on the bottom right corner of the screen, after clicking it a dialog will ask you if you want to "shut down" or "enter OS" or something like that. Select the "Enter OS" option, the machine will reboot and show the BIOS splash so be ready to make your selection. 

:D GLHF

FYI:
<F2> accesses BIOS, <ESC> accesses Boot menu, and <TAB> displays POST.

---

