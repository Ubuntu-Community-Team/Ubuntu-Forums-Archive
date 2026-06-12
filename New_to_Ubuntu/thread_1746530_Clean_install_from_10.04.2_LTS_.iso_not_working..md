---
title: "Clean install from 10.04.2 LTS .iso not working."
date: 2011-05-01
forum: New to Ubuntu
---

### Post by e-hermit on 2011-05-01
Hi, been using Ubuntu just recently since 9.04 Jaunty as a NON-power user so need some "absolute beginner talk" help.
 
I have kept up-to-date with all upgrades since then and just recently had the new 11.04 working for me since the 1st day of release on my old spec Athlon XP desktop but prefer the speed and user-experience of the 10.04 LTS.
 
I've twice downloaded the .iso from ubuntu's download section and twice burned it at 4x for my burner speed (once yesterday and the 2nd time today) and it still won't clean install 10.04.02 for me. The initial screen to "try" or "install", etc. will get there if I press a key but once I actually try to run the options of "try ubuntu" or "install", it does some weird "command line stuff ala ms win xp" and I end up at what looks like to be ubuntu linux's version of the command line. It also does this "command line" stuff if I boot from install cd and don't press anything on the keyboard when the "ubuntu symbol background" shows up. I have to do a keypress to get to the "try ubuntu" "install" "mem test" "disk test" menu.
 
current specs:
athlonxp2500/512mb/80GB/radeon9600
clean installed both on 11.04 release day - dualboot:winxppro/ubuntu11.04
 
Are the "download section" and "mainpage" for 11.04 with 10.04.2 LTS option giving me a broken .iso image? because these are the two places I downloaded the 10.04.2 .iso from...
 
Please help, thanks. btw, I would really prefer to go back to 10.04.2, I haven't tried the option to have 11.04 run like 10.10... I feel at ease with the "LTS" factor of 10.04.2 and a clean install would be my preferred method.
Also, I haven't retried doing a fdisk and starting from scratch as I would prefer to keep my couple of days old install of winxp... I'm just trying to clean install 10.04.2 over 11.04 to save a bunch of wasted time from a winxp clean install scenario.

---

### Post by wolfen69 on 2011-05-01
Last time that happened, I just downloaded the alternate cd and it went well. Sometimes the live cd environment just doesn't work right. You can find the alternate cd here: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by e-hermit on 2011-05-02
:) Thanks so much wolfen69. That link to a working "alternative .iso" indirectly lead me to the simple solution. I'm so embarassed... I feel like a dunce.
 
Actually both "live" and the recent "alternative" .iso's were working fine from the get go.
 
The only problem was that during the bootup of the installation disk, I didn't set the F6 option to select "nomodeset" on either "Try out ubuntu" or the "install...". Had I done this part, I wouldn't have wasted a couple of days out of my life tinkering with my pc. HAHAHA.
 
The thing was, I was able to get 10.04.2 working with the "alternative" download but my install ended up logging into a "command line" version of ubuntu. Searched the web about it and tried "startx" as a solution but came out worse with a frozen blank screen.
Then after searching for a solution for that, I found out the 3-step process of F6 option to "nomodeset" which would've worked for with my "live" downloads. After the install completes and you restart, you need to press "shift" to pull up grub menu and press "e" to edit and delete "quiet" and that other word next to it(sorry closed the webpage and forgot to remember it). Then type in "nomodeset" in that spot you just deleted the two words from. Ctrl+x to reboot and FINALLY the ubuntu gui after selecting ubuntu on my dualboot menu. WHAT A RELIEF!!!
Oh the other part to the final step was for those with nvidia graphics cards... go to system and hardware drivers and update. I have an ati card and when I tried to update, came up empty handed.
 
MAN OH MAN!!!... whatta feelin' to see that GUI :)
 
BIG THANKS wolfen69, your help got me there.:KS:KS:KS:KS:KS

---

