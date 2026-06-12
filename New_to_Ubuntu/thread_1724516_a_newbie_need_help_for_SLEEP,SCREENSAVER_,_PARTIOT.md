---
title: "a newbie need help for SLEEP,SCREENSAVER , PARTIOTIONING PROBLEMS...Please!"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by mohammedhosen on 2011-04-08
hello every body and thanks for reading my post
i own ihave Acer Aspire one KAV10 intel atom 1.6ghz 1gb RAM 150 gb hd, runing both XP SP3 & UBUNTU netbook 10.10 ...
it was working very very nice for the last year...
until  3 days ago ...i suffered form " BLACK SCREEN SUDDENLY APPEARS ..like if its in sleep mode ...BUT NOT RESPONDING TO MY KEYBOARD ORDERS !!!
AND I ALSO oFOUND , that when i close the lid ...IT DOESNT GO TO SLEEP " although this option is checked in the "power management preferences" and it was working very fine in the previous versions of ubuntu ...
AND the screensaver...JUST WORK FINE ...BUT SHOW A BLANK SCREEN RATHER THAN THE USUAL IMAGES !!!
after searching ...i found a post with a bit similar problem ..and they suggest  INCREASING SWAP SIZE !!!
and i tried " using GPARTED " to reduce xp partition size ...BUT DIDNT KNOW HOW !!!

some says its a kernel issue or a bug ...
IAM REALLY FRUSTRATED AND DONT KNOW WHAT TO DO !!!!
ANY HELP IS APPRECIATED 
THANKS!

---

### Post by Paddy Landau on 2011-04-08
It seems unlikely indeed that this has anything to do with swap size. If your swap size is at least 1Gb, then I think we can rule that out.

*First question: How big is your swap size? (If you're not sure, open a terminal, type the command *[FONT=Courier New][SIZE=2]sudo parted --list[/SIZE][/FONT]* and post the results -- or just post a screenshot of GParted.)*

I could be wrong, but it sounds like a hardware issue has developed.

However, try this. When you power on your machine, you will get your usual menu asking whether you want to boot Windows or Ubuntu.

The default Ubuntu will be the latest kernel version. Just underneath that will be the recovery option. Just underneath that should be the previous kernel version for Ubuntu (well, it should be). Choose that one (press your down-arrow to select it and then press Enter).

Once you have booted into that, see whether it has gone back to normal. If it has, it's a kernel problem. If it has not, it's something else.

*Second question: What happens when you boot like this?*

I'm no expert on this, but if you answer both questions, I hope someone with more knowledge will pick up on this and help you.

---

### Post by mohammedhosen on 2011-04-08
thanks alot for answering me...
well...my swap is 2.3 gb ...which i think is  twice bigger than my RAM..
by the way sir..idont have this issue with windows xp sp3 ...BUT I HAVE THIS ISSUE ASLO WITH THE PREVIOUS KERNELS  " although they was working properly when i  was using them at their time !!!!....
thanks alot again for answering me

---

### Post by cmcanulty on 2011-04-08
Ace aspire ones can go black if the bios isn't updated in time.Many google posts. I caught mine in time just by accident reading about it.
[http://www.google.com/search?q=acer+black+screen+bios+update](http://www.google.com/search?q=acer+black+screen+bios+update)

---

