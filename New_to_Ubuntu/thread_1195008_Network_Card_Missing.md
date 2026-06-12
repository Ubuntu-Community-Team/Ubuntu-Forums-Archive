---
title: "Network Card Missing"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by octotom on 2009-06-23
Recently, a technician came out to my place and hooked up my DSL connection.  I was stoked since the last few weeks I've had to use a 3G stick that they gave me and I was looking forward to actually being connected to the 'net with a real line!

After surfing around for a little bit, making sure that the DSL conneciton was working properly, I decided that I would install *buntu onto my machine.  I inserted the LiveCD, per normal, and checked to make sure that everything was compatible.  Sure enough, everything was.  So, I proceeded to install.

After the installation was finished, I noticed that I couldn't connect to the internet.  I couldn't connect via my 3G stick either because that is Windows only.  So, I eventually decided that I was going to need to reinstall Windows so that I could get back on the internet and search for a solution to my problem.

Once Windows was reinstalled, my DSL wouldn't work anymore.  I thought that this was pretty strange because it had just worked before.  I figured something must be wrong with the DSL box, as I was having problems with the phone also, and I decided to ask the technician when he came out again, which was yesterday.

The technician came and hooked his laptop up to my DSL box and it worked fine.  Then he looked through my computer, which was running XP again, and he said that Windows doesn't even have my network card listed as being in the computer.  He suggested that I reinstall XP again because, as he put it, "Windows may have 'forgotten it' when I was reinstalling it and such."

I reinstalled Windows again with no successful solution.

This is really strange to me because, in the matter of minutes, without doing anything, really, my computer "lost" the network card.  Though I know it's still in the computer!  What is kinda funny also is that, if I plug in my LAN line, sometimes my browsers homepage comes up and then I can go to maybe one other website but after that, I am told that I am in "Off line mode" or the connection can't be found.

Has a similar thing happened to anyone else?  Where can I start to try and rectify this?  Thanks in advance for your help!

---

### Post by starcraft.man on 2009-06-23
First question that pops into my head. Are you using an add on PCI network card instead of the integrated networking interface in your motherboard? I assume it's a recent card. That would explain both why it doesn't work in Ubuntu and XP. If so, just use the standard motherboard jack and you'll do fine.

On xp, go to the device manager (Run, devmgmt.msc). Look through your network interfaces section and can you just take a screenshot showing what's there. That would help. Once identified, you can find drivers at least for XP.

---

### Post by octotom on 2009-06-23
> **starcraft.man said:**
> First question that pops into my head. Are you using an add on PCI network card instead of the integrated networking interface in your motherboard? I assume it's a recent card.
To be honest, I'm not sure.  When I peer down through the vents, in the spot where the slot is where I would plug the LAN line in [on the inside of course], there is a silverish box box that is connected to what I think is the mother board.

> On xp, go to the device manager (Run, devmgmt.msc). Look through your network interfaces section and can you just take a screenshot showing what's there. That would help. Once identified, you can find drivers at least for XP.
Since my computer is in German, I hope I took a screenshot of the right opened section!  If not, I can try again.

ETA:  Since it doesn't seem that my computer is picking up the card, wouldn't that mean that my NIC may not show up in the Device Manager?  Also, something I neglected to mention before is that when I plug in the LAN line, the green lights turn on, so I know that a connection of some sort is made.  Maybe that will be useful too.

---

### Post by halitech on 2009-06-23
do you have a cd that came with the computer that has drivers on it? Looks to me (not that I undersand german but the icons for each item) that the network card is not installed software wise.

---

### Post by starcraft.man on 2009-06-23
> **octotom said:**
> To be honest, I'm not sure.  When I peer down through the vents, in the spot where the slot is where I would plug the LAN line in [on the inside of course], there is a silverish box box that is connected to what I think is the mother board.



[http://visual.merriam-webster.com/images/communications/office-automation/personal-computer/tower-case-back-view.jpg](http://visual.merriam-webster.com/images/communications/office-automation/personal-computer/tower-case-back-view.jpg)

Take note of picture. This is fairly universal layout. If you plug into the vertical rectangle in the middle right, all of those are integrated into the motherboard and should work. If you plug into anything in the horizontal slots underneath that part, those are expansion cards. Those would require separate installable drivers, they usually come on a CD with the NIC.

As to the pic, see my attachment (underlined missing section), I concur with Hali. That is the section you are entirely missing, not having it in your pic means that neither the integrated or a NIC (if you have) is installed. You need to consult the OEM manufacturer site/disc (if you bought your PC) or if you build it find the drivers disc/download from the makers site.

---

### Post by octotom on 2009-06-23
> **halitech said:**
> do you have a cd that came with the computer that has drivers on it? Looks to me (not that I undersand german but the icons for each item) that the network card is not installed software wise.

No, I don't have a drivers CD.  When I bought this computer, there was a window that popped up that said to burn a DVD so that in case Windows needed to be reinstalled, it could be returned back to the original settings.

Perhaps I should try reburning the DVD?  Maybe when it burned last time, it didn't do it right.  Or if I were to try reburning it again, would it just be a waste of time since the driver software isn't installed to begin with?

---

### Post by octotom on 2009-06-23
> **starcraft.man said:**
> If you plug into the vertical rectangle in the middle right, all of those are integrated into the motherboard and should work. If you plug into anything in the horizontal slots underneath that part, those are expansion cards.
It appears that everything on the back of my tower is integrated into the motherboard.  It looks like there is only one expansion slot and there is nothing in that.

> You need to consult the OEM manufacturer site/disc (if you bought your PC) or if you build it find the drivers disc/download from the makers site.
I think I'll try looking on the manufacturers site.  Maybe there will be something there.

---

### Post by scrooge_74 on 2009-06-23
Most ethernet cards are discover by the live cd, you should try using it again, it has a couple of items that will let you see which hardware you have

---

### Post by octotom on 2009-06-23
So the funniest thing just happened.  My the ethernet/LAN started to work.  I went to my computer's manufacturer's website and downloaded the driver and it started to work.

The funny thing is that I'd tried this last night but it didn't change anything.  I guess what matters though is that this is working [finally!].

Thanks a ton for your help guys [gals?]!

---

### Post by LewRockwell on 2009-06-23
and now that you're back to the functioning where you started are you going to try linux again?

it would seem that your computer's motherboard has everything integrated so if everything works in live-run then it should work after being installed to the hard drive

I'd offer more commentary and specific direction/advice except we haven't been given your equipment specific information

---

### Post by octotom on 2009-06-23
[QUOTE=LewRockwell;7504929]and now that you're back to the functioning where you started are you going to try linux again?/QUOTE]

I certainly hope so!  I probably will, though.  I used to use Linux a few years ago, until my computer had problems with the power supply.  I only recently was able to get a new one and even more recently internet again.

I just hope that once I try again, that this doesn't happen again!  Maybe it was just a fluke.

What specs would you like to see for my computer?  I'd like to hear your advice as to which distro would work best.

---

### Post by LewRockwell on 2009-06-23
see below

---

### Post by octotom on 2009-06-23
**make, model/build number**:  Olidata, "Alabama"

**installed OSes**:XP Home Service Pack 3

**additional software**:None, other than Firefox.

**accessories/customizations/modifications/peripherals**:  Processor:  Intel Atom (2x) 230 @ 1.6 GHz
DVD/CD-ROM:  TSSTcorp CDDVDW SH-S223F
Graphics Card:  Intel 82945G Express Chipset Family
NIC:  Realtek RTL8102E Family PCI-E Fast Ethernet NIC

I hope that works.  If I missed something important, let me know.

---

### Post by LewRockwell on 2009-06-23
> **octotom said:**
> **make, model/build number**:  Olidata, "Alabama"

**installed OSes**:XP Home Service Pack 3

**additional software**:None, other than Firefox.

**accessories/customizations/modifications/peripherals**:  Processor:  Intel Atom (2x) 230 @ 1.6 GHz
DVD/CD-ROM:  TSSTcorp CDDVDW SH-S223F
Graphics Card:  Intel 82945G Express Chipset Family
NIC:  Realtek RTL8102E Family PCI-E Fast Ethernet NIC

I hope that works.  If I missed something important, let me know.

http://www.chl.it/articoli/p117996-18248859/Olidata_Alabama_Hm_1971.html

looks like some of those came with Ubuntu 8.04 on them so you should be ok with that

---

### Post by octotom on 2009-06-23
Thanks!

---

