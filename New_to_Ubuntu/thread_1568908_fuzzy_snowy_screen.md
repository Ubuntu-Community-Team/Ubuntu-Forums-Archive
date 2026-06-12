---
title: "fuzzy snowy screen"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by klive on 2010-09-06
Sept 5, 2010
I am new to ubuntu, but have been using debian on a couple of machines for around 4 years.

Today I bought a lenovo G555 with amd athlon II processor, of course with windows 7 installed.  

I thought I would try ubuntu instead of debian for a few reasons...easier time with installing F77 compiler being the one that springs to mind...

I burned the 32bit Ubuntu ISO disc on a home machine, inserted to new machine, powered and told the machine to check CD before HDD for further instruction.  All was well, crisp fonts were dispalyed on the screen and nothing was out of the oridinary. As soon as ubuntu started running though the screen became extremely hard to read.  Font was smeared, and it felt like the image was smeared and possibly updating at the wrong rate. Hazy diagonal blue lines are present in the bg.  

I tried a few simple things, changing screen resolutions (tried each of the three 16:9 options listed under  System>Preferences>Monitors...  no joy)  Tried changing refresh rate under same tab, but it turns out 60Hz is the only option on the drop down menu.

Did a bit of web reserach and found some posts relating to my xorg.conf file... in /etc/  which apparently doesn't exist by default in this version of Ubuntu (10.04).

*** N.B.  At this point in writting my post, I went over to the laptop to re-run through the steps I had taken, so I could document them for this post... I do not knwo at what point my screen cleared, but at some point it did... of course at that point I had been working for over an hour.. mostly modifying xorg.conf.

So I know the problem is fixable, ... i know i upgraded and updated during the effing around, but can't say for sure what is was that fixed the situation...

with a nice tidy looking display, i tried rebooting and was treated to a fuzzy looking display...
so, knowing that i somehow fixed it i tried rerunning all the commands I had tried previously... no joy

I tried dumping some of the text i had previously put in xorf.conf therein again and rebooted,,, but since it wasnt the right combo of text i wound up with no display at all... so i tried reinstalling ...  and repeating any and all commands I could think of that i tried... no LUCK.

bottom line...
i am pretty sure that it was my /etc/X11/xorg.conf that was the problem (initally there wasn't one, and i created one...) too bad i didn't record what was in the one when i had it working...
 P-lease help.

for the record, my graphics card is:
ATI mobility Raden HD 4200

-Klive

one more thing, the screen looks fine in windows which is configured at 60Hz refresh rate... and also looks fine in the bootloader menus... its just in ubuntu where its a mess...

---

### Post by klive on 2010-09-06
Ummm wow...
thats embarassing...
turns out if I go to System > Administration > Hardware Drivers, 

And select and install the driver, well, thats it, problem solved.  I am guessing I will sort out wireless the same way.

OK, well that'll be all for now.#-o#-o #-o

---

### Post by klive on 2010-09-06
Although in hindsight, it is interesting that it did work WITHOUT the driver by writting the right things into xorg.conf... im just sayin'...

---

### Post by mcduck on 2010-09-06
> **klive said:**
> Although in hindsight, it is interesting that it did work WITHOUT the driver by writting the right things into xorg.conf... im just sayin'...

It just used the opensource dirver instead of the graphics card manufacturer's driver.

The problem was just that the opensource driver doesn't yet have full support for all the new cards. If you had a bit older graphics card, like I do, you wouldn't need the proprietary driver at all (on the other and you couldn't even use the official driver, as AMD dropped support for all older cards in their own driver)

---

