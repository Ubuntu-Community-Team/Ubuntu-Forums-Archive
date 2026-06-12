---
title: "can't boot from cd"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by qjmoss on 2009-06-19
I've recently decided to install windows onto my computer, I followed this Vista install disk instructions and it failed to format my hard drive half way through. So for about a week i was stuck with Grub bootloader error 17. I got upset and put my laptop in my closet :mad:     But today i realized i could probably just use Unetbootin and make a install point from my usb drive.   it worked. I currently am running Kubuntu.  but the problem is still here.  When I put my windows vista install disk in, it doesnt read.  It sounds like its doing something.. but it goes right to grub.  

Now, before you say theres something wrong with my install disk. I've made different ISO disks and tried to have them boot also. No luck.


now, before you say to check my Bios. I did, and I set my cd rom to boot first.

=)
No luck.


does anyone have any idea what could be going on =/

---

### Post by starcraft.man on 2009-06-19
Ok. That's peculiar. The first thing that popped into my head is your drive failed (not so common but does happen). Only thing I can think of if it's recognized by the BIOS and not booting ANY bootable media. 

To test, do you happen to have an old CD/DVD drive lying around? Just pull out the plugs to the current one and attach to the old one. Not very hard to do. If the problem persists, report back and maybe someone knows.

I know you said you looked, but I'd check one more time bios options. Another thought, instead of relying on boot priority, select the CD drive manaully, most computers have a "hit F12 to select boot media" type screen.

If no help, post back.

---

### Post by qjmoss on 2009-06-19
Messed around with bios for awhile.. 


Got this output

PXE-E61-Media test failure, check cable
PXE-M0F-exiting PXE rom

hm.

---

### Post by starcraft.man on 2009-06-19
Can you check if the cable is firmly inserted at the back of the drive? Both power and the Sata or IDE cables. Ideally, testing with another known working DVD drive would rule out hardware failure entirely.

---

### Post by qjmoss on 2009-06-19
I would have to take my laptop apart.

I'm not very experienced with doing that, I don't want to have that one corner that doesnt go back together and just squeeks and moves when i type ; )


Is there some way I can see if it's working properly via terminal.  

hm.  

I'd rather not rip my notebook apart =)

---

### Post by qjmoss on 2009-06-20
bump

---

### Post by LewRockwell on 2009-06-20
I'm absolutely positive many here would enjoy assisting you but we're a little shy on information and most folks just can't think of anything to recommend when they don't have much information to go on.

Let's start from the top. You'll give us the make, model/build number, installed operating system(s), and any other modifications/additions/software/peripherals/accessories/etc (regardless of there apparent relevance, or lack thereof).

Then we'll need information like which OSes run and which don't, internet connection(s) wired/wifi/wireless, and what(if anything) you've already attempted and how that's worked out.

So my first question is does your optical drive read/write ANY disks? If not, did this occur during your attempt to use the Vista disk or after(or was it possible to ascertain that?).

---

### Post by LewRockwell on 2009-06-20
And while we're waiting on that information we'll consider a few troubleshooting tips for future folks reading this thread.

First we'll do a cold boot or two and take note of any start-up and/or shut-down messages that we don't normally see.(a cold boot is a start initiated via the actual physical switch/button as opposed to a warm boot which is initiated through the software and usually found as "reboot/restart" on your shut-down menu)

Then, if necessary, we'll go to our BIOS settings and make sure everything is good-to-go there. If you are having doubts about whether a drive(optical and/or hard-drive) is being recognized properly at start-up you can check to see what your BIOS is reporting for that particular drive. Visiting your BIOS settings(and becoming familiar with them) may very well assist you in troubleshooting future difficulties with other accessories/hardware/peripherals as well.

---

### Post by starcraft.man on 2009-06-20
> **qjmoss said:**
> I would have to take my laptop apart.

I'm not very experienced with doing that, I don't want to have that one corner that doesnt go back together and just squeeks and moves when i type ; )


Is there some way I can see if it's working properly via terminal.  

hm.  

I'd rather not rip my notebook apart =)

Sorry, kinda glossed over the fact that it was a notebook and not a desktop. Answer rockwell's requests for information.

I did a quick google on the PXE error your getting and it isn't uncommon but does seem to have numerous possible sources and fixes (it's a generic error). From what I've gathered from my reading (and I preface it by stating I've never had any experience with this problem before) these are the possible problems:
- Incorrectly setup bios > check priority, if can, reset the defaults
- Unbootable media > check for scratches, burn new copy
- Drive in question defective (maybe not connected, dead) > interchange to be sure, check cabling
- Hard disk dying/bad sectors > Reformat, replace.

From what you said, I don't think it's 1 or 2. 4 likely isn't the problem since you can't even boot a live cd. I think it's 3, and since you've stated you don't want to take the notebook apart (an understandable feeling) I'm not sure we can do much...

If someone's more experienced with this, I welcome their input.

Edit: A note on lew's pointers, yes a cold boot can sometime fix things but in this case I don't believe so. As for the bios, maybe that is the trouble, moss said he tweaked around there a bit, I assumed he knew what options he was touching. As a diagnostic moss, can you please go back to your bios and reset it to defaults (usually an option for that somewhere) then set the boot priority again to cd and try once more.

---

### Post by LewRockwell on 2009-06-20
So now let's assume your drives are operating properly but you need to do some correcting/additions to the data/system(s) on your hard-drive.

If you've just had a grub or bootloader or MBR(master boot record) problem, the first thing you might try would be Super Grub Disk from [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If you're interested in writting zeros to each and every writable area on your hard-drive(s) then you might use DBAN [http://www.dban.org/](http://www.dban.org/) or Killdisk [http://www.killdisk.com/](http://www.killdisk.com/)

If you'd like to enjoy a live-run CD with a wide variety of wonderful utilities including gparted, clonezilla, firefox, and many more then grab yourself the latest release of Parted Magic at [http://www.partedmagic.com/](http://www.partedmagic.com/)

If you'd like some smaller *nix distros to play around with then you'll probably enjoy [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) at 50mb and [http://www.puppylinux.org/](http://www.puppylinux.org/) at 100mb.

---

### Post by qjmoss on 2009-06-21
Sorry everyone, I've been at work.. still too busy to answer all questions, but at work I was thinking.   Would it be possible that Kubuntu doesnt support my cd drive, and Ubuntu does?

---

### Post by starcraft.man on 2009-06-21
> **qjmoss said:**
> Sorry everyone, I've been at work.. still too busy to answer all questions, but at work I was thinking.   Would it be possible that Kubuntu doesnt support my cd drive, and Ubuntu does?

No. This doesn't have anything to do with support for the drive itself anyway. As you described, you can't even boot any media, kubuntu or the vista install disk.

---

### Post by qjmoss on 2009-06-21
Guess i could call sony, and see if my warrenty is still in play.. I wonder how much it would cost for a new cd drive..

---

### Post by wpshooter on 2009-06-21
Moss:

You say "I am currently running Kubuntu".

Are you running that from your hard drive or from a USB thumb drive ?

---

### Post by qjmoss on 2009-06-22
I'm running from my hard drive. Installedvia usb drive/Unetbootin

---

### Post by qjmoss on 2009-06-22
I think something happened when I started messing around with my Windows vista install disks and deleting partions and making new ones, because this happened when I got my bootloader error, and my computer was not usable because I couldnt boot from cd.

I just don't know why my cd drive would fail right then, when everythin else got messed up... ya knoww...

---

### Post by tashirosgt on 2009-06-22
I don't own a laptop, so I'm not sure that I follow the entire discussion.  To test a hard drive, you can download various bootable Cds from hard drive manufacturers (like "Drive Fitness Test" by Hitachi, formerly IBM) or use tools on a bootable Linux like SystemRescueCd.  Is the basic question whether the drive is bad or not?

---

### Post by sadaruwan12 on 2009-06-22
Hi,
Did you checked your Vista DVD or CD on another ROM drive beside your one. Before you do anything first check your DVD or CD on a another ROM to verify that it works with out any problems. If it does work then try to do the partitioning part using a WinXP CD and then try to install Vista on one of those partitions.

---

