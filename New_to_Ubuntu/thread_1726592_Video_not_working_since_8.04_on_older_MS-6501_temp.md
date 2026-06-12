---
title: "Video not working since 8.04 on older MS-6501 temperamental motherboard"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by jal301 on 2011-04-11
I have one of the original server / dual-processor boards with two separate CPU's (specs linked below) which has been really temperamental with Ubuntu - but I am committed to sticking with it and not giving this old machine up.  The final issue I have yet to resolve on this machine is the video.  Video has not worked since Ubuntu version 8.04.  I have tried different video cards and the latest purchase causes the board to send out a continuous beep and locks it up in the middle of the CD loading for an install.  So back to the original AGP card...on 9.10 I only get a 640 x 480 resolution.  On 10.04, Ubuntu boots to a command prompt (both the install from having another video card originally installed or when I boot to CD) and I don't really know what code to enter at this point - it just says "Welcome to Ubuntu...." or something like that.  So I have this problem but I do not know where to begin in order to resolve this.  I would like to upgrade to one of the newer versions of Ubuntu since support is ending for the latter versions.  Any suggestions / guidance / direction is appreciated!
Thank you!

[http://www.superwarehouse.com/MSI_K7D_Master-L_ATX_Dual_Athlon_Motherboard/MS-6501-030/ps/190873](http://www.superwarehouse.com/MSI_K7D_Master-L_ATX_Dual_Athlon_Motherboard/MS-6501-030/ps/190873)

---

### Post by TeoBigusGeekus on 2011-04-11
> **jal301 said:**
> I would like to upgrade to one of the newer versions of Ubuntu since support is ending for the latter versions.  


Do it... Perhaps the newest kernels used in the latest versions will resolve your hardware problems.

---

### Post by jal301 on 2011-04-15
> **TeoBigusGeekus said:**
> Do it... Perhaps the newest kernels used in the latest versions will resolve your hardware problems.

I would *like* to but I cannot because running any version newer than 8.04 gives me some kind of video issue which I have not been able to resolve.  What I would really like to know is how to begin to resolve the last issue I have with Ubuntu and this older machine.

---

### Post by Mark Phelps on 2011-04-15
Need to know the make and model video card. Open a terminal and enter "lspci" and look for a line containing VGA.

If you have an ATI card, and it's NOT one of the newer PCI/PCIe HD 3x/4x/5x cards, there will be no restricted drivers available for it. Support for those drivers ended with Ubuntu 8.10.

You may be able to use the default open-source drivers, but don't know if they still work with AGP cards anymore.

---

### Post by jal301 on 2011-04-15
> **Mark Phelps said:**
> Need to know the make and model video card. Open a terminal and enter "lspci" and look for a line containing VGA.

If you have an ATI card, and it's NOT one of the newer PCI/PCIe HD 3x/4x/5x cards, there will be no restricted drivers available for it. Support for those drivers ended with Ubuntu 8.10.

You may be able to use the default open-source drivers, but don't know if they still work with AGP cards anymore.

Okay, thank you for the leads.  It is an nVidia card and does require a restricted driver.  I have not explored much with the open-source driver(s).  I will go through some of your suggestions first thing tomorrow and come back with the results.

---

### Post by jal301 on 2011-04-16
> **Mark Phelps said:**
> Need to know the make and model video card. Open a terminal and enter "lspci" and look for a line containing VGA.

If you have an ATI card, and it's NOT one of the newer PCI/PCIe HD 3x/4x/5x cards, there will be no restricted drivers available for it. Support for those drivers ended with Ubuntu 8.10.

You may be able to use the default open-source drivers, but don't know if they still work with AGP cards anymore.

Okay, so I have an nVidia GeForce2 MX 400 AGP8X 64mb card.  I found the following two posts concerning this card:

[http://ubuntuforums.org/archive/index.php/t-480991.html](http://ubuntuforums.org/archive/index.php/t-480991.html)
[http://ubuntuforums.org/archive/index.php/t-415267.html](http://ubuntuforums.org/archive/index.php/t-415267.html)

The first has no answer except for the next-to-last post which offers a suggestion although I'm not certain how to execute the nvidia-gxl command; nor do I know if this will work with my current, fresh install of 8.04 or anything newer.

The second set of posts has a number of people claiming success but again I do not know how to execute these nor do I know if this will work with my current, fresh install of 8.04 or anything newer.

What do you suggest as a next step?

By the way - I did not enter "lspci" from terminal so I will boot and do so now and see if there is any additional information which may be helpful.  I got the model from pulling the card and reading the tag applied.

---

### Post by jal301 on 2011-04-16
> **Mark Phelps said:**
> Need to know the make and model video card. Open a terminal and enter "lspci" and look for a line containing VGA.

If you have an ATI card, and it's NOT one of the newer PCI/PCIe HD 3x/4x/5x cards, there will be no restricted drivers available for it. Support for those drivers ended with Ubuntu 8.10.

You may be able to use the default open-source drivers, but don't know if they still work with AGP cards anymore.

So now I have run 'lspci' in terminal with the following output:
01:05.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
02:06.0 VGA compatible unclassified device: Creative Labs SB Live! EMU10k1 (rev 05)

I'm guessing that the second VGA device is the extra sound card that I have installed; although it is a PCI card and not a VGA.  I removed it with hopes that perhaps having it installed (and with the system possibly recognizing it as a VGA device and causing a conflict) was causing the computer to not offer a greater range of resolutions but this did not help.  So, I am still open to any suggestions you may have.

---

### Post by jal301 on 2011-04-16
And while I am carrying this conversation with myself, I have also tried the following: In my earlier pursuits to correct this problem, I thought that perhaps the card was just old and I needed a newer one.  So I bought an nVidia NV 34 GeForce FX 5500 128mb card.  Still with my fresh install of 8.04 I can replace the former card and the system boots but does not offer any greater resolution choices than the former (stuck at 640 x 480).  sudo nvidia-settings does not work but I suppose that I do not have something installed to get this to work as terminal returns "nvidia-settings: command not found".

This current card (the FX 5500 is the one where when I tried to install 10.10 from the CD, the CD would load to a point and then the install would freeze and a continuous beep would come from the motherboard.  When I would try to boot from the Live CD, it would just freeze at a point, upon multiple tries.

Do you think that I am having an AGP problem?  Is this an nVidia issue?  Should I try a PCI video card?  I'm hoping that somebody could help with a true / known solution because I'm tired of wondering aimlessly here with this problem, unable to stumble upon a solution.

Thank you in advance for your time, consideration, and help.

---

### Post by wep940 on 2011-04-17
You might also want to download the alternate CD and try installing from that.  It goes through the old configure of video, and is text based, so perhaps it might work to install and then see if the video works.

---

### Post by clhsharky on 2011-04-17
jal301

Ububtu has been moving to auto-config with devices with the last few releases, and it might be giving you issues.

1 - Move sound card to different pci slot, pci slots are shared on older motherboards, then install.
2 - Or remove sound card and try installation again, to see if there is a still a conflict. Creative Labs sound cards have been problematic.

10.04 LTS works well with NVidia GeForce  and proprietary drivers,  GeForce4 MX 4000 will use the default Nouveau open source drivers as will the FX 5500.
I have both of them.


Sharky

---

### Post by jal301 on 2011-04-17
> **wep940 said:**
> You might also want to download the alternate CD and try installing from that.  It goes through the old configure of video, and is text based, so perhaps it might work to install and then see if the video works.

I will try this next time I do a fresh install to the latest version with this computer.  I performed an upgrade to 10.04 from 8.04 last night and everything went smoothly.  But as I said before, installing right from the 10.04 CD was giving me issues so I will keep this in mind.

> **clhsharky said:**
> jal301

Ububtu has been moving to auto-config with devices with the last few releases, and it might be giving you issues.

1 - Move sound card to different pci slot, pci slots are shared on older motherboards, then install.
2 - Or remove sound card and try installation again, to see if there is a still a conflict. Creative Labs sound cards have been problematic.

10.04 LTS works well with NVidia GeForce  and proprietary drivers,  GeForce4 MX 4000 will use the default Nouveau open source drivers as will the FX 5500.
I have both of them.


Sharky

I performed the upgrade to 10.04 with the sound card removed with success - excellent!  It looks like the last thing I need to work through is being limited to a 640 x 480 resolution but I have read that others have had this issue so I will explore this one a bit further and report back.

Thank you to each of you for your help!

---

### Post by jal301 on 2011-04-17
> **clhsharky said:**
> jal301

Ububtu has been moving to auto-config with devices with the last few releases, and it might be giving you issues.

1 - Move sound card to different pci slot, pci slots are shared on older motherboards, then install.
2 - Or remove sound card and try installation again, to see if there is a still a conflict. Creative Labs sound cards have been problematic.

10.04 LTS works well with NVidia GeForce  and proprietary drivers,  GeForce4 MX 4000 will use the default Nouveau open source drivers as will the FX 5500.
I have both of them.


Sharky

Sharky,

Did you have any issues with either of these cards being limited to a 640x480 resolution?  I have the proprietary driver installed (96 for the MX 4000 and 173 for the FX 5500) and I have been unable to get past this issue.  I see in the forums that a lot of people are reporting the same problem but there has been a shotgun approach to solving it - and I would like to stick to something a bit more 'official' than to attempt a half-assed work-around (although, at this point - *anything* working is a big improvement, I'd just like to know that it *will* work *before* attempting it).  What do you suggest?

PS - I attempted the code suggested in the post linked below but that caused the system to freeze upon reboot and I am stuck doing a fresh install of 8.04 again.

[http://ubuntuforums.org/showpost.php?p=10470321&postcount=2](http://ubuntuforums.org/showpost.php?p=10470321&postcount=2)

---

