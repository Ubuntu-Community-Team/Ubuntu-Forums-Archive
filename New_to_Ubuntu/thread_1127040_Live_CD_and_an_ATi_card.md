---
title: "Live CD and an ATi card"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by shakujou on 2009-04-16
I'm wanting to install the AMD64 version of Kubuntu on my computer, since I tried out Ubuntu a year or two ago on my old computer and loved it.  Now I want to give Kubuntu a try since KDE sounds like it would better suit me.  

My problem is that no matter how many times I try to boot the Live CD on my computer, it gets stuck trying to boot it up on my computer.  First I pick a language, then I select boot to Live CD (or whatever the first option is), I get past the loading bar, and then it freezes on the next step and gives me three lines of seemingly random tech related text.  It wont let me past this screen, and once I left it on for a few hours like that and it actually went completely blank.

Could it be a problem with the fact I'm using an ATi card?  This is partly why it's taken me so long to even try again, because I was afraid that the ATi card would hamper my efforts to use Linux.

My hardware is such:
Asus P5Q Pro P45 mobo
Intel Core 2 Duo E8200 @ 2.88 ghz (slight OC)
ATi Radeon HD4850
G. Skill 2gb PC8500 ram (plan to upgrade, which is why I want to use AMD64 version)
WD 320gb HDD

Could it be a problem with any of this information?

---

### Post by balaknair on 2009-04-16
If it's the ATI card, try using the 'safe graphics mode' in the LiveCD session. It will be low-resolution and not so pretty, but it usually works. Once you boot into safe mode, install K/Ubuntu, boot into the new install and install and activate the proprietary drivers(via System menu> Administration> Hardware Manager) and reboot. After rebooting, you can now change the resolution and use desktop effects.

Hope this helps.
All the best.

---

### Post by celthunder on 2009-04-16
I have a p5q motherboard with a q8300 with an ati hd4850 graphics card  and i am running kde/gnome/xfce just fine shouldn't be your graphics card.  You sure the cd works?

---

### Post by shakujou on 2009-04-16
Well, I ran the disc to see if there were any defects, and it turns our there were 3 or 4 of them. Since both of my live CDs stop at the same point, I'm assuming now that it's a problem with the way I'm burning the disc image.  That or it could be that for whatever reason, there's an error in the way I download the file.  Any known problems for people who use torrents to download the images?  I keep using that service since it's much faster than a direct download from a server.  

Since I've narrowed it down to a problem with my disc, can anyone recommend a program (Win XP) that can properly burn disc images?  I always seem to have a problem with using Nero.

---

### Post by stoer on 2009-04-16
Try imgburn, it's free and works.

[http://www.imgburn.com/](http://www.imgburn.com/)

(scroll down until you get under the advertising to find the download link).

Good luck

---

### Post by balaknair on 2009-04-16
Check the MD5 checksum to verify the downloaded CD image is accurate.
[http://www.softpedia.com/get/System/File-Management/MD5-Checker.shtml](http://www.softpedia.com/get/System/File-Management/MD5-Checker.shtml)

Try using a slower burn speed with Nero(higher speeds are more prone to errors). I'd recommend 4x-8x if you're repeatedly getting errors.

Alternate CD burning software for Windows(freeware)
_CDBurnerXP_
[http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/CDBurnerXP-Pro-beta.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/CDBurnerXP-Pro-beta.shtml)
_Ashampoo Burning Studio Free_
[http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Ashampoo-Burning-Studio-Free.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Ashampoo-Burning-Studio-Free.shtml)

---

### Post by shakujou on 2009-04-16
Well, I'm posting from the live CD right now.  Thanks for your help guys.  I've learned my lesson, never use Nero for image burning, even at 4x speed I still got the same errors.  

One more quick question though.  Would you recommend doing a disc cleanup and defrag on my XP partition first before installing Kubuntu completely?  I'm going to do a completely clean install later of both OSs, but I want to get the trial and error part of using Linux again before I setup a permanent configuration.

---

### Post by balaknair on 2009-04-16
> **shakujou said:**
> 
One more quick question though.  Would you recommend doing a disc cleanup and defrag on my XP partition first before installing Kubuntu completely?  I'm going to do a completely clean install later of both OSs, but I want to get the trial and error part of using Linux again before I setup a permanent configuration.

Yes, a disk clean up and defrag of XP would definitely be a good idea.

---

