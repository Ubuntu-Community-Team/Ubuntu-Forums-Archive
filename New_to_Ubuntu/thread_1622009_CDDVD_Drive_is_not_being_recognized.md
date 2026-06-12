---
title: "CD/DVD Drive is not being recognized"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by frogknowledge on 2010-11-14
I am using Ubuntu 10.04 LTS the Lucid Lynx.

I put a DVD in my optical drive and nothing happens.
I go to places>computer click on the CD/DVD Drive icon nothing happens double click and nothing happens.
I right click on the icon and click properties and noticed that "The permissions of "CD/DVD Drive" could not be determined.".

What do I do?

---

### Post by sidzen on 2010-11-15
Replace the drive, DVD-RW.
Would yours, perchance, be a CD-RW/DVD-ROM?  If so, trash it!

---

### Post by Verbeck on 2010-11-15
could you check whether the cables are connected firmly

---

### Post by mnix on 2010-11-15
I dunno if I can solve your issue, but I can certainly help you narrow it down (before you go replacing the hardware):

Have you ran this drive in another OS?  Any issues?

On another note, do you happen to be dual booting?  If so, does it work in the other OS?

Can you boot from CD-ROM?

If this is a recent problem on an install you've been using for awhile, has anything changed recently?

What kind of drive is it? (i.e. SATA, IDE, USB etc and type DVD, DVD-RW, CD, CD-RW, ect.)

Have you checked for firmware updates?

---

### Post by coffeecat on 2010-11-15
> **frogknowledge said:**
> I right click on the icon and click properties and noticed that "The permissions of "CD/DVD Drive" could not be determined.".

That is normal when there is no disc in the drive. So... Does this happen with just one particular DVD or have you tried several? What type of DVD? A blank DVD you are trying to write to or a pre-recorded DVD? Movie, data or something else? What happens when you put a CD in the drive?

---

### Post by oboedad55 on 2010-11-15
> **coffeecat said:**
> That is normal when there is no disc in the drive. So... Does this happen with just one particular DVD or have you tried several? What type of DVD? A blank DVD you are trying to write to or a pre-recorded DVD? Movie, data or something else? What happens when you put a CD in the drive?

The OP said he put a DVD in the drive and nothing happened. I went around and around with this and finally found an answer. I installed the 2.6.35-rc1 kernel and all was well. None of the previous kernels helped but this one fixed the problem. You can find it here; 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

Download the linux-image for your processor as well as the two linux-headers files, the one for your processor and the other one, and install them. Piece of cake.

---

### Post by coffeecat on 2010-11-15
> **oboedad55 said:**
> The OP said he put a DVD in the drive and nothing happened.

I'm quite well aware of what the OP said. I have had something similar happen with a bad disc. The drive behaves as though there is no disc, which is why I asked the OP for more details about the disc(s) they have used.

---

### Post by oboedad55 on 2010-11-18
Primum non nocere: Above all, do no harm.

---

### Post by coffeecat on 2010-11-18
Indeed! You're quite right. :wink:

---

### Post by siguher on 2010-11-20
I am also having this problem in Ubuntu 10.10.  I am a newbie to Linux and I am trying to set up my system.  Everything works great except my DVD/CDrw drive (matshita DVD-RAM UJ840s).   I just can not get it to work.
I tried to use it with K3B burning software but it crashed with the error message that it did not have permission to write to it.  Then I went to computer rigth clicked ot the drive and under the permissions flip it says "the permissions of "cd/dvd drive" could not be determined.
I tried to insert few cd to see if it worked - A game disc for civ 4 and Warlord 4 (both windows version) - nothing happened and the cd icon in computer vanished,  next I put in original (bouht not written) audio disc -  The icon for my drive in computer changed to audio but then I got the message "Unable to mount audio disc Drive /dev/sr0 does not contain audio files.  And last I put in the same Ubuntu 10.10 startup disc that I used to install the system and the same thing happened as when I put in civ 4 and Warlord 4 cds.

Now I know the drive works - simply because I used it to install the system and it works fine in windows.

First google I went to a site that suggested that this might be a HAL problem.  So I restarted HAL but no change.
One suggested that I needed to mount the drive.  So I did (sudo mkdir /media/cdrom - sudo mount /dev/sr0 /media/cdrom).  Got the right message (mounted successfully) but no change.

Now I am just lost.  If anyone has any idea how to fix this I would be very thankful.

Best regards
Sid

---

### Post by mnix on 2010-11-20
This is kind of wild guess, which sounds like you might well be ok on...but a few things to try.

Firmware update - This is the most likely of the suggestions I am about to give

SATA port - least likely but semi-possible.  I had this issue on install.  My DVD burner was plugged into a SATA port on a controller Ubuntu apparently didn't like for this particular purpose.  Hence, I could boot from the CD, but not install from the CD since the boot system couldn't find the CD (file sytem to read) from whence it booted.  This gave me an error similar to the error you get if your installation disk is faulty.

---

### Post by siguher on 2010-11-20
It is me again.  I connected another Cd drive to my computer and it works so I do not need the fix for the original drive.

Best regards
Sid

---

### Post by oboedad55 on 2010-11-21
Sid, a few more details. Is this Kunbuntu? If so, I believe that's a separate entity now and can be found here; [http://www.kubuntu.org/](http://www.kubuntu.org/)
Otherwise, please tell more about your system, laptop, desktop, etc. Something sounds fishy. Is this a straight Ubuntu install or from Windows? Some of us had the disappearing CD issue with 10.04 but I haven't seen it with 10.10. Are you running Gnome and adding KDE programs? Tell all.

---

### Post by coffeecat on 2010-11-21
> **siguher said:**
> nothing happened and the cd icon in computer vanished

> **siguher said:**
> I connected another Cd drive to my computer and it works so I do not need the fix for the original drive.

@siguher, a long shot this, but this sounds familiar. Is the CD/DVD drive that is giving you problems in 10.10 a USB connected external CD/DVD drive?

---

