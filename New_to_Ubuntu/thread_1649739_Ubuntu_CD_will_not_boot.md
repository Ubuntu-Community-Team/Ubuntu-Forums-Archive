---
title: "Ubuntu CD will not boot"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by jchw on 2010-12-20
A few days ago I bought a Ubuntu Manual with a Ubuntu installation CD. I have tried many times to boot up the CD and install Ubuntu with no success. When I booted up Windows I pressed F2 and went into the boot menu and made the CD drive the first priority. This has made no difference and the PC goes straight into Windows and the CD still does not boot up.

In Windows I went to My computer and brought up the CD drive and a Ubuntu screen appeared with three options to do a manual boot, boot later or install a boot helper. I tried to install the boot helper  but that failed with the error message 'could not retrieve the required installation files'. 

I have tried all options to make the CD work with no success. I must have booted up the machine dozens of times in failed attempts and this can't be doing my old machine any good.

Does anyone have any ideas how I could make the CD boot up?

---

### Post by Hippytaff on 2010-12-20
Try downloading the ISO and burning it, you might have a duff CD
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by sikander3786 on 2010-12-20
Welcome to the forums :-)

Are you sure the boot order is correct in the Bios menu? If yes, simply the disc might not be in good health.

In order to check your boot order, if you've got some other bootable disc e.g, Windows, you can try booting that (don't install :-) ) and see if you succeed.

Let us know how that goes. If it is a problem with the disc you own, you might need to download and burn a new image to a disc or a USB drive. And we'll definitely try to help you then :-)

---

### Post by jchw on 2010-12-20
I think the CD is OK because I tried it in my laptop and I can see all the files and folders in it.

I have tested the cd drive in the PC and the drive is working OK and the drivers are up to date.

I have also downloaded the ISO but I was not successful in getting it onto a CD hence the reason I went out and bought the manual. I thought that was going to solve the problem but unfortunately it has not worked that way.

I have a laptop with Ubuntu which works fine but that was  Wubi instal and I was trying this time to use a cd to have a non Wubi version on the PC.

---

### Post by alzie on 2010-12-20
Going back to what sikander3786 said, when you boot does your computer show a boot from cd message?  I'm wondering if when you set the boot order maybe it didn't get saved to the bios.

I've done it, clicking exit instead of save and exit ;)

---

### Post by sikander3786 on 2010-12-20
Files and folders being listed in a CD-ROM disc is not the guarantee that the disc is bootable :-)

Have you got a flash drive? And can you make sure that your system is capable of booting from a USB device? If yes, you can use a USB drive for installation.

---

### Post by Hippytaff on 2010-12-20
> **alzie said:**
> Going back to what sikander3786 said, when you boot does your computer show a boot from cd message?  I'm wondering if when you set the boot order maybe it didn't get saved to the bios.

I've done it, clicking exit instead of save and exit ;)

This is a good point, I have also done this a number of times :roll:

---

### Post by jchw on 2010-12-20
I have just tried a Microsoft Office disc in the PC and it did not boot up. I tried the same disc in my laptop and it did boot up so maybe the problem is by cd drive in the PC.

When I reset the boot order in the PC I saved the changes and when I went in subsequently the order was correct with the CD drive on top.

---

### Post by jchw on 2010-12-20
I do not see a message boot from cd when I boot up, it just goes straight into Windows.

---

### Post by jchw on 2010-12-20
I have got a USB drive so I could try to install that way. 

Would you suggest downloading again from the ISO onto the memory stick?

---

### Post by sikander3786 on 2010-12-20
First of all, check the MD5SUM of your downloaded image in order to save you troubles later. If the MD5SUMs don't match, you probably have got a corrupt image and need to re-download then.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

If ok, use unetbootin to burn the image to USB.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

There are many other USB creation utilities around but the one I never had any problems with is Unetbootin so I recommended it ;-)

Then change the boot order from Bios to boot from the USB drive and hope it boots successfully this time.

Good Luck!

---

### Post by jchw on 2010-12-20
I have just downloaded Ubuntu onto my flash drive and reset the priority of the boot menu to floppy disc. 

When I rebooted it went straight into Windows without booting up from either the USB drive or the cd.

Maybe I should just download Wubi but I was trying to avoid that as I wanted to run Ubuntu in a separate partition and avoid the problems that are occurring with upgrading the Wubi version.

---

### Post by amjjawad on 2010-12-20
> **jchw said:**
> I have just downloaded Ubuntu onto my flash drive and reset the priority of the boot menu to [COLOR=Red]_**floppy disc**_[/COLOR]. 

When I rebooted it went straight into Windows without booting up from either the **USB** drive or the **cd**.


Do you think your machine will boot up from USB and/or CD while BIOS is set to boot up from Floppy? I don't really think so.

Please check [**this**]("http://ubuntuforums.org/showthread.php?p=10257675"). I guess it's the perfect place to start from.

---

### Post by guilleme on 2010-12-20
> **jchw said:**
> I have got a USB drive so I could try to install that way. 

Would you suggest downloading again from the ISO onto the memory stick?

Yes, I'll suggest you to first download the iso and then burn it into the usb to find out if it works. Please tell us how it worked after doing it.
Good luck.

---

### Post by amjjawad on 2010-12-20
> **guilleme said:**
> **burn** it into the usb

You don't "burn" that to USB. USB Drive is not CD/DVD ;)

Edit: This is how you do that the right way: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Check #2

---

### Post by jchw on 2010-12-21
Many thanks to Sikander3786, Amjjawadand others for the ideas and guidance. Please excuse my ignorance on some of these things as this is stretching by computer skills to the limit. Its an interesting learning experience though.

I downloaded Unetbootin but had problems once it was downloaded. I assume I use the Windows version because that is the OS that I have running in the PC at the moment. I selected the Ubuntu version in Unetbootin but it seemed to want to download it into my document file which seemed to be wrong. Should it download it onto the USB drive? I was not able to set the Unetbootin download to go to the USB drive.

I then read Amjjawad's reply about the floppy drive and I see now that I do not have the option in the boot menu for a boot from the USB drive so maybe that option is not going to work anyway.

Looking at the guide Amjjawad sent and in particular some of the images it looks like my boot menu options are very different and this may be why I cannot use the cd to boot up. I will go back into the BIOS and see if I can use Amjjawad's guide to set the boot menu correctly. There are several other suggestions that I have yet to try properly. 

Sorry to be so useless at this and many thanks for the help so far. Another few days should crack it!:D

---

### Post by amjjawad on 2010-12-21
> **jchw said:**
> Many thanks to Sikander3786, Amjjawadand others for the ideas and guidance. Please excuse my ignorance on some of these things as this is stretching by computer skills to the limit. Its an interesting learning experience though.

I downloaded Unetbootin but had problems once it was downloaded. I assume I use the Windows version because that is the OS that I have running in the PC at the moment. I selected the Ubuntu version in Unetbootin but it seemed to want to download it into my document file which seemed to be wrong. Should it download it onto the USB drive? I was not able to set the Unetbootin download to go to the USB drive.

I then read Amjjawad's reply about the floppy drive and I see now that I do not have the option in the boot menu for a boot from the USB drive so maybe that option is not going to work anyway.

Looking at the guide Amjjawad sent and in particular some of the images it looks like my boot menu options are very different and this may be why I cannot use the cd to boot up. I will go back into the BIOS and see if I can use Amjjawad's guide to set the boot menu correctly. There are several other suggestions that I have yet to try properly. 

Sorry to be so useless at this and many thanks for the help so far. Another few days should crack it!:D

Don't apologize, we are all learning here.

No matter what, your BIOS must have the option to boot from CD-ROM or CD-Drive.
I know the BIOS in my guide is different but in general, that option must be there. Try to check the manual of your Motherboard, that will help you a lot.
Even though, if your system does not boot neither from CD nor USB which I doubt, there's a solution for that.

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Did you use UNetbootin to download Ubuntu? I know you should be able to do that but I suggest to do that from here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
In this link, all the instructions you need to create a LiveCD or LiveUSB are there already.

Let us know if you need anything.

Edit:
How old your machine is? can you please tell us what's your hardware specifications?

---

### Post by sikander3786 on 2010-12-21
If you can please post the make and model of your computer, we can try and search the instruction manual regarding the Bios there ;-)

And if you have already downloaded Ubuntu image, what you need to do is download the Unetbootin Windows version, run the .exe and then follow the instructions here.

[http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)

Just select the Disk image, give the path to your ISO, select USB drive (with care) and click OK.

Feel free to ask whatever you need to :-)

---

### Post by migs73 on 2010-12-21
> **jchw said:**
> I think the CD is OK because I tried it in my laptop and I can see all the files and folders in it.


have you tried to boot it in your laptop?

---

### Post by jchw on 2010-12-22
Yesterday I thought I had made a breakthrough as I managed to burn a CD on my laptop downloaded using Ubuntu Wubi which I have been using very successfully for many months. My objective is to install Ubuntu on my old PC but I thought I would test the CD first by trying it on my laptop as I have wanted to move from Wubi to a full upgraded version for some months.

I installed to run alongside existing operating systems and not to overwrite them although I did expand the Ubuntu partion slightly. I have a 500 G hard drive so space should not have been a problem. The installation seemed to go very well but this morning when I restarted the laptop it looks like I have lost Vista, Wubi and the new installed Ubuntu 10.10. It comes up and says error: no such partition. grub rescue_

Before I installed 10.10 on the laptop I made a backup using Deja dup on a flash drive so I am hopeful I may be able to recover the data.

It looks to me like I should reinstall Ubuntu 10.10 on my laptop as if this is a new machine and accept that Vista and Wubi are gone. I will then work to reinstall the data somehow from Deja dup. Vista is no great loss anyway.

On the PC I will give up the idea of installing Ubuntu alongside Windows as if anything goes wrong with it my wife will kill me. With hindsight I should have downloaded the Wubi version which seem a bit safer.

---

### Post by mastablasta on 2010-12-22
sorry to dissapoint you but there is no wubi version. wubi is a programme that installs Ubuntu in Windows using a virtual drive that it creates.
 
you probably didn't loose any data yet. GRUB is Ubuntu's boot loader. windows uses it's own boot loader (MBR). Both easilly be fixed and data accessed. 
 
GRUB info here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
MBR (vista fix) here: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
depending on which system you want to fix first and then continue from there.
 
i seriosuly suggest that next you stay with the installation to see if there are any strange messages. installation of Ubuntu takes only about 15 minutes or so.

---

### Post by jchw on 2010-12-22
Hi mastablasta,

Thanks for those suggestions. I think I need to repair Windows first but this does not look possible as Vista was preinstalled and I do not have an installation disc. I will see if I can find bootrec.exe online and download it.

---

### Post by amjjawad on 2010-12-22
> **jchw said:**
> Hi mastablasta,

Thanks for those suggestions. I think I need to repair Windows first but this does not look possible as Vista was preinstalled and I do not have an installation disc. I will see if I can find bootrec.exe online and download it.

Do you really need Vista?

---

### Post by sikander3786 on 2010-12-22
You can download the Vista Repair Disc here. Its legit ;-)

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by jchw on 2010-12-22
I do not really need Vista but that is where the data is located. If I could rely on retreiving the data from Deju dup then I could safely overwrite Vista and have a clean laptop running just Ubuntu.

That is quite a risk to rely on the backup. I am trying to download the recovery disc from Neo Smart but there is a payment required of $9.75 and the payment was declined by Visa! Amazing while typing this message a call came though and a computer at the other end asked me to verify the last 4 transactions on my Visa account which I have done. Hopefully the download should now proceed. Nothing seems to be easy.

---

### Post by amjjawad on 2010-12-22
> **jchw said:**
> I do not really need Vista but that is where the data is located. If I could rely on retreiving the data from Deju dup then I could safely overwrite Vista and have a clean laptop running just Ubuntu.

That is quite a risk to rely on the backup. I am trying to download the recovery disc from Neo Smart but there is a payment required of $9.75 and the payment was declined by Visa! Amazing while typing this message a call came though and a computer at the other end asked me to verify the last 4 transactions on my Visa account which I have done. Hopefully the download should now proceed. Nothing seems to be easy.

I'm not sure what kind of program is that but each Hard Disk Manufacture has a tool to backup and stuff like that. Did you check that already or not yet?

Yes, if I were you, I would backup my data, format and install Ubuntu.
Vista, I spent the worst year in my life with it. It's history now though.

---

### Post by sikander3786 on 2010-12-22
> I am trying to download the recovery disc from Neo Smart but there is a payment required of $9.75

Torrent download is free. I think you chose the direct download instead.

---

### Post by jchw on 2010-12-22
The NeoSmart payment has now cleared and I have downloaded the repair file but the download file will not burn onto the CD as it comes up with a message medium not ready. I suspect this is back to one of the original problems that the CD drive is not working properly.

I have now lost access to my laptop with a working CD drive because of my own fault so it looks like I cannot make a CD of the repair file. 

I think the only other option is to reinstall Ubuntu on the laptop and delete the windows side and lose all the data. I will then have a data retrieval problems but at least I should have a working system. 

Deja dup was recommended by someone on the forum so there should be a reasonable chance of recovering some if not all of the data.

---

### Post by amjjawad on 2010-12-22
> **jchw said:**
> Deja dup was recommended by someone on the forum so there should be a reasonable chance of recovering some if not all of the data.

Just an advice and you're free to take it or ignore it :)

With all due respect to everyone, I would do some search myself instead of following an advice from someone blindly. This is from real-life experience.
I hope no one would get me wrong and/or feel offended as I don't mean anything bad :)

There's a saying but I can't remember it now. Anyway, I've never heard about Deja dup (Yes, I know I could search google and find out what it is) but what I know is every Hard Drive, it has a tool/software to recover, etc.

Anyway, good luck and I hope you could recover your data.
That's why it's always recommended to backup your data before doing anything ;)

---

### Post by sikander3786 on 2010-12-22
You can also burn that image to a USB drive and boot from it. Post back if you need any help.

And regarding recovery of data, if the partitions are there, you can just mount them under Ubuntu while booted from a Live USB and copy over your data to a safer location.

Were you able to create a Live USB successfully using Unetbootin?

---

### Post by jchw on 2010-12-22
OK, I will have a go at downloading the file into my USB drive.

---

### Post by sikander3786 on 2010-12-22
From Ubuntu Live CD, follow these instructions.

[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

If creating the USB from Windows, you need the USB Tool.

[http://www.lancelhoff.com/usb-creator-for-windows-7/](http://www.lancelhoff.com/usb-creator-for-windows-7/)

[http://store.microsoft.com/help/iso-tool](http://store.microsoft.com/help/iso-tool)

---

### Post by jchw on 2010-12-22
It looks like there is only an option for a USB download with Windows 7. With Vista it looks like you can only burn to a CD or does it not matter?

---

### Post by jchw on 2010-12-22
I have just seen that the repair file for both Windows 7 and Vista can be USB as well as CD.

---

### Post by jchw on 2010-12-22
I have just downloaded the Systemdisc_windows ISO filr onto my USB drive but  it has no effect when run in the laptop. It just comes up with a blue screen with default and says it will boot automatically in 9 seconds then it just loops round.

---

### Post by jchw on 2010-12-22
Wow! Amazing success after all the struggles. I reinstalled Ubuntu in the laptop and wiped out Windows together with all my data in the Wubi installed Ubuntu. I then did a Deja Dup restore and in 30 minutes to an hour all my documents were restored. I had forgotten to install Thunderbird, Wine and a few others and when I did that all my emails appeared in their correct folders. Even the fonts and appearances have been restored. This is such a relief!

I now have Ubuntu 10.10 installed with all my data exactly how it should be. The dreaded Vista has been eliminated and there will be no more dual booting. 

Many many thanks for all your support during this struggle and sorry to be so slow at all this. 

Tomorrow I will put Ubuntu Wubi in the PC because I cannot risk anything going wrong with that installation. At least until I have pursuaded my wife to use Ubuntu and we can drop Windows completely.:D:D:D

---

### Post by amjjawad on 2010-12-22
> **jchw said:**
> Wow! Amazing success after all the struggles. I reinstalled Ubuntu in the laptop and wiped out Windows together with all my data in the Wubi installed Ubuntu. I then did a Deja Dup restore and in 30 minutes to an hour all my documents were restored. I had forgotten to install Thunderbird, Wine and a few others and when I did that all my emails appeared in their correct folders. Even the fonts and appearances have been restored. This is such a relief!

I now have Ubuntu 10.10 installed with all my data exactly how it should be. The dreaded Vista has been eliminated and there will be no more dual booting. 

Many many thanks for all your support during this struggle and sorry to be so slow at all this. 

Tomorrow I will put Ubuntu Wubi in the PC because I cannot risk anything going wrong with that installation. At least until I have pursuaded my wife to use Ubuntu and we can drop Windows completely.:D:D:D

HOOHAA, Well done :D

Just an advice... if you want your wife to try ubuntu, I suggest to create a LiveCD/USB and ask her to try it. Wubi could turn to be another nightmare for you. Yes, I'm so much caution :)

---

