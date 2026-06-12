---
title: "Lucid Lynx with crashing issue"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by HooDHunTeR007 on 2010-04-23
Hello, Im new to these forums and it took me nearly an hr to figure out how in the world i could post a new thread, so I hope this is being posted where it needs to be cause i have no clue hwo to tell.
i recently upgraded to 10.04beta from 8.04LTS, and it went fairly smoothly, but since i did this here are the issues i have noticed:

-compiz fusion lost over 50% of its features
-wine crashes while loading my WC III TFT game, but IF it loads gameplay is choppy and very poor FPS compared to my previous setup i had on 8.04LTS
-lettering on the borders of my firefox window among others seems pixelated
-canNOT reboot the kernel with control+alt+backspace anymore

aside from the lettering deal, the rest of these issues are important to me, and if its something im doing wrong here please let me know. i have ran wine in a virtual desktop and it does NOT lock up and the FPS is much better, but the game i play is unplayable in a window... it needs to be full screen or its un usable.
Also, if anyone could possibly tell me a (if there is any) easy way to just go back to the ay my PC was setup about a week ago, then i promise i wont make the mistake of trying out a beta version again. I loved 8.04LTS very much, but so far the only thing 10.04 can do without irritating me is surf the web. thank you for any feedback you have for me.

---

### Post by mick222 on 2010-04-23
Sounds like your graphics card is not supported anymore can you let us know what it is ? alt sys k restarts x .

---

### Post by Elfy on 2010-04-23
> compiz fusion lost over 50% of its features - which ones are gone that you need?

> canNOT reboot the kernel with control+alt+backspace anymore - System - Preferences - Keyboard Preferences - Layout tab - Options - key sequence to kill X server

> lettering on the borders of my firefox window among others seems pixelated - likely to be the graphics card - what card is it is the driver installed?
wine crashes while loading my WC III TFT game, but IF it loads gameplay is choppy and very poor FPS compared to my previous setup i had on 8.04LTS
> 
wine crashes while loading my WC III TFT game, but IF it loads gameplay is choppy and very poor FPS compared to my previous setup i had on 8.04LTS - never used wine so not sure - you could try renaming .wine to wine and starting again

> Also, if anyone could possibly tell me a (if there is any) easy way to just go back to the ay my PC was setup about a week agonot really - reinstall to go back

---

### Post by mick222 on 2010-04-23
> **forestpiskie said:**
> 

not really - reinstall to go back
 You could always back up your home partition then reinstall  backup using software like deju dup .Then restore it once you reinstall. Hardy is supported for another18 so no hurry to upgrade.
p.s. if you reinstall make a seperate home folder if you can.

---

### Post by HooDHunTeR007 on 2010-04-25
Nvidia 6800 series graphics card... i do like 8.04 i put alotta time into making it work for me, but im always loking for the newest thing out too. as far as compiz fusion goes, i lost most animations, expo no longer works, among other things missing in the main menu for advanced settings manager i never used and that just arent there. cant wait for the stable verson to be out... i think that might fix everything.

---

### Post by HooDHunTeR007 on 2010-04-26
ok so i verified the nvidia driver... it installed an update for the driver, and yet wine is still crashing... moreso now even. an available restore option for upgrading OS versions to go back to previous setups would be great in the future... i would highly recommend this, or at least for beta versions.
also i did change that setting in keyboard functions, and it does SOMTHING when i press ctrl+alt+backspace, but it goes to a black screen and just sits there. it does kill the X kernel... it just doesn't revive it. ill continue to play around with the graphics drivers to see if i find something that will work, and will keep you posted. If you have any suggestions for me regarding this issue it would be much appreciated. thanks.

---

### Post by clhsharky on 2010-04-26
HI HooDHunTeR007

A release upgrade sounds like its the easiest way but its not.
I can install and configure a release faster than upgrading and fixing any old config files that have issues with the new apps.
Up grade doesn't give you all that comes with a fresh install.
A lot of things have changed a great deal between 8.04 and 10.04.
Especially because of your customizing and configuring, afresh install will give you the most stability.

Sharky

---

### Post by HooDHunTeR007 on 2010-04-26
i was thinkin the same thing, and i just DL'ed a copy of 8.04LTS just in case the final 10.04 doesnt fix my wine issue. my wife is begging me to run my vista recovery disk instead... just dont want to though, but unfortunately it may be the easiest solution. once 10.04LTS final is out, i guess i will try the final version of that... if nogo, then hopefully i can find the time to put 8.04LTS back on and setup the way i prefer... if not the WIFE will kill me with trying to put vista back on herself... ARGH! lol. thanks for all your input. if there are no other answers to my questions, then close the thread.

---

### Post by clhsharky on 2010-04-26
HI 

you could duel boot

you both could be happy

Partition half and half and you store files on both sides, so you don't lose much space.

Sharky

---

