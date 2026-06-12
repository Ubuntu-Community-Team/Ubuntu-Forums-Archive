---
title: "[SOLVED] reformating"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by navidson on 2009-01-08
I have "upgraded" from ubuntu 8.04LTS to 8.10 and have found the performance of my computer and internet has drastically decreased compared to 8.04. It's a fairly new computer and have been told there should be no prob running either but after a lot of searching and messing around I'm feeling that a fresh start back to 8.04 may be my best option. anything i need is basically backed up on a seperate harddrive. Is there anything i should know before i use the ubuntu disk that came with the computer to reinstall 8.04? I'm pretty intermediate with computers but have been loving linux up to this point...any advice would be greatly appreciated. thanks.

---

### Post by iaculallad on 2009-01-08
You just have to boot from your CD media and manually partition the drive and supply the information needed, the rest would be accomplished by the Ubuntu LiveCD.

---

### Post by navidson on 2009-01-08
will the option to manualy partition it be there with the disk? i've never actually reformatted a harddrive myself but i basically want a fresh start haha. my head hurts from all the computer reading i've done, hurts more from all the stuff i didn't understand. hehe.

---

### Post by Paqman on 2009-01-08
If your data is backed up then just go for it.

If you want to retain your settings then you can take a backup of your home folder (make sure you get all the hidden files, ctrl-h to see them). Then once you've reinstalled 8.04 copy the contents into your own home folder and take ownership of them with:
```
sudo chown -R username:username /home/username
```

The other way to achieve the same thing is to have /home mounted on a separate partition. Then when you reinstall choose "manual partitioning" and pick the existing /home partition to be mounted at /home and make sure it isn't selected to be formatted.

---

### Post by suomalainen on 2009-01-08
Hi Buddy!

If you want to erase your drive for a real clean install take a look at

Darik's Boot and Nuke! It's free and awesome. Even was type approved in Canada by the Royal Canadian Mounted Police.

[http://www.dban.org/](http://www.dban.org/)

Don't forget to export your email.

Don't forget to save your wallpaper and icon folders if you created them

Make a list of all the apps you have in Applications in case you installed something you want to use again.

Few thoughts.....

---

### Post by navidson on 2009-01-08
well so far i've tried to do it off the cd i got with my computer and it's telling me it can't find the autorun program. with that link in the last post will i have to figure out how to get all my drivers again? i'm not all that computer literate as far as these things go. or is there a way to get my autorun to work? haha I can't even perform the easiest step. sadistically funny.

---

### Post by Rohan Kapoor on 2009-01-08
> **navidson said:**
> well so far i've tried to do it off the cd i got with my computer and it's telling me it can't find the autorun program. with that link in the last post will i have to figure out how to get all my drivers again? i'm not all that computer literate as far as these things go. or is there a way to get my autorun to work? haha I can't even perform the easiest step. sadistically funny.

I guess I don't understand. You did put the cd in and tell the computer's bios to boot off of it, right?

---

### Post by navidson on 2009-01-08
ooo that could very well be the deal...um...how exactly do i get it to boot off the cd?...i'm starting to feel fairly dumb haha.

---

### Post by handydan918 on 2009-01-08
> **navidson said:**
> well so far i've tried to do it off the cd i got with my computer and it's telling me it can't find the autorun program. with that link in the last post will i have to figure out how to get all my drivers again? i'm not all that computer literate as far as these things go. or is there a way to get my autorun to work? haha I can't even perform the easiest step. sadistically funny.

Heh. I can hear your computer laughing at you .
Let's teach it a little respect.
Try rebooting with the 8.04 disk in the drive. If the live cd boots up, good. 
If not, reboot, and get into your bios, usually a keypress like esc, f2, f11, f12, or del is used to bring up the bios. 
Once in, check the boot order and make sure the cdrom is first in the line up. Save your changes, (often f10) and exit. 
Post back if the box hasn't yet learned who is master....

---

### Post by navidson on 2009-01-08
thanks everyone for your help i'm back to 8.04 now when i go to do my updates it tells me to Please insert the disk labeled:
Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)
in drive /cdrom/

well the disk is in the drive and i press okay and nothing happens. and it's not letting me update...

---

### Post by handydan918 on 2009-01-09
> **navidson said:**
> thanks everyone for your help i'm back to 8.04 now when i go to do my updates it tells me to Please insert the disk labeled:
Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)
in drive /cdrom/

well the disk is in the drive and i press okay and nothing happens. and it's not letting me update...

Post the output of ```
cat /etc/apt/sources.list
```

I suspect you just need to enable some repos...you could also just open synaptic and check on my theory there...

---

### Post by Paqman on 2009-01-09
> **suomalainen said:**
> 
Make a list of all the apps you have in Applications in case you installed something you want to use again.


Just as an aside: Ubuntu can [do this automatically]("http://ubuntuforums.org/showthread.php?t=261366") for you. It will even reinstall them all automatically, too.

---

### Post by navidson on 2009-01-09
> **handydan918 said:**
> Post the output of ```
cat /etc/apt/sources.list
```

I suspect you just need to enable some repos...you could also just open synaptic and check on my theory there...

ryan@dell-desktop:~$ cat /etc/apt/sources.list
## deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main

---

### Post by navidson on 2009-01-09
i check it out and it was trying to run off the cd still. i got it working...my internet downloads are superslow but i'll deal with that after my updates are done downloading...handydan...thanks so much for the help...if i post what network card i have can you tell me if it's an n series because i have a feeling they may have installed the wrong network card....mine's supposed to be superfast and it most definitly is not.

---

### Post by WitchCraft on 2009-01-09
> **Paqman said:**
> If your data is backed up then just go for it.

If you want to retain your settings then you can take a backup of your home folder (make sure you get all the hidden files, ctrl-h to see them). Then once you've reinstalled 8.04 copy the contents into your own home folder and take ownership of them with:
```
sudo chown -R username:username /home/username
```

The other way to achieve the same thing is to have /home mounted on a separate partition. Then when you reinstall choose "manual partitioning" and pick the existing /home partition to be mounted at /home and make sure it isn't selected to be formatted.


Ay! Backup your E-Mails and address book !
Additionaly, icons, themes and background images reside in /usr/share/

---

### Post by handydan918 on 2009-01-09
> **navidson said:**
> i check it out and it was trying to run off the cd still. i got it working...my internet downloads are superslow but i'll deal with that after my updates are done downloading...handydan...thanks so much for the help...if i post what network card i have can you tell me if it's an n series because i have a feeling they may have installed the wrong network card....mine's supposed to be superfast and it most definitly is not.

well, all I can do is google it..but post away. Try giving us the output of ```
lspci | grep -i net
```
And if you're still having the "insert cd" issue, look at your sources.list and find this line:

```
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted 
```

and comment it out (by adding a # to the beginning of the line.)

---

### Post by navidson on 2009-01-09
k the cd thing is figured out now. thanks handydan...here is my ethernet controller.
i've been getting much slower download speeds on speedtest.net than my roommates and i supposedly have a much better card than them so i'm not sure what's going on...

ryan@dell-desktop:~$ lspci | grep -i net
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

