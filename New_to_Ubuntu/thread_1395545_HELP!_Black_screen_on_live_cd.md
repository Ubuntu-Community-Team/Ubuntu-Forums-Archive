---
title: "HELP! Black screen on live cd"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Gatesgamer33 on 2010-02-01
Whenever I go and boot to a live cd of ubuntu 9.10, I go and hit "Use without changes" It goes to a black screen. It is on an Intel GMA 4500MHD, and I have already tried to use the kernel option "nomodeset" with it only showing the Ubuntu logo afterwards. I REALLY need help on this, my mother is breathing down my neck. Any post is appreciated.

---

### Post by Gatesgamer33 on 2010-02-01
Could an admin delete my poll? Thanks. Also, I have installed the system via the alternate install cd, and the results are the same with grub.

---

### Post by cariboo on 2010-02-01
All I can do is close the poll, you'll have to wait for an admin to come along and remove it.

Have you tried starting the Live CD in safe graphics mode? Press F4 at the menu screen, select safe graphics mode, press enter then choose whatever option you want from the menu.

---

### Post by Gatesgamer33 on 2010-02-01
How exactly can I close the poll? Thank you. 
I have tried starting the computer in safe graphics mode, with no luck.

---

### Post by Gatesgamer33 on 2010-02-01
bump

---

### Post by Nebelhom on 2010-02-01
Before you do any of this, please read to the END.


Right, I'm not an expert on this, but the black screen happens to me each time I installed ubuntu (twice so far)

What I did to get the installation working is the following:

On the start up when you are asked to choose if you want to install it after testing ubuntu out first or straight away, you have the menu Options by pressing F6.

in there I had to switch off acpi=off, noapic and nolapic (I was told these measures are quite intrusive, but unfortunately I don't know what they mean). Also on the line below all your options there is a line of text you can edit by simply using the keyboard. There I removed the quiet splash bit, but I am not sure if that one is necessary (which is just the splash screen).

that way I was able to circumvent the blackscreen and install Ubuntu

BUT!

then I had the same problem in Ubuntu as such. I would boot up (I had a dual boot with XP) and it was a black screen again. I had to install the drivers for my NVidia drivers via the command line, which I can explain to you how to do if you have an nvidia graphics card, if not I am out of my waters and you best find a guide how to install your drivers from the command line just to be on the safe side.

And if you get past the black screen installation part, make sure you have still access to the internet to check with people who know their stuff on this (just in case), otherwise your stranded and up s**t creek ;)

using the commandline as a newbie is quite heavy as a start and almost made me stop trying ubuntu, so it really is important you know what to do.

---

### Post by pirlo89 on 2010-02-01
well, the way i see it, you have 2 options:

1-burn the cd again in the lowest speed possible.
2-you can select install ubuntu but before you hit the finish button (to install ubuntu),  you cancel the installation and the ubuntu desktop appears for you to use. 

P.S. :that happened to me when i burned the cd in high speed, i burned it again in low speed and now it works like a charm ! :)

---

### Post by ljpp on 2010-02-06
[QUOTE=pirlo89;8759542]well, the way i see it, you have 2 options:
[B]
1-burn the cd again in the lowest speed possible.[/B]
/QUOTE]

Would Linux community PLEASE stop spreading this bull. Burning at minimum speed on high speed media is likely to introduce pit smearing, which results in bad/lower quality burns. If you use 16x DVDs or higher, burn around 8-10x. If you use high speed CDs, reduce speed around -50%, but do not go to extremely slow speeds.

Chemicals of high speed medium is designed to work on high speeds, and going too low causes over exposure (depends on the drive of course).

---

