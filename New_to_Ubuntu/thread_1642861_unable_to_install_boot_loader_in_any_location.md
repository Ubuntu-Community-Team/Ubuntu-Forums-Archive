---
title: "unable to install boot loader in any location"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by degarb on 2010-12-10
Trying to install U on external HD.  But can't install boot loader. I need xp far more than U.  So need a boot loader.  What gives?

---

### Post by oldfred on 2010-12-10
The latest version Maverick does not give an option of where to install grub unless you use manual install. I guess they assume that if installing to more than sda that it is an advanced install. It normally just defaults to installing grub2 to sda which will overwrite your windows boot loader on the internal drive. 

If you have installed grub2 to the internal drive we have instructions on how to reinstall grub to the external and either XP or a windows like boot loader to the internal to boot windows.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by degarb on 2010-12-11
Thanks.  I confess I am still confused.  

My assumptions (please correct them): *grub is boot loader? * boot loader not good on external drive. * **Will installing with no bootloader will make xp inaccessible?**

Why I think not advanced install: Only a moron has one hd, while a fool has only two. The brave have three. The other reason: with ext drives so cheap and available, this type of install on the external drive should be the future.

---

### Post by degarb on 2010-12-11
> **oldfred said:**
> The latest version Maverick does not give an option of where to install grub unless you use manual install. I guess they assume that if installing to more than sda that it is an advanced install. It normally just defaults to installing grub2 to sda which will overwrite your windows boot loader on the internal drive. 

If you have installed grub2 to the internal drive we have instructions on how to reinstall grub to the external and either XP or a windows like boot loader to the internal to boot windows.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

I guess I need to know in next few minutes before I abort install, if I install with no boot loader, what will happen.   Will it boot as before in xp, or will it boot to Ubuntu?  This can be fixed later by adding lines to the windows boot loader we all trust and know?  Or some later more advanced fix?

Again, need to know in few minutes before I just hit abort.

---

### Post by oldfred on 2010-12-11
If you are using advance install it gives a choice on where to install grub and you want it installed to the external drive.

If you do not install grub at all you will not be able to boot. There are some fairly complicated (to me) ways to use a windows boot loader. But if you install grub2 to the external drive and set the external drive as first in the boot order in BIOS, it will boot grub and grub will give you a choice of Ubuntu or windows. If you remove external it will boot from the internal drive and boot your windows.

---

### Post by degarb on 2010-12-11
> **oldfred said:**
> If you are using advance install it gives a choice on where to install grub and you want it installed to the external drive.

If you do not install grub at all you will not be able to boot. There are some fairly complicated (to me) ways to use a windows boot loader. But if you install grub2 to the external drive and set the external drive as first in the boot order in BIOS, it will boot grub and grub will give you a choice of Ubuntu or windows. If you remove external it will boot from the internal drive and boot your windows.

Okay, the last sentence puts my mind at rest.  Since, I am betting the china made external drive may only have a year life left before failure.

I will attempt to install grub on external drive now.

---

### Post by degarb on 2010-12-11
It wont install on any drives, including external.

I made a twenty eight gig ext4 partion for ubu, and 2 gig swap.  Did I need another for grub?

---

### Post by oldfred on 2010-12-11
And if it installs to the wrong drive it is not all that difficult to reinstall boot loaders. It seems difficult at first but after you do it a few times it is no big deal at all. But you need a windows repair CD for the version of windows you have. But you can repair both windows & Ubuntu with a Ubuntu liveCD (or most Linux rescue CDs).

If you have a windows CD you just need to run fixMBR for XP. For Vista/7 it is BootRec.exe /fixmbr.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by degarb on 2010-12-11
Also, it is telling me that cancelling may cause macine to not be able to boot.  I am not buying it, unless it already wiped the windows boot loader, which I can't imagine they would do that at this point.

---

### Post by degarb on 2010-12-11
> **oldfred said:**
> And if it installs to the wrong drive it is not all that difficult to reinstall boot loaders. It seems difficult at first but after you do it a few times it is no big deal at all. But you need a windows repair CD for the version of windows you have. But you can repair both windows & Ubuntu with a Ubuntu liveCD (or most Linux rescue CDs).

If you have a windows CD you just need to run fixMBR for XP. For Vista/7 it is BootRec.exe /fixmbr.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


I don't see how the live cd can help fix the mbr, if the installer cannot install it.

Also, this is a gateway machine with xp home.  I only have a xp pro from my old machine. So, I don't have a proper version.  

Should I hit cancel, or install with no grub?  Or do I need a third partion?

---

### Post by degarb on 2010-12-11
Still waiting for a reply, before I hit cancel or continue with no grub.

---

### Post by oldfred on 2010-12-11
I always install grub. 

LiveCD will install grub. And Ubuntu liveCD will install a windows boot loader. The boot loader for XP is the same boot loader all the way back at least win98 and maybe before. You can use any winXP CD to reinstall a XP boot loader.

From Ubuntu's command line this will install a boot loader that boots windows. If you need it.

I will be back tomorrow. Its late.

---

### Post by degarb on 2010-12-11
> **oldfred said:**
> I always install grub. 

LiveCD will install grub. And Ubuntu liveCD will install a windows boot loader. The boot loader for XP is the same boot loader all the way back at least win98 and maybe before. You can use any winXP CD to reinstall a XP boot loader.

From Ubuntu's command line this will install a boot loader that boots windows. If you need it.

I will be back tomorrow. Its late.

I too am tired.  Thanks for the help.

I do understand  a windows CD you just need to run fixMBR for XP.

I am still unsure why grub wouldn't install on any partions, even the external ext 4 ones.  Your post doesn't tell me the lines to fix the mbr with the live cd, or why it would work, but not the installer.  

I did hit abort install, and machine booted normally into windows.  I am guessing I need another partion for grub on the external drive.  If so, then I need to run again and create it and install again. Took 4 hours tonight, with not much luck.  

On a side note: there is much work to be done on installer cd for 10.1.  No status updates as it downloads and installs stuff, making most users abort as they think install is freezing.  The ps2 mouse didn't work during install, which made it a pain. The partioning utility is bassawards, lacking intuitive things.  And during entire install I saw only drab, uninspired graphics too, that would fail to stir any anticipation.  I think the beta leader needs to incorporate new blood into the tests.   It has feel of being tested by only pros.

---

### Post by oldfred on 2010-12-11
I do not see the things you do, but I partition in advance. My last couple of installs I did say to update while installing and it does take a while. 
Before, just as I converted from CD to USB install with partitions set up in advance I was able to install in about 10 minutes, but then going back and doing updates, adding my programs and some settings ended up about an hour total. Now the install takes longer but the updates is shorter, still about an hour.

You should not need a partition for grub, as that is the grub code the MBR points to (and it is a lot more complicated to maintain.  I had/have one with grub legacy, but do not use it anymore. You have to have grub in the MBR of the external if you want to boot Ubuntu. Just that you have to use manual install to get that choice. Computers only boot by loading BIOS, BIOS jumps to MBR, MBR loads code from hard drive. Windows is only slightly different as the windows code in the MBR looks for the active partition (boot flag) and jumps to that partiitons boot sector ( or PBR) which loads the code from the hard drive.

---

### Post by QLee on 2010-12-11
[QUOTE=degarb]Thanks.  I confess I am still confused.  [/QUOTE]
I'll try and clear up some of that confusion, oldfred will give you excellent help with your install.

[QUOTE=degarb]My assumptions (please correct them): *grub is boot loader? [/QUOTE]

Correct, first stage in the MBR of the harddrive, points to the location (partition, volume) of the rest of the bootloader and the menu file.

[QUOTE=degarb]* boot loader not good on external drive. [/QUOTE]

Incorrect. It's a matter of choice. First stage of GRUB (bootloader) needs to be in the MBR of the drive that the system treats as the "boot" drive, can be internal or external, typically it is configured in the system BIOS or changed by some hotkey (computer maker dependent) accessed after the POST.

[QUOTE=degarb]* **Will installing with no bootloader will make xp inaccessible**[/QUOTE]

Since we are talking about an Ubuntu install, no, the Windows bootloader would not be touched and Windows would still boot. However, Ubuntu would not boot because the Windows bootloader wouldn't automagically recognise it. You could use the Windows bootloader to boot Ubuntu but you would have to learn how to configure it. The Grub bootloader installed with Ubuntu will recognise Windows and add it to the GRUB menu.


[QUOTE=degarb]Why I think not advanced install: Only a moron has one hd, while a fool has only two. The brave have three. The other reason: with ext drives so cheap and available, this type of install on the external drive should be the future.[/QUOTE]

Well, I don't think of myself as a moron or fool, but my laptop only has room for one internal and it's USB2 so I'm not willing to put up with the slower speed of booting and running from external. I have one old desktop that is USB1 and I'm really not interested in booting from an external on that one, no matter how inexpensive they are these days.

It's considered "advanced" because not all users in the target audience have as much knowledge as you do, many of them need things to be as simple as possible.

I hope this helps to clear up some of the confusion you mention and makes sense.

---

### Post by QLee on 2010-12-11
[QUOTE=degarb]...  I think the beta leader needs to incorporate new blood into the tests.   It has feel of being tested by only pros.[/QUOTE]

Please allow me to correct this assumption also. The betas and indeed the alphas also are available to us all. Lots of inexperienced users install and test them. In fact, some experienced users complain about having to put up with inexperienced user questions in the threads during the time leading up to release. There is a separate forum location for threads relating to versions not yet released.

---

### Post by amjjawad on 2010-12-11
oldfred is one of the most experienced users in this forum but because he's an advanced user, sometimes, his posts seem a bit complicated/hard to understand. He's a great support indeed. I suggest you go back and read his posts carefully.

If you're not willing to do so, then allow me to jump in and share my opinion.

First thing first, you need to understand the BASICS about GRUB and what is GRUB. There you go:

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
+ use Google if the above links are not enough

Second of all, you need understand that we don't see your machine and we're not sitting in front of your screen but you do. We're doing our best to help and provide the proper advice so that you could fix your issue. However, you need to understand that we can't do everything by ourselves.

Third of all, I think this post has covered everything but that's my opinion:

> **oldfred said:**
> If you are using advance install it gives a  choice on where to install grub and you want it installed to the  external drive.

If you do not install grub at all you will not be able to boot. There  are some fairly complicated (to me) ways to use a windows boot loader.  But if you install grub2 to the external drive and set the external  drive as first in the boot order in BIOS, it will boot grub and grub  will give you a choice of Ubuntu or windows. If you remove external it  will boot from the internal drive and boot your windows.


I had XP on my internal HDD. I installed Ubuntu 10.04 on an external HDD. I had no problems whatsoever and the above post by oldfred does explain my situation. Ubuntu's boot loader (GRUB2) was installed in the MBR of the external HDD. As long as the external HDD is plugged in, I could boot into Ubuntu and choose from GRUB2 Menu whether to login to Ubuntu OR to Windows.
As long as the external HDD is NOT plugged in, I boot normally to Windows XP with no menu or anything else, just booting directly to Windows.

Your BIOS settings need to be updated. You have two options as per the above scenario:
a) Your external HDD will be the first device to boot form > in that case, the external HDD should be plugged in and once GRUB2 menu will show up, you have the choice to choose between Ubuntu and Windows

b) Your internal HDD will be the first device to boot from > in that case, the internal HDD which has ONLY Windows installed on, it will boot and you'll NOT be able to boot into Ubuntu. Why? because the MBR of the internal HDD has only one boot loader which is Windows boot loader and there is no info or anything refer to Ubuntu.


That's the simplest explanation I could come up with ;)

Oh, and I also recommend to read about [MBR]("http://en.wikipedia.org/wiki/Master_boot_record").

---

### Post by amjjawad on 2010-12-11
> **oldfred said:**
> If you are using advance install it gives a choice on where to install grub and you want it installed to the external drive.

If you do not install grub at all you will not be able to boot [COLOR=Red]**Ubuntu**[/COLOR]. There are some fairly complicated (to me) ways to use a windows boot loader. But:

 **if you install grub2 to the external drive and set the external drive as first in the boot order in BIOS, it will boot grub and grub will give you a choice of Ubuntu or windows.** 

If you remove external it will boot from the internal drive and boot your windows.

+1

I added: [COLOR=Red][B]Ubuntu
[/B][COLOR=Black]and I split the text to make it easier to read.

That post said it all. There's nothing more to say :D
[/COLOR][/COLOR]

---

### Post by oldfred on 2010-12-11
Another more complicated site to review.:) It covers how windows Vista (or 7) boots, dual boots and other info on windows. But it helps you to understand computer booting in general.

Since it has a lot of written info, just reviewing the pictures is worth your time. ( And a little less complex).

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by amjjawad on 2010-12-11
> **oldfred said:**
> 
Multibooters, Pictures here worth 1000+ words

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)



Undeniably, this is one of my bookmarks :)

---

### Post by degarb on 2010-12-11
I thank you all for the superb support.  My head is still thrashing from a mere 6 hours of sleep, and foggy (I need sleep, and would kill for it.).  My eyes are foggy, perhaps with tears of gratitude.

The installer simply refused to install the grub in any of the partitions.  Can it install on ntfs?  

When I hit cancel and aborted install, then rebooted into windows, I did need to turn off and on the external drive, as it wouldn't show up in windows.  I am wondering if that could have been the reason the installer refused to install the mbr there in the external sdd5 ext 4 partion...some mechanical problem from the 500 gig partition resize.

After migrating dos and ahk scripts to ubu, it would be nice to use ubu on the main desktop.  That would leave voice dictation and handbraking video, which I only use 250 hours a year, at this point.  I could virtual machine those, perhaps.

---

### Post by oldfred on 2010-12-11
Grub does not like to install to partitions, just MBR. An install to a partition is considered unreliable. With a second drive you have another MBR, so you should only install to the external's drive MBR.

---

### Post by amjjawad on 2010-12-11
My body's battery is very low now and it's time for me to sleep so hope I'll make some sense from what I'll write :)

Just curious, what's the size of your external HDD? is it 500GB? could you please post a screenshot while GParted is on? you know [GParted]("http://gparted.sourceforge.net/"), right? you'll find GParted while you're booting from the LiveCD or LiveUSB here:

System > Administration > GParted.

Once you open it, on the right top corner, you can select the HDD from a drop down list (hope that's the same name in Linux's World :D ). Select your External HDD from there and take a screenshot and upload it here please.
 
Another question. Can you format your external HDD? if yes, then ignore what I wrote above and try to format it and install.

No, you can't install GRUB on an NTFS partition. GRUB will be located in the root partition which is ext4 and a tiny part in the MBR.

If I were you, I would create the partitions I need for Ubuntu before installation. I do that always.

---

### Post by oldfred on 2010-12-11
amjjawad, minor point. 

You can install grub2 to NTFS or FAT32. I use it to boot all my flash drives even though they are formated FAT32. You do not get the full Ubuntu install where you have osprober and update-grub as those are part of Ubuntu. So you have to create your own grub.cfg and manually edit it. 

Just to see if I could do it I downloaded the neo win7 repair CD and installed it to a flash drive, then installed grub2 and created a typical chainboot entry and it worked (I was surprised:)).

---

### Post by amjjawad on 2010-12-11
> **oldfred said:**
> amjjawad, minor point. 

You can install grub2 to NTFS or FAT32. I use it to boot all my flash drives even though they are formated FAT32. You do not get the full Ubuntu install where you have osprober and update-grub as those are part of Ubuntu. So you have to create your own grub.cfg and manually edit it. 

Just to see if I could do it I downloaded the neo win7 repair CD and installed it to a flash drive, then installed grub2 and created a typical chainboot entry and it worked (I was surprised:)).

I'm sorry but that what happens when I don't sleep while I have to :)

Thanks for the reminder and for the explanation, my friend :)
Always like to read your posts.

---

### Post by degarb on 2010-12-12
Hello everyone and thanks again.  (I cannot take screen shot with gparted since I have yet to install a successful Ubuntu.

I suspected a checksum, so I checked it, and scratches.  I decided the alternate cd would be prudent to cover more possible reasons for the failure.  So I downloaded, verified, and ran that cd.

The install went flawless.  It even claimed to modify the windows boot.ini.   However, it didn't.  Reboot and no sign of Linux.

I hope someone can help me add a few lines to the boot.ini to solve this.  

Gateway: p4 2ghz, 1 gig ram, 500 gig ext drive (sdd 4, with two logical ext4 partitions, 30 gig and 2 gig for swap)

boot.ini reads:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by oldfred on 2010-12-12
If you did a standard install, not a wubi it would not modify the boot.ini. Did you do a wubi install. So we can see where you are now (Alt CD is not a liveCD):

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by degarb on 2010-12-12
> **oldfred said:**
> If you did a standard install, not a wubi it would not modify the boot.ini. Did you do a wubi install. So we can see where you are now (Alt CD is not a liveCD):

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

No woobi.  I wanted a backup OS, since a 2002 usb2 pci card going bad blanked out my xp.  I couldn't repair it.  I remembered a vague complaint an hour before it blanked about an unrecognized hub.  So, I yanked it out, fixing xp.  But, it pissed me off that a minor failing pci component could blank out an entire OS into blackness! Had I not seen the bubble, the machine would have been down for who knows how long!

I found this page [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Would this be safe to do?  I told the alt installer to do it's thing.  But it frightens me to much too much with boot loaders, outside of editing the xp boot.ini

I probably won't reboot this xp machine tonight (running some scripts to pull images animate and upload to another server for weather info for several people, recording, serving internal mp3s to other computer, running a business web server)  Then, I will spend next week, into weekend, working and getting yelled at by wife to get off the computer.

---

### Post by oldfred on 2010-12-13
Your link is old and to grub legacy. If you have grub 0.97 that link is ok.

Most installs now are grub2 which uses totally different instructions to reinstall.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by degarb on 2010-12-13
> **oldfred said:**
> Your link is old and to grub legacy. If you have grub 0.97 that link is ok.

Most installs now are grub2 which uses totally different instructions to reinstall.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

In step 5. I don't under stand the definition of sdx (1. what about partition? 2. is this the boot partition in this step or the linux installation?_

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
SIMPLEST - Copy GRUB 2 Files from the LiveCD
This is a quick and simple method of restoring a broken system's GRUB 2 files. The terminal is used for entering commands and the user must know the device name/partition of the installed system (sda1, sdb5, etc). The problem partition is located and mounted from the LiveCD. The files are then copied from the LiveCD libraries to the proper locations and MBR. It requires the least steps and fewer command line entries than the following methods. If for example Windows is on sda1 and Ubuntu is on sda5, and Windows has overwritten the MBR, then the target for grub installation will be /dev/sda5, and the MBR in the boot sector of sda will be re written for grub.
1. Boot to the LiveCD Desktop (Ubuntu 9.10 or later).
2. Open a terminal by selecting*Applications, Accessories, Terminal*from the menu bar.
3. Determine the partition with the Ubuntu installation. The*fdisk*option "-l" is a lowercase "L".
a. sudo fdisk -l
If the user isn't sure of the partition, look for one of the appropriate size or formatting.
Running*sudo*blkid*may provide more information to help locate the proper partition, especially if the partitions are labeled.*The device/drive is designated by*sdX, with*X*being the device designation.*sda*is the first device,*sdb*is the second, etc. For most users the MBR will be installed to*sda, the first drive on their system. The partition is designated by the*Y. The first partition is 1, the second is 2. Note the devices and partitions are counted differently.
4. Mount the partition containing the Ubuntu installation.
sudo mount /dev/sdXY /mnt
Example:*sudo mount /dev/sda1*Note: If the user has a separate /boot partition, this must be mounted to*/mnt/boot*Note: If the user has a separate /home partition, this must be mounted to*/mnt/home. Encrypted home partitions should work.
5. Run the*grub-install*command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
sudo grub-install --root-directory=/mnt/ /dev/sdX
Example:*sudo grub-install --root-directory=/mnt/ /dev/sda
6. Reboot
7. Refresh the GRUB 2 menu with*sudo*update-grub


Step 5 reads::::
5. Run the*grub-install*command as described below. This will reinstall the GRUB 2 files on the mounted partition to the proper location and to the MBR of the designated device.
sudo grub-install --root-directory=/mnt/ /dev/sdX
Example:*sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by degarb on 2010-12-13
In step 7.  I don't understand. (Do I need to do this from live cd?  Won't machine boot to without this?)

:::
7. Refresh the GRUB 2 menu with*sudo*update-grub

::


(Do I need to do this from live cd?  Won't machine boot to without this?)



?

---

### Post by oldfred on 2010-12-13
You mount the partition that you have installed Ubuntu to. Partitions are sda1, sda2, sdb1, sdb2 etc where a or b is drive and 1, 2, 3 are partitions. X refers to drive a, b etc and Y - 1, 2, 3, etc refers to partition in the instructions.

Then you install to the MBR of the drive sda or sdb etc that you want to boot from. Computers only boot from the MBR. Although one boot loader in the MBR can call another boot loader. That is how grub2 boots windows.

the sudo update-grub is a command once in Ubuntu to update the grub menu with all the operating systems on your system. You run that after booting, not from liveCD.

---

### Post by degarb on 2010-12-13
(I have sda1 as my boot and xp.  sdd5 is the ubu.)

* So, to confirm, I would do:
 sudo grub-install --root-directory=/mnt/ /dev/sda
or sudo grub-install --root-directory=/mnt/ /dev/sda1

* Also, I just booted to the live CD.  I found the standard PS2 mouse wasn't working.  Wasn't sure of the work around.  Window has better, more obvious keyboard navigation, even allowing mouse to be moved with key pad.  In the live CD, Tabbing didn't get me around.  Is there a trick to control cursor with mouse?

If I remember, alt f2 brings up run box.  Would I type command.com :-) or terminal?

---

### Post by oldfred on 2010-12-13
No.

If sda1 is windows you destroy your windows. You do not have a separator boot partition do you?


This is the correct one 
sudo grub-install --root-directory=/mnt/ /dev/sda

You almost never have a number at the end fo the grub-install command, unless you are an advanced user, and know that you are booting with another copy of grub from another system and know your system may be less reliable. It will break more often and require reinstall of grub on some changes.

---

### Post by degarb on 2010-12-13
> **oldfred said:**
> No.

If sda1 is windows you destroy your windows. You do not have a separator boot partition do you?


This is the correct one 
sudo grub-install --root-directory=/mnt/ /dev/sda

You almost never have a number at the end fo the grub-install command, unless you are an advanced user, and know that you are booting with another copy of grub from another system and know your system may be less reliable. It will break more often and require reinstall of grub on some changes.

well, since sda is windows and sdd5 is Ubuntu, then I should type:
sudo grub-install --root-directory=/mnt/ /dev/sdd 
right?

---

### Post by degarb on 2010-12-13
right?

---

### Post by Quackers on 2010-12-13
If you want to install grub2 to the mbr of sdd, then yes that would be correct. Then obviously to boot it, you would need to set that drive as first boot device in the bios.

---

### Post by degarb on 2010-12-13
> **Quackers said:**
> If you want to install grub2 to the mbr of sdd, then yes that would be correct. Then obviously to boot it, you would need to set that drive as first boot device in the bios.

Oldfred wrote : "No.

If sda1 is windows you destroy your windows. You do not have a separator boot partition do you?"

So sda1 is wrong, but sda is right and wont destroy ability to boot to windows?

Quackers wrote: "Then obviously to boot it, you would need to set that drive as first boot device in the bios."

 I obviously do not want to fiddle with bios each time I boot in windows, v. linux.  So maybe sdd is wrong. I simply want linux available in boot list if that drive is attached.  If not, I would simply boot to xp as the default OS.  And, I don't want to make any mistakes and make xp non bootable.

The simple design is to add grub into the boot.ini, but that seems to be about a 50 step process.  This is a 7 step process, but the help page is vague on about 3 points, of which this is one.

---

### Post by Quackers on 2010-12-13
Then if sdd5 is your ubuntu /root partition install grub2 to sdd. To boot it you will need to select the usb hard drive as first boot device. However if you have a separate /boot partition don't do it.
If the usb hard drive is not attached at some time, boot should revert to second boot device (HDD would be my guess).

You asked oldfred about installing to sda1. This would have been incorrect in that you would be installing grub2 to a partition rather than the mbr of the disc. That's why he said no. Not because of the drive designation.

---

### Post by degarb on 2010-12-13
> **Quackers said:**
> Then if sdd5 is your ubuntu /root partition install grub2 to sdd. To boot it you will need to select the usb hard drive as first boot device. However if you have a separate /boot partition don't do it.
If the usb hard drive is not attached at some time, boot should revert to second boot device (HDD would be my guess).

That makes sense.

Just to cement: So, it doesn't touch the original boot record.  And it will add option to boot into windows on boot, now on sda. 

Right?

---

### Post by oldfred on 2010-12-13
+1 for Quackers.

If sdd is the external flash that is what you set to boot. It will give you a choice for Ubuntu or windows. Then if it is not plugged in and you have BIOS set to boot internal second, it will boot that. Which is just what you want.

---

### Post by degarb on 2010-12-13
> **oldfred said:**
> +1 for Quackers.

If sdd is the external flash that is what you set to boot. It will give you a choice for Ubuntu or windows. Then if it is not plugged in and you have BIOS set to boot internal second, it will boot that. Which is just what you want.

I just did instructions sudo grub-install --root-directory =/mnt/ /dev/sdd

I checked bios 1. cd 2. external device (which I assumed was flash drive or usb HD, but apparently not usb HD) 3. hd is the boot priority.  
But, still booting to hd only.

I am guessing old machine is not up to task.

What would happen if I  did sudo grub-install --root-directory =/mnt/ /dev/sda ?

---

### Post by wilee-nilee on 2010-12-13
Hey why don't you make it easier for the free help, as it is there are so many posts I'm not going to read everyone to decipher where your at. you have two very knowledgeable helpers and now a 3rd who know this area asking for the script. actually your lucky to have oldfreds help thats who most of us follow. Quackers knows this stuff as well.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.
[B]
Notice that in post #27 oldfred asks for the script.[/B]
> **oldfred said:**
> If you did a standard install, not a wubi it would not modify the boot.ini. Did you do a wubi install. So we can see where you are now (Alt CD is not a liveCD):

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by oldfred on 2010-12-13
+1 on wilee-nilee's running boot script.

I would not suggest installing grub to sda, only because you then have to have the external plugged in to boot.

How old is computer? It was about 4 or 5 years ago they started to update BIOS to boot USB. But not all computers were changed at same time. There are some other ways to boot if necessary.

---

### Post by matt_symes on 2010-12-13
++1; on running the script. Ridiculous. Just run the script.

---

### Post by degarb on 2010-12-13
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: syntax error near unexpected token `newline'
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'



This computer is a 2002 gateway in brand new condition. 

Why would grub not boot if the external drive with UBU not attached?

---

### Post by degarb on 2010-12-13
Unsure why the error at new line.  Perhaps because Live cd?

Oldfred, What is the other way to boot into the Ubu on external drive?  Pardon me if I missed the link if you gave it to me.

---

### Post by Quackers on 2010-12-13
Did you download the boot script to the desktop or is it in Downloads?
Copy/paste it to the Desktop if not, then re-run the command.

---

### Post by degarb on 2010-12-13
> **Quackers said:**
> Did you download the boot script to the desktop or is it in Downloads?
Copy/paste it to the Desktop if not, then re-run the command.


On the desktop.  

I did exactly as instructions.  I also tried cd ubuntu/Destop then ran it, with same error.


I find it hard to believe that grub2 could be so flawed as to not allow xp boot if my UBU external drive isn't attached.

---

### Post by matt_symes on 2010-12-13
Hi> 

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh 
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: syntax error near unexpected token `newline'
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: `<!DOCTYPE html  PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'

He has downloaded the page and not the script.

Kind regards

---

### Post by degarb on 2010-12-13
> **matt_symes said:**
> Hi

He has downloaded the page and not the script.

Kind regards


No This is the sh file.  I will double check.

---

### Post by degarb on 2010-12-13
Okay, correct.  
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   240,107,489   240,107,427   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,934,559   234,934,497   7 HPFS/NTFS
/dev/sdc2         234,934,560   390,716,864   155,782,305   f W95 Ext d (LBA)
/dev/sdc5         234,934,623   390,716,864   155,782,242   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   918,177,797   918,177,735   7 HPFS/NTFS
/dev/sde2         918,179,838   976,771,071    58,591,234   5 Extended
/dev/sde5         918,179,840   972,865,535    54,685,696  83 Linux
/dev/sde6         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3ECC2741CC26F337                       ntfs       =you                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01C38B5C54257960                       ntfs       =you                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01C71EEF4317D1C0                       ntfs       DSK2_VOL1                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        01C71EEF45728AA0                       ntfs       =you                          
/dev/sdc: PTTYPE="dos" 
/dev/sde1        32C4647DC46444E7                       ntfs       Iomega HDD                    
/dev/sde2: PTTYPE="dos" 
/dev/sde5        25a54591-9cca-48a1-8bab-d690bf30b161   ext4                                     
/dev/sde6        92cff236-6963-4d91-8d77-2f94a94c9a21   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/=you              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/=you_             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/=you__            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=6 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect  /NoExecute=OptIn 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional D" /fastdetect/NoExecute=OptIn 

=========================== sde5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a54591-9cca-48a1-8bab-d690bf30b161 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a54591-9cca-48a1-8bab-d690bf30b161 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ecc2741cc26f337
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 01c38b5c54257960
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=25a54591-9cca-48a1-8bab-d690bf30b161 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=92cff236-6963-4d91-8d77-2f94a94c9a21 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


 481.0GB: boot/grub/core.img
 472.5GB: boot/grub/grub.cfg
 470.7GB: boot/initrd.img-2.6.35-22-generic
 480.9GB: boot/vmlinuz-2.6.35-22-generic
 470.7GB: initrd.img
 480.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  c0 5b a1 8d 00 00 80 01  |.........[......|
000001c0  01 00 07 fe 7f 1f 3f 00  00 00 e1 d0 00 0e 00 00  |......?.........|
000001d0  41 20 0f fe ff 00 20 d1  00 0e a1 0c 49 09 00 00  |A .... .....I...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde2

00000000  2e a4 7a ea e5 e0 0f fa  82 46 d4 20 0c 3f 11 b6  |..z......F. .?..|
00000010  b3 1c 81 03 65 c0 19 bb  5c 56 f6 36 93 47 73 0b  |....e...\V.6.Gs.|
00000020  ff f3 38 c4 20 19 09 fe  c1 9e 48 4d 80 b4 18 01  |..8. .....HM....|
00000030  04 89 8a d4 65 79 ee e7  aa 5d b9 7a bd c5 db ac  |....ey...].z....|
00000040  9c 27 a9 a3 a8 1b 37 1d  7d b4 33 77 97 30 21 0e  |.'....7.}.3w.0!.|
00000050  62 1d f4 c4 2c a2 19 fb  10 92 80 08 5b 00 d6 10  |b...,.......[...|
00000060  eb 10 85 c2 64 0f 84 47  5a e5 00 2c 40 75 b9 99  |....d..GZ..,@u..|
00000070  16 aa 0e dc 92 72 ff af  a0 00 a5 6e 15 16 ce 53  |.....r.....n...S|
00000080  ac ba c2 08 a5 0d 40 d3  4d 15 7b a3 ff f3 28 c4  |......@.M.{...(.|
00000090  1a 13 a1 c6 e2 5e 02 d0  09 2a 0a 8f 43 c1 50 5c  |.....^...*..C.P\|
000000a0  34 02 e7 5b 24 2c 29 ce  a8 d3 15 77 53 12 41 b2  |4..[$,)....wS.A.|
000000b0  79 8a a6 df 1f ff d5 a4  0d 29 25 1e fa bb 86 2c  |y........)%....,|
000000c0  d7 30 7d 94 68 a8 a8 94  59 c1 c4 a1 e8 aa 15 dd  |.0}.h...Y.......|
000000d0  25 ae 49 77 ff f3 28 c4  06 0e 39 4a e2 58 01 86  |%.Iw..(...9J.X..|
000000e0  05 39 5b c0 6f b0 6c 95  08 18 a8 d5 59 8e 29 74  |.9[.o.l.....Y.)t|
000000f0  bf fe a9 55 aa 70 be 4f  bf 0c fd fd 93 8c 21 1c  |...U.p.O......!.|
00000100  04 0c 59 89 03 33 17 68  76 66 61 4e 14 e0 b1 5f  |..Y..3.hvfaN..._|
00000110  f9 79 cc 2d 07 67 23 24  07 b8 00 6c ff f3 28 c4  |.y.-.g#$...l..(.|
00000120  08 0e b9 9a c5 be 03 04  15 53 71 4a 37 ea c4 5b  |.........SqJ7..[|
00000130  72 99 e7 63 57 f5 0d d5  b2 b6 fc bc ad d7 76 3e  |r..cW.........v>|
00000140  7f cd a1 b4 14 69 48 fa  3c ac 95 6d dd a6 3e e8  |.....iH.<..m..>.|
00000150  2c fc 47 c5 24 72 7f df  68 b7 e0 00 c0 15 bb ff  |,.G.$r..h.......|
00000160  80 a8 56 08 ff f3 28 c4  08 10 88 46 c0 5e 00 86  |..V...(....F.^..|
00000170  00 ec ea 7b 09 13 01 1e  ff fd 44 cc a0 0a 76 1d  |...{......D...v.|
00000180  09 2c 42 22 63 96 48 b0  2a 19 15 18 b0 d4 44 05  |.,B"c.H.*.....D.|
00000190  c3 82 23 c0 d0 71 f0 d7  2c 14 4d 4d b9 6d d4 09  |..#..q..,.MM.m..|
000001a0  9f ac a4 58 e1 03 e7 37  67 ea 0c 55 ff f3 48 c4  |...X...7g..U..H.|
000001b0  00 1b a3 a6 c9 5e 09 53  a8 06 00 26 bb ff 00 fe  |.....^.S...&....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 42 03 00 fe  |...........pB...|
000001d0  ff ff 05 fe ff ff 02 70  42 03 00 98 3b 00 00 00  |.......pB...;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

```
sdd

---

### Post by matt_symes on 2010-12-13
redundant

---

### Post by degarb on 2010-12-13
The " redundant" mbr in sdb is because I added two old hard drives from other machine with old mbr on sdb.  I had xp on both second and third.  (but only one working xp on c: or sda)The third hd probably has no mbr.  This second dead mbr on sdb is not used by the gateway machine.

---

### Post by degarb on 2010-12-13
what about a boot cd that would load the Ubuntu that is installed?

---

### Post by Quackers on 2010-12-13
Have you set the bios to boot from the 500GB drive?

---

### Post by degarb on 2010-12-13
> **Quackers said:**
> Have you set the bios to boot from the 500GB drive?

Old machine,  It allows the second boot priority to be external, what ever they meant by that in 2002.  Did they have flash drives then?

I am eyeing [http://www.linux.com/archive/feature/113945](http://www.linux.com/archive/feature/113945)  as my next avenue.  That is a very clearly written page.  I am pretty sure the ntldr doesn't care if there is a dead, defunct, os listed in its menu.   So, if the linux drive is removed or dies, then no loss or panic.

---

### Post by matt_symes on 2010-12-13
Hi

> The " redundant" mbr in sdb is because I added two old hard drives from other machine with old mbr on sdb.No. No. No. I posted the script in case you were having problems downloading it. While i was posting it, you posted your results, so my post was redundant:)

Kind regards

---

### Post by wilee-nilee on 2010-12-13
If you want a usb boot assist this is the site. It seems if I can decipher your answer that you have no usb boot.
[http://www.plop.at/](http://www.plop.at/)

If you do have a usb boot then use the per-session key prompt=sde 500 gig drive this gets you to a post bios bootfrom list. My key prompt from power up is f12 yours may be different.

---

### Post by amjjawad on 2010-12-13
> **degarb said:**
> Okay, correct.  
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 [SIZE=3][B]=> Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.[/B][/SIZE]

[SIZE=4]**sda1**[/SIZE]: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

**[SIZE=4]sdb1[/SIZE]**: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

[SIZE=4]**sdc1**[/SIZE]: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

**[COLOR=Red]Disk /dev/sda: 40.0 GB[/COLOR]**, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

**[COLOR=Red]Disk /dev/sdb: 122.9 GB, [/COLOR]**122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   240,107,489   240,107,427   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

[COLOR=Red]**Disk /dev/sdc: 200.0 GB**[/COLOR], 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   234,934,559   234,934,497   7 HPFS/NTFS
/dev/sdc2         234,934,560   390,716,864   155,782,305   f W95 Ext d (LBA)
/dev/sdc5         234,934,623   390,716,864   155,782,242   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

[COLOR=Red]**Disk /dev/sde: 500.1 GB**[/COLOR], 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   918,177,797   918,177,735   7 HPFS/NTFS
/dev/sde2         918,179,838   976,771,071    58,591,234   5 Extended
/dev/sde5         918,179,840   972,865,535    54,685,696  83 Linux
/dev/sde6         972,867,584   976,771,071     3,903,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3ECC2741CC26F337                       ntfs       =you                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01C38B5C54257960                       ntfs       =you                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        01C71EEF4317D1C0                       ntfs       DSK2_VOL1                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        01C71EEF45728AA0                       ntfs       =you                          
/dev/sdc: PTTYPE="dos" 
/dev/sde1        32C4647DC46444E7                       ntfs       Iomega HDD                    
/dev/sde2: PTTYPE="dos" 
/dev/sde5        25a54591-9cca-48a1-8bab-d690bf30b161   ext4                                     
/dev/sde6        92cff236-6963-4d91-8d77-2f94a94c9a21   swap                                     
/dev/sde: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/=you              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/=you_             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/=you__            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=6 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect  /NoExecute=OptIn 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional D" /fastdetect/NoExecute=OptIn 

=========================== sde5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a54591-9cca-48a1-8bab-d690bf30b161 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25a54591-9cca-48a1-8bab-d690bf30b161 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos5)'
    search --no-floppy --fs-uuid --set 25a54591-9cca-48a1-8bab-d690bf30b161
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3ecc2741cc26f337
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 01c38b5c54257960
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd5 during installation
UUID=25a54591-9cca-48a1-8bab-d690bf30b161 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=92cff236-6963-4d91-8d77-2f94a94c9a21 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


 481.0GB: boot/grub/core.img
 472.5GB: boot/grub/grub.cfg
 470.7GB: boot/initrd.img-2.6.35-22-generic
 480.9GB: boot/vmlinuz-2.6.35-22-generic
 470.7GB: initrd.img
 480.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  c0 5b a1 8d 00 00 80 01  |.........[......|
000001c0  01 00 07 fe 7f 1f 3f 00  00 00 e1 d0 00 0e 00 00  |......?.........|
000001d0  41 20 0f fe ff 00 20 d1  00 0e a1 0c 49 09 00 00  |A .... .....I...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde2

00000000  2e a4 7a ea e5 e0 0f fa  82 46 d4 20 0c 3f 11 b6  |..z......F. .?..|
00000010  b3 1c 81 03 65 c0 19 bb  5c 56 f6 36 93 47 73 0b  |....e...\V.6.Gs.|
00000020  ff f3 38 c4 20 19 09 fe  c1 9e 48 4d 80 b4 18 01  |..8. .....HM....|
00000030  04 89 8a d4 65 79 ee e7  aa 5d b9 7a bd c5 db ac  |....ey...].z....|
00000040  9c 27 a9 a3 a8 1b 37 1d  7d b4 33 77 97 30 21 0e  |.'....7.}.3w.0!.|
00000050  62 1d f4 c4 2c a2 19 fb  10 92 80 08 5b 00 d6 10  |b...,.......[...|
00000060  eb 10 85 c2 64 0f 84 47  5a e5 00 2c 40 75 b9 99  |....d..GZ..,@u..|
00000070  16 aa 0e dc 92 72 ff af  a0 00 a5 6e 15 16 ce 53  |.....r.....n...S|
00000080  ac ba c2 08 a5 0d 40 d3  4d 15 7b a3 ff f3 28 c4  |......@.M.{...(.|
00000090  1a 13 a1 c6 e2 5e 02 d0  09 2a 0a 8f 43 c1 50 5c  |.....^...*..C.P\|
000000a0  34 02 e7 5b 24 2c 29 ce  a8 d3 15 77 53 12 41 b2  |4..[$,)....wS.A.|
000000b0  79 8a a6 df 1f ff d5 a4  0d 29 25 1e fa bb 86 2c  |y........)%....,|
000000c0  d7 30 7d 94 68 a8 a8 94  59 c1 c4 a1 e8 aa 15 dd  |.0}.h...Y.......|
000000d0  25 ae 49 77 ff f3 28 c4  06 0e 39 4a e2 58 01 86  |%.Iw..(...9J.X..|
000000e0  05 39 5b c0 6f b0 6c 95  08 18 a8 d5 59 8e 29 74  |.9[.o.l.....Y.)t|
000000f0  bf fe a9 55 aa 70 be 4f  bf 0c fd fd 93 8c 21 1c  |...U.p.O......!.|
00000100  04 0c 59 89 03 33 17 68  76 66 61 4e 14 e0 b1 5f  |..Y..3.hvfaN..._|
00000110  f9 79 cc 2d 07 67 23 24  07 b8 00 6c ff f3 28 c4  |.y.-.g#$...l..(.|
00000120  08 0e b9 9a c5 be 03 04  15 53 71 4a 37 ea c4 5b  |.........SqJ7..[|
00000130  72 99 e7 63 57 f5 0d d5  b2 b6 fc bc ad d7 76 3e  |r..cW.........v>|
00000140  7f cd a1 b4 14 69 48 fa  3c ac 95 6d dd a6 3e e8  |.....iH.<..m..>.|
00000150  2c fc 47 c5 24 72 7f df  68 b7 e0 00 c0 15 bb ff  |,.G.$r..h.......|
00000160  80 a8 56 08 ff f3 28 c4  08 10 88 46 c0 5e 00 86  |..V...(....F.^..|
00000170  00 ec ea 7b 09 13 01 1e  ff fd 44 cc a0 0a 76 1d  |...{......D...v.|
00000180  09 2c 42 22 63 96 48 b0  2a 19 15 18 b0 d4 44 05  |.,B"c.H.*.....D.|
00000190  c3 82 23 c0 d0 71 f0 d7  2c 14 4d 4d b9 6d d4 09  |..#..q..,.MM.m..|
000001a0  9f ac a4 58 e1 03 e7 37  67 ea 0c 55 ff f3 48 c4  |...X...7g..U..H.|
000001b0  00 1b a3 a6 c9 5e 09 53  a8 06 00 26 bb ff 00 fe  |.....^.S...&....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 42 03 00 fe  |...........pB...|
000001d0  ff ff 05 fe ff ff 02 70  42 03 00 98 3b 00 00 00  |.......pB...;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

```sdd


If you have problems with booting because it's an old machine as you say and you have problems with installing GRUB2, etc etc... WHY are you using 4 HDDs and you expect that to work perfectly without any issue whatsoever?
If I were you, I would remove the other two HDDs and make it much more simpler for myself.

I had a huge problem before 3 months just because my BIOS couldn't handle 3 HDDs (2 SATA and 1 IDE). After all, I made it easier for myself and kept only two. After all, the IDE drive is old and I guess it was 20GB or 40GB.

I'm not saying it's impossible as I don't believe in that word but I'm saying: Make it easier for yourself.
You already have 500GB HDD so why you keep the other two if both of them will not be half the size of the HDD??

Just a thought.

---

### Post by oldfred on 2010-12-13
Plop or a bootable CD would work if you are removing the smaller hard drives.

But if you keep a smaller hard drive installed, just install grub to it and boot that drive.

But if your computer is from 2002, it certainly does not boot USB devices, that is not grub's fault. And if it is from 2002 you probably have IDE devices and the BIOS may only allow you to boot primary master. Do you have to set jumpers on the hard drive to define it as master or slave. Or do you have a cable select with connectors that determine boot order. Does BIOS even let you choose which hard drive to boot?

[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

Also if your computer is from 2002, you have a BIOS limit of 137GB or maybe even less. You cannot boot from any partition beyond 137GB on your hard drive as the BIOS was designed back when 80 or 120GB was hard drive size.

---

### Post by degarb on 2010-12-14
Backups and space.  If you only have something backed up once, it isn't backed up.  

I plan to add another 500 gig soon for 5 drives.   I normally only would rely on 3 drives, some dvds both here and at mother's house.  But if you have the drives, use them.  The case handles them all fine and was built for 3 internal drives.  It was the best of its day for gateway.

---

### Post by amjjawad on 2010-12-14
> **degarb said:**
> Backups and space.  If you only have something backed up once, it isn't backed up.  

I plan to add another 500 gig soon for 5 drives.   I normally only would rely on 3 drives, some dvds both here and at mother's house.  But if you have the drives, use them.  The case handles them all fine and was built for 3 internal drives.  It was the best of its day for gateway.

If you have 500GB and planning to add another 500GB so why are you using 40GB?!

Well, as long as you know what are you doing then good luck :)

---

### Post by degarb on 2010-12-14
I tried boot part but it couldn't read from drive

dd in linux just complained command not found.

And setting up the menu.1st in grub 4 dos was not written for real people.

---

### Post by oldfred on 2010-12-14
Who mentioned grub4dos? I have never used it. Grub2 will boot just about anything. 

I have a grub2 install on my win7 repair USB and it boots the windows repair. But that way is not for beginners as you have to manually create your own boot stanza.

Only used menu.lst with grub legacy 2 years ago.

---

### Post by degarb on 2010-12-14
> **oldfred said:**
> Plop or a bootable CD would work if you are removing the smaller hard drives.

But if you keep a smaller hard drive installed, just install grub to it and boot that drive.

But if your computer is from 2002, it certainly does not boot USB devices, that is not grub's fault. And if it is from 2002 you probably have IDE devices and the BIOS may only allow you to boot primary master. Do you have to set jumpers on the hard drive to define it as master or slave. Or do you have a cable select with connectors that determine boot order. Does BIOS even let you choose which hard drive to boot?

[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

Also if your computer is from 2002, you have a BIOS limit of 137GB or maybe even less. You cannot boot from any partition beyond 137GB on your hard drive as the BIOS was designed back when 80 or 120GB was hard drive size.

I was toying with idea of installing grub to sdb and using grub4dos out of boot.ini to load sdb 120 gig, sdc is 200 gig partitioned.  Though I still am stumped on how to set up the menu.1st file. I am confused now.  I guess the idea against using grub in sda 40 gig drive is that xp wont boot if external is broke or removed.  

All cable select, now.

---

### Post by amjjawad on 2010-12-14
I think the OP is confused about lots of basic concepts.

I'd strongly recommend to read more about GRUB2, Booting, etc.

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[www.google.com]("http://www.google.com")


[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

### Post by amjjawad on 2010-12-14
> **degarb said:**
> I am confused now.

PLEASE, refer to my previous post!!!!!

---

### Post by degarb on 2010-12-14
Plop looks interesting but just another, yet lighter, live linux.  And, not a way to boot our beloved Ubuntu.

---

### Post by oldfred on 2010-12-14
If you are using cable select and have an old BIOS, you really only have one MBR to boot from. The BIOS boots from the primary master and that is totally controlled by where the drive is placed on the cable.

Only newer BIOS/motherboards that support SATA have the capability to select boot drive in BIOS. That was about 5 years ago, but some portables stayed IDE longer than desktops. Also there may be some portables that let you boot flash as they removed floppy and everyone complained, so they added USB boot.

---

### Post by degarb on 2010-12-14
My options (?): 

1. Install grub in sda (downside: loose windows if External drive goes out)  Correct?

2. Install grub4dos, which will use ntbldr to start grub4dos,  Then find someone knowledgeable that knows how to get the linux to run.

3. find a fix for why bootpart won't read from any hard drives.

4. figure out how to use dd under linux live cd to write the file.

Or some of these not valid?

---

### Post by degarb on 2010-12-14
After messing for another 3 hours today, I give up.  I am just going to wipe out the Ubuntu partitions.  And put ntfs for wubi

I will install it and test.  I am unsure that it is not a backup for xp.  Since many of my xp installs have failed, but the second install works fine.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

It looks like it may be an alt os outside of xp, but the remove program routine, may just be there to help uninstall it.

---

### Post by degarb on 2010-12-14
Could it be that the main first partition of sde did not have a boot flag?

---

### Post by Quackers on 2010-12-14
Linux doesn't use boot flags.

---

### Post by tededfred on 2011-01-15
quick question in regard to....

[I]I had XP on my internal HDD. I installed Ubuntu 10.04 on an external HDD. I had no problems whatsoever and the above post by oldfred does explain my situation. Ubuntu's boot loader (GRUB2) was installed in the MBR of the external HDD. As long as the external HDD is plugged in, I could boot into Ubuntu and choose from GRUB2 Menu whether to login to Ubuntu OR to Windows.
As long as the external HDD is NOT plugged in, I boot normally to Windows XP with no menu or anything else, just booting directly to Windows.

Your BIOS settings need to be updated. You have two options as per the above scenario:
a) Your external HDD will be the first device to boot form > in that case, the external HDD should be plugged in and once GRUB2 menu will show up, you have the choice to choose between Ubuntu and Windows

b) Your internal HDD will be the first device to boot from > in that case, the internal HDD which has ONLY Windows installed on, it will boot and you'll NOT be able to boot into Ubuntu. Why? because the MBR of the internal HDD has only one boot loader which is Windows boot loader and there is no info or anything refer to Ubuntu.
[/I]

This is the setup that I have, however, when the external drive is off and I try to boot I get Grub "Error 25". The system hangs and does not boot into windows xp by default. I can boot into Ubuntu and Windows XP just fine as long as the external drive is powered on. Any thoughts on getting Windows to boot without having the external drive powered on?

---

### Post by amjjawad on 2011-01-15
> **tededfred said:**
> quick question in regard to....

[I]I had XP on my internal HDD. I installed Ubuntu 10.04 on an external HDD. I had no problems whatsoever and the above post by oldfred does explain my situation. Ubuntu's boot loader (GRUB2) was installed in the MBR of the external HDD. As long as the external HDD is plugged in, I could boot into Ubuntu and choose from GRUB2 Menu whether to login to Ubuntu OR to Windows.
As long as the external HDD is NOT plugged in, I boot normally to Windows XP with no menu or anything else, just booting directly to Windows.

Your BIOS settings need to be updated. You have two options as per the above scenario:
a) Your external HDD will be the first device to boot form > in that case, the external HDD should be plugged in and once GRUB2 menu will show up, you have the choice to choose between Ubuntu and Windows

b) Your internal HDD will be the first device to boot from > in that case, the internal HDD which has ONLY Windows installed on, it will boot and you'll NOT be able to boot into Ubuntu. Why? because the MBR of the internal HDD has only one boot loader which is Windows boot loader and there is no info or anything refer to Ubuntu.
[/I]

This is the setup that I have, **however, when the external drive is off and I try to boot I get Grub "Error 25". The system hangs and does not boot into windows xp by default**. I can boot into Ubuntu and Windows XP just fine as long as the external drive is powered on. Any thoughts on getting Windows to boot without having the external drive powered on?

That's because you have installed GRUB2 in the MBR of your "internal HDD" instead of the MBR of the external one.

To fix this, you need to:
1- Fix the MBR of the internal HDD using **fixmbr** and **fixboot** commands using Windows Disc.

2- Re-install GRUB2 in the MBR of your external HDD.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

In my signature, 3rd Link, there is a complete guide of howto install Ubuntu on an external HDD or USB Drive. Ignore the Wubi part and you can carry on after that.

Good luck ;)

---

