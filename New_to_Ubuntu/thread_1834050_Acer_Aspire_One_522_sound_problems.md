---
title: "Acer Aspire One 522 sound problems"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2011-08-27
Hi,  I bought a new Acer Aspire One 522 netbook a couple of weeks ago and installed both Natty and WinXP in seperate partitions on it.  Once I installed all Acer's Windows drivers on the XP.  all its sound facilities including internal mic and external earphone jack work fine there,  but on Natty, despite trying various suggestions in similar threads here,  I'm still struggling with big sound troubles.

Maybe some subtle differences between my Aspire One and the models referred to in other threads explain why the suggestions in other threads haven't worked, or maybe I'm just plain thick and stupid.  Either way, I could do with some guidance if anyone has the patience to go through it with me!! 

Here's my setup:

Acer Aspire One 522 netbook with AMD Dual Core C-50 (1Ghz) processor
2 Gb DDR3 memory
Natty with linux-headers-2.6.38-11-generic (2.6.38-11.48 )
Classic desktop
Soundcard ATI Technologies Inc Device 1314    (ATI ID aa01)    

OK, a few days ago,  after opting for Analog Stereo Duplex sound (instead of the default rear socket digital HDMI interface) I had internal speaker sound but no internal or external mic or external earphone socket  working. 

I then downloaded alsa-hda-dkms-acer3830tg_0.1_all.deb and had Ubuntu Software Center install alsa-hda-dkms  (2.1.1.2-5ubuntu).   This gave me good earphone socket sound and good external mic socket sound, but internal mic sound was very low level,  crackly and basically unuseable.

So then I discovered : [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html), downloaded script "alsa_setup.sh" from there and ran it.   This script called for a file /usr/src/linux-headers-2.6.38-11-generic/include/linux/autoconf.h which does not exist,  but the script continued to run for several more minutes.   I don't know what it was doing,  but it ended according to plan in an automatic restart.

But after running that script,  I found I had lost all my sound facilities.  No speaker sound,  no earphone sound,  no mic,  terminal command 'alsamixer' generates the response 'no mixer elems found'   and my Sound Preferences -  Hardware tab,  Input tab,  and Output tab all tell me to Choose a device...  but there are no options shown at all there,  only blank areas.      Basically this script appears to have removed whatever sound installation I previously had.

I tried to run alsa-hda-dkms again in the hope that would reinstall what I had lost, but this time it had no effect.   No sound and command 'alsamixer' only yields 'No mixer elems found'

So since my efforts only seem to be serving to dig me into deeper trouble,  I'm wondering what to try next.  Dunno,  looks like I need to take a step back and re-install all my sound software from scratch.   I have found two sources of alsa drivers listed at [http://www.alsa-project.org/snapshot](http://www.alsa-project.org/snapshot),  but I don't really know whether running the 'makefile' in one of those would be a sensible way to proceed now.   

Anyone guide me,  please?

---

### Post by stchman on 2011-08-27
The script I authored was for Intel HDA sound cards not ATI.

---

### Post by Sleepy-zz-John on 2011-08-27
> **stchman said:**
> The script I authored was for Intel HDA sound cards not ATI.
OK,  noted,  thanks.   This teaches me that the differences are more fundamental than I realised. 
So now my question is where to start to undo the damage running that script has done?

---

### Post by Sleepy-zz-John on 2011-08-29
Bump

Sorry about my lengthy complicated-looking OP. :redface: 

What I guess I'm looking for now is some guidance on where to start with  reinstalling all my sound-related s/w from scratch.

---

### Post by Sleepy-zz-John on 2011-08-30
Bump again.

and this time some more info in my "alsa-info.txt" attachment

---

### Post by Zill on 2011-08-30
Sleepy-zz-John:  Although you probably *could* repair the damage done to your Ubuntu installation, I suggest that this is probably more trouble than it is worth.

Given that this is a new installation presumably you have little of your own data stored on it.  On this basis, I recommend reinstalling Ubuntu.  Just make sure that you have good backups of *all* your data on the machine before you start.

When you have your new Ubuntu installation running, I suggest you repost clearly advising *exactly* what you wish to do to change the default sound system.  Hopefully someone will then be able to give good advice and provide the right resolution of the problem.

---

