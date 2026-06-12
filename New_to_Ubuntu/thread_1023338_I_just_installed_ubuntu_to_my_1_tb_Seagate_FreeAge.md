---
title: "I just installed ubuntu to my 1 tb Seagate FreeAgent Desk but can't get to run"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by CJM3407 on 2008-12-27
I followed this guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

But now that the cd is gone it just loads vista.  I remember reading something about bios or dual boot mode.  But i wasn't sure how to setup the ability to make the computer ask what os do i want to use.

---

### Post by SlalomMan on 2008-12-27
Did you make sure that GRUB installed okay? It should ask you which thing you want to boot into. If somehow the grub installation got messed up, then you can try reinstalling it from the cd.

Here's a topic that tells you how to do it. It's a bit old, but still relevant. I used it when I went to a triple-boot setup.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by CJM3407 on 2008-12-27
So, do i just use the LIve Desktop cd, and cancel the quick install.  Do the instructions and then start the install.  Or is there no way to setup the computer to ask me which os to use, now.  So, I don't have to reinstall.

---

### Post by SlalomMan on 2008-12-27
What you're going to do is boot from the live cd, and assuming you can connect to the internet, go to the page I linked you to, and follow the instructions to reinstall grub. I can't think of any other reason why grub would not be working.

Let me know if that works or not.

---

### Post by CJM3407 on 2008-12-27
Umm this didn't help and on top of that something seems weird.  I have installed it onto the EHDD but it the ubuntu startup using the cd.  Gives me the original choices of install or try without affecting computer.  So it isn't even running the version I installed.

---

### Post by Sef on 2008-12-27
> Umm this didn't help and on top of that something seems weird. I have installed it onto the EHDD but it the ubuntu startup using the cd. Gives me the original choices of install or try without affecting computer. So it isn't even running the version I installed.

So you installed Ubuntu onto your external hard drive?

---

### Post by CJM3407 on 2008-12-27
yes

---

### Post by CJM3407 on 2008-12-27
Can someone help me with this

---

### Post by SlalomMan on 2008-12-27
I've never tried installing on an external hard drive, but there's a few guides that can help.

[http://ubuntukids.org/blog/?p=69](http://ubuntukids.org/blog/?p=69)

[http://midspot.wordpress.com/2006/10/18/installing-ubuntu-on-an-external-usb-hard-drive/](http://midspot.wordpress.com/2006/10/18/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by silent contender on 2008-12-27
I use this page on the wiki to install Ubuntu 8.04 onto a external HDD:

[https://help.ubuntu.com/community/BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB")

It should be fairly easy to do if your BIOS supports USB boot (it should if your computer is less than ~6yrs. old).  Otherwise, you may have to make a boot CD.

Also, the link SlalomMan post to ubuntukids.org mentioned that Seagate FreeAgent HDD have compatibility problems (you may have already read that though)

Good luck on the install.

---

### Post by caljohnsmith on 2008-12-27
In order to get a clearer picture of your current setup and what it might take to get Ubuntu booting, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your booting problem might be.

---

### Post by CJM3407 on 2008-12-28
Here are the results,  umm i changed my BIOS to where all the USB devices are on the top.  Also, there was  the first section.  Showed Drive 0: (My 200 gb internal) and then Drive 1: (None).

Should that not show up as the Seagate drive.

---

### Post by caljohnsmith on 2008-12-28
> **CJM3407 said:**
> Here are the results,  umm i changed my BIOS to where all the USB devices are on the top.  Also, there was  the first section.  Showed Drive 0: (My 200 gb internal) and then Drive 1: (None).

Should that not show up as the Seagate drive.
According to the results you posted, you have Grub installed just fine to your 1 TB Ubuntu sda drive, so it should be bootable. Therefore, if you are still booting into Vista, you must be still booting your 200 GB Vista sdb drive on start up. From what you say above though it sounds like you might be having problems with your BIOS recognizing the new 1 TB drive. I would comb through your BIOS and check all drive-related settings to see if you can get your BIOS to recognize your 1 TB drive, and if so, you should be able to set the 1 TB drive to boot first. If that doesn't work, you might be able to get a BIOS upgrade from your motherboard manufacturer's website that might correct the problem. 

But since you can boot Vista, if you don't want to mess with your BIOS, I would recommend using [EasyBCD]("http://neosmart.net/dl.php?id=1") within Vista to add Ubuntu to your Vista boot menu. That should be relatively easy, because you all ready have Grub installed to the boot sector of the Ubuntu sda5 partition. Here is a [tutorial]("http://neosmart.net/wiki/display/EBCD/Ubuntu") of how to add Ubuntu to the Vista boot menu. How about giving that a shot and let me know how it goes.

---

### Post by Cicchelli on 2010-11-28
For all the the wonderful FreeAgent and external drive users that want to use there drives for Ubuntu.  I just bought a 500gb drive and spent the day getting Ubuntu to boot off the drive.  The drive is not formatted correctly to boot Ubuntu from the drive through Windows.


1. Get your hand on a USB flash stick and install Ubuntu .  Use the USB installer to load to your USB flash. If you needs question about this let me know and I will assist.
2.With the USB and the FreeAgen hooked up, boot Ubuntu off the flash USB. 
3. Make sure you do a manual install make the primarydrive  for Ubuntu  your FreeAgent HDD. Make sure you save your info because you should reformat.  WARNING: Be carfull in this section make sure you know what drive your FreeAgent is.
4. I used .xfs format and also made a FAT32 partition so I can transfer Windows documentations.
5. Make sure you have a internet connect and proceed with the instruction.

~Note~ I noticed the only partition that Windows notice was the FAT32 and not .XFS

Once everything finally installs(give it sometime) reboot your computer and boot from your FreeAgent.
I seen a lot of people having trouble booting with HDD still hooked up.  Just put it last in the order of loading in the boot menu in your BIOS.

Now I'm working on Multi booting through this and other external drives.
Hope this helps.

---

### Post by Cicchelli on 2010-11-28
For  all the the wonderful FreeAgent and external drive users that want to  use there drives to boot Ubuntu.  I just bought a 500gb drive and spent the  day getting Ubuntu to boot off the drive.  The drive is not formatted  correctly to boot Ubuntu from the drive through Windows.


1. Get your hand on a USB flash stick and install Ubuntu .  Use the USB  installer to load to your USB flash. If you needs question about this  let me know and I will assist.
2.With the USB and the FreeAgen hooked up, boot Ubuntu off the flash USB. 
3. Make sure you do a manual install make the primarydrive  for Ubuntu   your FreeAgent HDD. Make sure you save your info because you should  reformat.  WARNING: Be carfull in this section make sure you know what  drive your FreeAgent is.
4. -I used .xfs format and also made (Important) a  FAT32 partition so Windows will notice the partition.
5. Make sure you have a internet connect and proceed with the instruction.

~Note~ I noticed the only partition that Windows notice was the FAT32 and not .XFS

Once everything finally installs(give it sometime) reboot your computer and boot from your FreeAgent.
I seen a lot of people having trouble booting with HDD still hooked up.   Just put it last in the order of loading in the boot menu in your BIOS.

Now working on Multi booting through this and other external drives.
Hope this helps.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10175170") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10175170")

---

