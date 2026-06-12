---
title: "Changing Distros, Step-by-Step?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by CybaCowboy on 2008-12-27
Okay,


So normally I use Ubuntu, but in a spare-of-the-moment decision, I thought I'd change to the Google-powered gOS (see [http://www.thinkgos.com](http://www.thinkgos.com)), which is based directly on Ubuntu (version 8.04 I think)...

Well it's pretty and the green theme is fantastic, but it's starting to become obvious that I don't use (most of) Google's products and services as much as I thought I would; further to this, there are a number of key computer functions that do not work (which work fine in the latest version of Ubuntu), and the community support definately leaves a lot to be desired.


Therefore, I am eager to switch back to Ubuntu as soon as possible, though I'm wanting a little bit of help this time around - when I switched from Ubuntu to gOS, I killed my GRUB and stuffed-up my Linux partitions... Being the (Linux) noob that I am, it took me about 6 hours to get gOS going, without harming the 50GB+ of data stored on my Microsoft Windows partition!


Anyway, the way I figure it, there's gotta be an easier way to change distros and I remember reading something on the gOS "support" site that said a distro upgrade, if performed incorrectly, will transform a gOS system into a "fully-fledged Ubuntu system".

Can anyone shed some light on this, and maybe offer a Linux noob step-by-step instructions on changing distros?


I have the Live CD of Ubuntu 8.10, if that makes it any eaiser (I'd still need step-by-step instructions though, given my previous experiences changing distros!)...

---

### Post by billgoldberg on 2008-12-27
I woudn't adive on this.

Simply back up your data and install Ubuntu 8.10 on the gOS partition.

If the grub then doesn't show you windows partition do this in a terminal:

sudo gedit /boot/grub/menu.lst

In the bottom of the document past this:

> #Windows boot
title Windows XP
root (hd0,1)
chainloader +1

note that (hd0,1) means that windows is on sda2 or hda2

If yours is on sda1 or hda1, it's (hd0,0).

Use the command "fdisk -l" (without the ") in a terminal to see what drive it's on.

If it's on the second hard drive, use (hd1,0).

---

### Post by CybaCowboy on 2008-12-27
Are you *sure* this is the best way to do it?


When I previously changed from Ubuntu to gOS, I tried installing gOS over-the-top-of-Ubuntu (as you suggest for the reverse) and I ended up with *two* Linux installations!

It was the attempt to remove one or the other that kept me in front of my computer for the next six hours...

---

### Post by mkvnmtr on 2008-12-27
This is how I installed over a distrubution many times when I first started using Ubuntu. First I would boot the live disk. Go to partition editer. Look at all your partitions. Figure out which are which by the size and the label. You should be able to tell which is windows and Gos. You should see which is boot and which is swap with out much trouble. Write it down if you need to. Then when you go to install use the manual install.You will only be interested in the boot and the ubuntu partitions. Those you will need to set mount points and format. When you are going back with the same boot system you don't even need to format and the mount point should be already set.Don't change the size or anything else you don't understand. When you go to format if you haven't done it right GParted should not let you proccd. Up to the point of formating you can back out ton the live disk desktop and go to the forum  to ask questions. When you feel sure proceed. There is no hurry. My first time I backede out about 8 times.

There are better and faster ways but when you are not sure this should get yuou through with no mistakes.

---

### Post by CybaCowboy on 2008-12-27
Here is the setup of my current partitions, which hold gOS and Microsoft Windows Vista:
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/Currentpartitions.png[/IMG]

Using this setup, I was able to get my computer working again (*without* damaging the data stored on Windows Vista partition!), when I stuffed it up last time (as mentioned above)... I tell you this because I have a feeling that there should be at least one more Linux partition.


Next, we have the manual-partition-edit screen from the Live CD's installation wizard, showing the current partitions:
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/Preparepartitions.png[/IMG]

Whether this is right or not, I was going to try and format the two Linux partitions, then presumably install Ubuntu on top of my existing gOS installation... But the installation wizard won't let me select the "Format" checkboxes (this is also the case with the two boxes below...)!


It does however, give me some options if I double-click the Linux partitions...

sda2 (swap):
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/Editpartitionsda2swap.png[/IMG]

sda3 (ext3):
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/Editpartitionsda3ext3.png[/IMG]


Anyway, not quite sure where to go from here, so hopefully one of you guys can help me...

---

### Post by mkvnmtr on 2008-12-27
I am confused I don't see a boot partition. Is this a wubi install?

---

### Post by CybaCowboy on 2008-12-27
> **mkvnmtr said:**
> I am confused I don't see a boot partition. Is this a wubi install?

No idea what "wubi" is and whilst I'm definitely no Windows noob, I *am* a Linux noob and the above is how I "fixed" it when I stuffed it last time, replacing Ubuntu with gOS.

Evetything works fine, including GRUB and gOS/Windows, but I'm confident that *somewhere* I have stuffed it up, as you have seemingly noticed...


By the way, those "fixed" Linux partitions you see above, they were created manually, during the process of changing from Ubuntu to gOS.


Oh yeah, I meant to ask, couldn't I just use Terminal to do a distro-upgrade to get Ubuntu back?

According to gOS support site:
[i]**Do not let an upgrade happen (but updates are fine)**


Note that because gOS 3 is an unofficial Ubuntu 8.04 derivative Good OS (the creator of gOS) has no control over what is in an Ubuntu upgrade (not upDATE, but upGRADe, as in "upgrading from windows XP to Vista", rather than in "accepting a security update"). gOS has tried to make it impossible that this happens, nevertheless it is in theory possible (by enabling the wrong update repository, or by other unintentional actions) that the Updater tries to "Upgrade" gOS 3 to another (newer version) of Ubuntu, this can damage your gOS install if you let it happen! So never under any circumstance accept an UPGRADE, of course the regular updates you get should be fine, as gOS is based on Ubuntu 8.04 which version Ubuntu has pledged will not auto-upgrade to a newer version, as it is deemed a "long term stable" version, so all updates from ubuntu should be fine.[/i]

So shouldn't I be able to simply do a distro upgrade?

It's gotta be easier than all this stuffing around (though I will need the specific Terminal command to do this, and the instructions to add the applicable repository)...


My existing repositories:
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/SoftwareSources.png[/IMG]

And the "updates" tab (which I suspect bears no relevance, but I posted it here just in case...):
[IMG]http://i98.photobucket.com/albums/l272/gregoryopera/Temporary/SoftwareSourcesupdates.png[/IMG]

---

### Post by mkvnmtr on 2008-12-27
I can't see where your Grub boot is. You are using Grub to boot? I see your swap partition and it is a little big but no need to change it. The partition with windows in it should not be touched. If you delete the partition formated in ext3 with the live disk and leave the area undefined when you install yoou can choose to use the largest free space. Then the installer will form a grub doot partition and a Ubuntu partition in this space. Grub will recognize your windows os and give you the choice to boot in either with linux being the default if you don't choose in so many seconds. There should be no problems. Click on install and follow the installer up to the point that it asks you to format. Then you can back oout and think about it. Only when you are ready proceed. After the format there is no backing. Back up your data in windows and the worst thing that can happen is you have to reinstall windows and try again to get the dual boot. You can not ruin equipment only lose data. A back up will keep you from loosing data. Try it I will be up for another hour if you have questions.

---

### Post by CybaCowboy on 2008-12-27
So just to clarify (in a nutshell), delete the "sda3 (ext3)" partition, use the installation wizard to install to "the largest free space" and theoretically, eveything should be sweet?

---

### Post by mkvnmtr on 2008-12-27
Yes that should give you a boot partition of less than 1Bb, I think it is just a few Mbs and a Ubuntu partition of all the rest of the space in that partition. One note I have read there is a bug in the 8.10 installer where it will tell you that it will remove every thing  but it won't. That scared a lot of people but it works just fine. 8.04 didn't have this problem. This is why I tell you to get to the point of formating and then back out untill you are sure.

---

### Post by CybaCowboy on 2008-12-28
My heart skipped a beat when it told me it was going to format everything, but I held my breath, closed my eyes and hoped for the best...

And now my computer is back to the way it was a few days ago!


Thanks guys!

---

### Post by mkvnmtr on 2008-12-28
Great. Have fun.

---

