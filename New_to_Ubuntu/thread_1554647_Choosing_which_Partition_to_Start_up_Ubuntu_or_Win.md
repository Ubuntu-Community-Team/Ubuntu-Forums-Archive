---
title: "Choosing which Partition to Start up: Ubuntu or Windows"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by CaronMargarete on 2010-08-17
I have Ubuntu & Windows partitioned (there's actually 4 partitions on this ACER Aspire 4535 laptop). I got a virus in Windows and decided to upgrade to Windows 7 rather than deal with the problem.
 
I used to be able to choose either Ubuntu or Windows to boot from but now Windows has changed this option to only boot up in Windows. I am not technically minded so I have no idea how to fix it because I can't access Ubuntu at all right now. 
 
How do I get in behind Windows to create this command again??? 
 
Please keep instructions stupidly simple for me... many thanks in advance.
 
Please note that I am also an idiot who didn't back up my ubuntu before upgrading windows so yes, for this I need added caution and a slap on the forehead!

---

### Post by Ozitraveller on 2010-08-17
How to restore Grub boot loader after installing Windows

[http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html)
[http://gamblis.com/2009/10/22/restore-ubuntu-grub-after-installing-windows-7/](http://gamblis.com/2009/10/22/restore-ubuntu-grub-after-installing-windows-7/)
Hope this helps

:)

---

### Post by CaronMargarete on 2010-08-17
Ozitraveller, thanks for the links. 
The first is too technical for me, the second seems easier, however, both require a ubuntu CD which I don't have because I never used a CD to download initially.
 
Any idea how to do it without a CD?

---

### Post by jaycee23 on 2010-08-17
How about creating a bootable live USB drive. Very easy to do but you will need a spare USB pendrive and download a version of Ubuntu.
This link should help
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Ozitraveller on 2010-08-17
> **jaycee23 said:**
> How about creating a bootable live USB drive. Very easy to do but you will need a spare USB pendrive and download a version of Ubuntu.
This link should help
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Agree that would be my suggestion too. :)

---

### Post by CaronMargarete on 2010-08-18
Bonza guys, will give it a go and see how it pans out. Thanks for your support!

---

### Post by CaronMargarete on 2010-08-22
Hi, I've hit a snag trying to get it to boot from the USB.
 
I tried to use pendrive as an installer, it wouldn't work so I used [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net) as suggested from another site. It seemed to work and I have files now on my USB, however I cannot boot.
 
When I go into the BIOS and try to change the boot order I get weird characters and I either hit Enter and Windows boots or I have to turn off the computer and change the boot order again to reaccess Windows. 
 
I've attached a screen shot of the USB files. The wubi file seems to bring up an error when I open it, Windows7 doesn't like it.
 
Can anyone see what's wrong with these files?

---

### Post by fmfrisch on 2010-08-22
I would try to download a new copy of the .iso as it seems some of the files might be corrupt. Then install it over to a USB drive and try again. If you are using Unetbootin i would go to the ubuntu website download the iso by myself and then tell Unetbootin to install that iso. That rather than just selecting the OS out of the list as there might be a chance Unetbootin remembers that it already have the ISO and uses the same corrupt file again

---

### Post by Ozitraveller on 2010-08-22
I did this 3 times over the weekend with any problems. 

So does the usb work and did the checksum work on the iso?

---

### Post by CaronMargarete on 2010-08-26
Ok, for the life of me I can't figure out what I'm doing wrong! 

I have downloaded the iso directly from the ubuntu website, no dramas there. I used Unetbootin and directed it to take the downloaded iso from my desktop. Again no dramas.   

I rebooted and selected it to load from the usb, it gave me this short, garbled line of characters, weird shaped lines and nonsense, when I hit Enter it boots windows.

I open the usb drive and check out the files. I open wubi and it runs fine. I select the Demo & Full Installation button, it gives me three options, Reboot now, I want to manually reboot later, and Help me boot from CD. 

When I selected Reboot now, of course, it did exactly that but rebooted windows. When I selected the second option nothing happened. And the third option it tells me that a previous installation was detected and needs to be removed before continuing. 

Obviously I don't want to uninstall the previous option because that's what I'm trying to get access to again so I'm having trouble understanding how to just open it to trial so I can change the commands as per the gamblis link recommendation above.

What's the deal? Can someone please step me through this???

---

### Post by bcbc on 2010-08-26
> **CaronMargarete said:**
> Ok, for the life of me I can't figure out what I'm doing wrong! 

I have downloaded the iso directly from the ubuntu website, no dramas there. I used Unetbootin and directed it to take the downloaded iso from my desktop. Again no dramas.   

I rebooted and selected it to load from the usb, it gave me this short, garbled line of characters, weird shaped lines and nonsense, when I hit Enter it boots windows.

I open the usb drive and check out the files. I open wubi and it runs fine. I select the Demo & Full Installation button, it gives me three options, Reboot now, I want to manually reboot later, and Help me boot from CD. 

When I selected Reboot now, of course, it did exactly that but rebooted windows. When I selected the second option nothing happened. And the third option it tells me that a previous installation was detected and needs to be removed before continuing. 

Obviously I don't want to uninstall the previous option because that's what I'm trying to get access to again so I'm having trouble understanding how to just open it to trial so I can change the commands as per the gamblis link recommendation above.

What's the deal? Can someone please step me through this???

So you installed using Wubi originally? In other words, from within Windows. If you still have the c:\ubuntu\disks\root.disk file you probably can recover all your files from your original wubi install.

Also, those links to reinstall grub won't help you since you need the windows bootloader for wubi, you've just lost the option to boot Ubuntu from within the windows bootmanager.

First off, confirm that the root.disk is still there, and back it up somewhere safe (outside the c:\ubuntu directory). If you reinstall or uninstall ubuntu it will be deleted.

Second, what version of Ubuntu were you running before?

---

### Post by CaronMargarete on 2010-08-29
> **bcbc said:**
> So you installed using Wubi originally? In other words, from within Windows. If you still have the c:\ubuntu\disks\root.disk file you probably can recover all your files from your original wubi install.

Also, those links to reinstall grub won't help you since you need the windows bootloader for wubi, you've just lost the option to boot Ubuntu from within the windows bootmanager.

First off, confirm that the root.disk is still there, and back it up somewhere safe (outside the c:\ubuntu directory). If you reinstall or uninstall ubuntu it will be deleted.

Second, what version of Ubuntu were you running before?

Honestly, I don't know because I didn't do the original install. A friend did with a CD. I know it was an old version because we then updated it to Koala and since then (& before windows xp **** itself) I updated it to lucid through the update manager. I am fairly sure that my friend changed the boot up after install. 

Let's start with working out how my system is presently configured and understand how to find this root.disk info you need. I don't know what I'm looking for or how to do it. 

What I do know is that the partition with ubuntu is still there because in Windows 7 I can see how the drives are partitioned, what I can't do is get into it, and that's what I want the option to do.

Ideas?

---

### Post by bcbc on 2010-08-29
Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by CaronMargarete on 2010-09-04
> **bcbc said:**
> Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

Bcbe, I cannot boot into the USB drive remember? If I could I wouldn't need to do this bootinfoscript.

I've tried to be really clear about what I've done in previous posts, all I need to know is how to access the ubuntu I've already got on my laptop.

How do I do this?

---

### Post by jtarin on 2010-09-04
Do as bcbc recommends> So you installed using Wubi originally? In other words, from within Windows. If you still have the c:\ubuntu\disks\root.disk file you probably can recover all your files from your original wubi install.

Also, those links to reinstall grub won't help you since you need the windows bootloader for wubi, you've just lost the option to boot Ubuntu from within the windows bootmanager.

First off, confirm that the root.disk is still there, and back it up somewhere safe (outside the c:\ubuntu directory). If you reinstall or uninstall ubuntu it will be deleted.

Second, what version of Ubuntu were you running before?

---

### Post by bcbc on 2010-09-04
I'm still a little confused. From this comment it seems you have a direct install.
> **CaronMargarete said:**
> What I do know is that the partition with ubuntu is still there because in Windows 7 I can see how the drives are partitioned, what I can't do is get into it, and that's what I want the option to do.

But this message is only given for wubi installs.
> **CaronMargarete said:**
> And the third option it tells me that a previous installation was detected and needs to be removed before continuing. 

So I am not really clear on what is happening. It's possible that the wubi message is regarding your earlier attempt to use it to boot in 'demo and full installation' mode. But we need to be sure before trying to find a solution.

Please search your computer and confirm that there is no 'root.disk' file anywhere.

---

### Post by CaronMargarete on 2010-09-04
> **bcbc said:**
> I'm still a little confused. From this comment it seems you have a direct install.

But this message is only given for wubi installs.

So I am not really clear on what is happening. It's possible that the wubi message is regarding your earlier attempt to use it to boot in 'demo and full installation' mode. But we need to be sure before trying to find a solution.

Please search your computer and confirm that there is no 'root.disk' file anywhere.

I know I don't get it either. I just completed a search it came up with nothing. 

From what I've been reading this afternoon I think I can use the Super Grub Disk to get me into Ubuntu again and from there I should be able to go into the terminal and use the commands gamlis recommends to fix the grub.

I also think the problem has come from not have a CD available and using a USB. If I can bypass the USB then it will hopefully be all-good. Going to attempt it now, fingers crossed!

---

### Post by CaronMargarete on 2010-09-11
> **CaronMargarete said:**
> I know I don't get it either. I just completed a search it came up with nothing. 

From what I've been reading this afternoon I think I can use the Super Grub Disk to get me into Ubuntu again and from there I should be able to go into the terminal and use the commands gamlis recommends to fix the grub.

I also think the problem has come from not have a CD available and using a USB. If I can bypass the USB then it will hopefully be all-good. Going to attempt it now, fingers crossed!

Got the Super Grub to install but I still cannot get into Ubuntu from there. The commands seem to run but then do nothing. I feel like I'm missing a step but for the life of me don't know what!

I need help either getting super grub to work or to get it off to try something else? 
Ideas?

---

### Post by jtarin on 2010-09-11
Before this disaster happened can you remember what the boot screen looked like. Black with 2 or more entries. Do you remember the entries and in what order? I'm still trying to determine whether this is WUBI or full install.Are you certain it was a Grub screen because if I'm not mistaken WUBI uses Windows loader.My signature has a link to EasyBCD which can modify the Win7 loader to boot WUBI or if Grub is on the Linux partition it can boot it.

---

### Post by CaronMargarete on 2010-09-11
> **jtarin said:**
> Before this disaster happened can you remember what the boot screen looked like. Black with 2 or more entries. Do you remember the entries and in what order? I'm still trying to determine whether this is WUBI or full install.Are you certain it was a Grub screen because if I'm not mistaken WUBI uses Windows loader.My signature has a link to EasyBCD which can modify the Win7 loader to boot WUBI or if Grub is on the Linux partition it can boot it.

The initial screen on boot up used to be a black screen with white writing, it listed approx 10 Ubuntu entries- I believe they were auto recovery entries because I think they changed each day or so. At the bottom of this list was the Windows access.

I honestly have no idea what used to be on my system. I've been really lost ever since this started. It used to look exactly like the GNU Grub screen shot shown on wikipedia if that helps. 

Is there a way you can work with me to step through this because it's all going over my head now, each time I read more information I get a little more overwhelmed. I'm sure it's not that difficult but it's frustrating because I have limited wifi access at the mo...

Thanks in advance jtarin.

---

### Post by jtarin on 2010-09-11
If Grub is _not_ in the MBR but in the / of the Linux partition this will help.

[An illustrated guide to EasyBCD]("http://neosmart.net/forums/showthread.php?t=6350")
(This is in the EasyBCD forum)

---

### Post by CaronMargarete on 2010-09-11
> **jtarin said:**
> If Grub is _not_ in the MBR but in the / of the Linux partition this will help.

[An illustrated guide to EasyBCD]("http://Make%20sure%20you%20use%20EasyBCD%20ver%202.xx")
(This is in the EasyBCD forum)

Hi, sorry the link you've provided didn't work, however I've since downloaded EasyBCD from your signature. I have to say this looks too easy to be true! 

The steps I've followed thus far:

1. Checked out the overview which listed Windows 7 and Super Grub
2. Went to Add New Entry button, clicked Linux/ BSD tab and selected GRUB Legacy (because I wasn't sure), left NeoSmart Linux as is and chose the partition which held Ubuntu previously. I didn't select the MBR box because I wasn't sure and don't know how to check, from here I hit Add Entry, and here we are...

I am concerned about not knowing if GRUB is installed in the MBR... in any case I have to turn my laptop off now so I guess I'm about to find out... fingers crossed and many thanks for your insight!

---

### Post by CaronMargarete on 2010-09-11
> **CaronMargarete said:**
> Hi, sorry the link you've provided didn't work, however I've since downloaded EasyBCD from your signature. I have to say this looks too easy to be true! 

The steps I've followed thus far:

1. Checked out the overview which listed Windows 7 and Super Grub
2. Went to Add New Entry button, clicked Linux/ BSD tab and selected GRUB Legacy (because I wasn't sure), left NeoSmart Linux as is and chose the partition which held Ubuntu previously. I didn't select the MBR box because I wasn't sure and don't know how to check, from here I hit Add Entry, and here we are...

I am concerned about not knowing if GRUB is installed in the MBR... in any case I have to turn my laptop off now so I guess I'm about to find out... fingers crossed and many thanks for your insight!

Argghhh!!! Just tried a restart... I'm missing something, and I'm sure it's small...

So I got a black screen with white writing that asked me to choose between Windows 7 and NeoSmart Linux. I chose Linux and it came back to the same screen again ... what's missing?

When I deleted and then re-added the linux with the MBR box checked it seemed to automatically towards the C:/ drive, but it's not located there- see previous screenshots...

For now I've deleted it again until you can advise...

---

### Post by boog321 on 2010-09-11
Grub was probably installed to the MBR, and when you installed windows 7 it overwrote the mbr.

Have you tried to write your new iso to a cd and boot from it, instead of the usb pendrive? That may help, and you could reinstall grub.

---

### Post by jtarin on 2010-09-11
You shouldn't be so impatient. My link is fixed in the post for the illustrated guide.You will have to scroll down some where the guy writes about Ubuntu10.04
BTW Ubuntu 10.04 uses Grub2.
Use Grub2 and check the box _is not installed in the MBR_ because its not. 
Your looking at the Win7 loader if Grub was there it has been overwritten by Win7 and unless you did a reinstall or repaired Win7 loader it was never there. 
There is also in the drop-down menu I believe a selection for WUBI try that next if GRUB2 doesn't work.
If and when GRUB2 needs to be reinstalled, reinstall to the "/" of the Linux partition.You will need the ability to boot from a Live CD environment (USB will do)to reinstall.

---

### Post by CaronMargarete on 2010-09-12
> **jtarin said:**
> You shouldn't be so impatient. My link is fixed in the post for the illustrated guide.You will have to scroll down some where the guy writes about Ubuntu10.04 
BTW Ubuntu 10.04 uses Grub2. Use Grub2 and check the box _is not installed in the MBR_ because its not. Your looking at the Win7 loader if Grub was there it has been overwritten by Win7 and unless you did a reinstall or repaired Win7 loader it was never there. There is also in the drop-down menu I believe a selection for WUBI try that next if GRUB2 doesn't work.

Hi Jtarin,

Sorry if I seem impatient but I live in Cambodia with no tech service help available, limited net access and weeks (now) of trying to find a solution. I appreciate you.

I did as you've suggested, that is used both grub2 and wubi, however I get this on a black screen with white writing:

GRUB4DOS 0.4.5b 2010-07-25, Mem: 631K/1789m/0M, End: 34C688
[Minimal BASH-like line editing is supported. ... (info added about TAB functionality) ... ]

grub>

At this point I need to restart the system. 

> If and when GRUB2 needs to be reinstalled, reinstall to the "/" of the  Linux partition.You will need the ability to boot from a Live CD  environment (USB will do)to reinstall.

I don't want to reinstall Ubuntu, that would completely wipe everything on the previous Ubuntu. In an earlier post I mentioned not backing up (I know! I know!) because Win7 reinstall wasn't done by me so I wasn't aware it would overwrite the MBR. Now I'm left knowing the information is still there but unable to access it. 

I simply want to access what's already there. Is this possible with EasyBCD? If so how specifically?

Many thanks in advance.

---

### Post by jtarin on 2010-09-12
> GRUB4DOS 0.4.5b 2010-07-25, Mem: 631K/1789m/0M, End: 34C688
[Minimal BASH-like line editing is supported. ... (info added about TAB functionality) ... ]This tells me it's a WUBI install. Okay now go back to EasyBCD remove any previous entries by using "Edit Boot Menu" then "Add new entry" Linux/BSD select "Type" Grub 4Dos.Click add entry.Go to the "Setup Bootloader" page in EasyBCD, and select "Install the Windows Vista/7 Bootloader to the MBR" then press "Write MBR":

[How-to: Recover files from Wubi install with LiveCD]("http://neosmart.net/forums/showthread.php?t=5004&highlight=wubi")

---

### Post by CaronMargarete on 2010-09-16
> **jtarin said:**
> This tells me it's a WUBI install. Okay now go back to EasyBCD remove any previous entries by using "Edit Boot Menu" then "Add new entry" Linux/BSD select "Type" **Grub 4Dos**.Click add entry.Go to the "Setup Bootloader" page in EasyBCD, and select "Install the Windows Vista/7 Bootloader to the MBR" then press "Write MBR":

[How-to: Recover files from Wubi install with LiveCD]("http://neosmart.net/forums/showthread.php?t=5004&highlight=wubi")

Hi Jtarin,

I removed all previous entries, and as instructed went to add the new entry: Grub4dos, however, this *type* is not in the drop down menu. I have Grub (legacy), grub2, Lilo, Free BSD, and WUBI.

I considered that the type may still have been wubi but the name needed to be changed to grub4dos so I tried this and followed the write to MBR instructions. After the restart I saw the grub4dos line on boot but when I selected it I got the same grub4dos line as before.

Ideas?

---

### Post by jtarin on 2010-09-16
Do it again a select WUBI

---

### Post by CaronMargarete on 2010-09-16
> **jtarin said:**
> Do it again a select WUBI

Yes, this is what I tried just before and I got the same message:

GRUB4DOS 0.4.5b 2010-07-25, Mem: 631K/1789m/0M, End: 34C688
[Minimal BASH-like line editing is supported. ... (info added about TAB functionality) ... ]
grub>

Next? ;)

---

### Post by jtarin on 2010-09-16
Try Grub2

---

### Post by jtarin on 2010-09-18
OK I'm still not clear if your have WUBI or not. If you still have your Ubuntu CD boot with it and select "Try" from the Ubuntu menu when it gets to the desktop run Gparted from the menu System>Administrator>Gparted. Don't make any changes while in Gparted. Take a screenshot and post.Close Gparted and reboot.

---

### Post by CaronMargarete on 2010-09-18
> **jtarin said:**
> OK I'm still not clear if your have WUBI or not. If you still have your Ubuntu CD boot with it and select "Try" from the Ubuntu menu when it gets to the desktop run Gparted from the menu System>Administrator>Gparted. Don't make any changes while in Gparted. Take a screenshot and post.Close Gparted and reboot.

Sorry, I don't have the CD. When I got Ubuntu it was loaded by a friend and I never received a copy of the disk.

I've downloaded a new version and will burn it to a disk asap. Can we use it?

---

### Post by jtarin on 2010-09-18
Yes we can.

---

### Post by CaronMargarete on 2010-09-22
> **jtarin said:**
> Yes we can.

[FONT=&quot]Hey Jtarin, 

Downloaded the netbook version of Ubuntu from their site, hoping that's the right one for my ACER Aspire 4535. Bought both a CD-R and a DVD-R disk to burn. Tried to burn on both, the DVD didn't work at all and the CD-R seemed to work, although I'm not confident it's done right- is there a way to list the files so that you can tell me? 

When I tried to reboot it seems like the EasyBCD is conflicting with the start up, even though I've deleted all but Win7 from the list. It won't boot from the disk no matter what I try. 

If I go into the files and open the wubi it asks me if I'm sure I want to uninstall, as though it wants to uninstall my previous version, clearly not ideal.

How do I get the disk to boot so I can run Gparted as you asked?
[/FONT]

---

### Post by perspectoff on 2010-09-22
Acer Aspire with ATI Radeon Graphics?

You may have trouble with booting the Lucid LiveCD due to the graphics.

If it doesn't boot up properly, you might have to use an older version of Ubuntu to fix the Grub, or else fix the graphics problems.

---

### Post by jtarin on 2010-09-22
> **CaronMargarete said:**
> [FONT=&quot]Hey Jtarin, 

Downloaded the netbook version of Ubuntu from their site, hoping that's the right one for my ACER Aspire 4535. Bought both a CD-R and a DVD-R disk to burn. Tried to burn on both, the DVD didn't work at all and the CD-R seemed to work, although I'm not confident it's done right- is there a way to list the files so that you can tell me? 

When I tried to reboot it seems like the EasyBCD is conflicting with the start up, even though I've deleted all but Win7 from the list. It won't boot from the disk no matter what I try. 

If I go into the files and open the wubi it asks me if I'm sure I want to uninstall, as though it wants to uninstall my previous version, clearly not ideal.

How do I get the disk to boot so I can run Gparted as you asked?
[/FONT]

#1.You would have been happier downloadingthe regular edition, but nevermind the one you have should work. 
#2. In the bios set your CD drive as the first bootable device
#3. EasyBCD shouldn't be interfering with your bootup as it is in actuality the Windows loader.

---

### Post by CaronMargarete on 2010-09-24
> **jtarin said:**
> #1.You would have been happier downloadingthe regular edition, but nevermind the one you have should work. 
#2. In the bios set your CD drive as the first bootable device
#3. EasyBCD shouldn't be interfering with your bootup as it is in actuality the Windows loader.

I changed the boot command in setup when I first burned the disk, it didn't boot from the disk. The laptop starts with the ACER screen and then goes immediately to the black screen/ white writing page that you'd usually use to select between Win7 and Ubuntu (or other OS). 

So even though I have the boot changed to load from CD it's not working. I can only go into Win7. And this is what I meant by the conflict. Perhaps it's not EasyBCD but it's something preventing the computer from loading the CD.

I'm not confident that the netbook version downloaded properly so I'm going to download the regular version today and burn the disk again.

In the meantime, how do I remove that initial boot up screen?

---

### Post by jtarin on 2010-09-24
> In the meantime, how do I remove that initial boot up screen?With EasyBCD or a Win7 disk.

---

### Post by CaronMargarete on 2010-09-25
> **jtarin said:**
> With EasyBCD or a Win7 disk.

Finally got my computer to try to boot from the CD however it didn't work, I'm thinking the files weren't downloaded or burned correctly.

This is the message I got on start up:

> ISOLINUX 3.63 Debian- 2008-07-15 Copyright (c) 1994-2008 H. Peter Anvin
isolinux: Disk error 80, AX = 4200, drive 9F
Boot failed: press any key...

I'm still attempting to download the other version of Ubuntu but find it takes a long time here and is constantly pausing because of the low quality of internet available.

Have you got an idea what this error means?

---

### Post by jtarin on 2010-09-25
> **CaronMargarete said:**
> Finally got my computer to try to boot from the CD however it didn't work, I'm thinking the files weren't downloaded or burned correctly.

This is the message I got on start up:



I'm still attempting to download the other version of Ubuntu but find it takes a long time here and is constantly pausing because of the low quality of internet available.

Have you got an idea what this error means?That more than likely is a burn error. Try a 4x speed to burn and make sure you verify your downloaded iso with md5 checksum. If you keep having this problem and your internet connection is poor you might consider ordering a free cd.

---

### Post by CaronMargarete on 2010-10-01
Hey, off the cuff, is there any way that the Win7 install completely wrote over all my partitions and wiped the previous ubuntu completely off my system?

I've looked in the disk management on win7 and can still see the original partitions but have just noticed that against the 256GB partition I had set aside for ubuntu it says 100% free, which it definitely shouldn't!

Am I looking at a complete write off here? Please tell me not!!! 

By the way, I'm still trying to download Ubuntu- Cambodian internet isn't exactly reliable...

---

### Post by jtarin on 2010-10-01
An installation of Win7 contains it self to one partition. It does not install itself to multi-partitions.Windows reporting Linux drives as free or unknown file system is normal.

---

### Post by CaronMargarete on 2010-10-01
> **jtarin said:**
> An installation of Win7 contains it self to one partition. It does not install itself to multi-partitions.Windows reporting Linux drives as free or unknown file system is normal.

Thanks Jtarin, this is a relief to hear but I'm not sure that it makes a difference now.

Try as a I might I can not get Ubuntu to download, the service here is really poor and it keeps timing out.

I've considered getting it mailed but it takes 10weeks in normal countries, here that would equate to about 6months because the mailing system is unreliable.

I do have one version (no idea which one or if it downloaded correctly) that is on my C drive however Windows tells me the installation wasn't done correctly and when it attempts to correct it prompts me to uninstall ubuntu, which I first thought would wipe the previous version on the other partition but now I'm not sure.

Have decided to just go ahead and do do as it instructs. I have to suck it up and realise that although I've lost quite a bit of data I haven't lost over 100G's as I first feared because my last sync was a month before this all started!

Here goes jumping off the bridge, may the water be deep! Thank you again for you help.

---

### Post by Darkness Des on 2010-10-01
Windows 7, for some random reason, installs to 2 partitions: A small one for it's loader, and then the one it actually identifies as a hard drive.

---

### Post by jtarin on 2010-10-01
A WUBI uninstall _will not_ wipe out an Ubuntu install on another partition. If you don't want to download a torrent of Ubuntu, which is usually the fastest way....then consider using jDownloader....it's in the repositories.You will not lose your download with this....however I usually go to their site and download the newest they have as a .deb file and install. You need to have Sun Java installed as jDownloader is a Java application.

---

### Post by jtarin on 2010-10-01
> **Darkness Des said:**
> Windows 7, for some random reason, installs to 2 partitions: A small one for it's loader, and then the one it actually identifies as a hard drive.
Please provide a link for that assertion.

---

### Post by oldfred on 2010-10-02
A new install of windows 7 will have a small 100MB boot/recovery partition that is hidden and the main install. It was so you could encrypt the main partition as the boot partition cannot be encrypted. If you install win7 to an existing NTFS partition overwriting XP or Vista it will not create the extra 100MB boot partition and all the boot files are in the main partition. 

We see this with many windows installs from the boot info script. You really need to get a working liveCD or USB flash working so you can repair or run tests on your system.

 Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by jtarin on 2010-10-02
> **oldfred said:**
> A new install of windows 7 will have a small 100MB boot/recovery partition that is hidden and the main install. It was so you could encrypt the main partition as the boot partition cannot be encrypted. If you install win7 to an existing NTFS partition overwriting XP or Vista it will not create the extra 100MB boot partition and all the boot files are in the main partition. 

We see this with many windows installs from the boot info script. You really need to get a working liveCD or USB flash working so you can repair or run tests on your system.

 Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I would still like to see a link to this assertion of a small partition as I have done many new installs of Win 7 and have never encountered this unless it is something done by an OEM possibly.

---

### Post by CaronMargarete on 2010-10-02
> **jtarin said:**
> I would still like to see a link to this assertion of a small partition as I have done many new installs of Win 7 and have never encountered this unless it is something done by an OEM possibly.

Hi, not sure if this shot will show you what you need but it's of my disk management. 

The unallocated space never used to be. I did that thinking that I could reallocate the space to my c drive to increase it, only to realise that it didn't do what I wanted so I never went back to fix it. Feel free to tell me how... ;)

---

### Post by jtarin on 2010-10-02
If you have nothing on there you can just format it and use it for what you want? In Windows a right-click onit will give you oprtions, but if you think have something on there you want to keep and its Linux files you can try to rescue them using the Ubuntu CD. You tell me "exactly" what you want to do and I'll offer suggestions. BTW that post about the small partition and assertion was not directed at you. It was a question for the other members who are speaking of a "hidden" partition.

---

### Post by CaronMargarete on 2010-10-02
> **jtarin said:**
> If you have nothing on there you can just format it and use it for what you want? In Windows a right-click onit will give you oprtions, but if you think have something on there you want to keep and its Linux files you can try to rescue them using the Ubuntu CD. You tell me "exactly" what you want to do and I'll offer suggestions. BTW that post about the small partition and assertion was not directed at you. It was a question for the other members who are speaking of a "hidden" partition.

:D I realise that it wasn't directed for me, but I thought you'd like to see a system that has the extra partition. I forgot to mention that I didn't add a fourth partition, from my knowledge I've only had three before.

I wanted to add the now unallocated space to my c drive to increase it. There's definitely nothing on it because as mentioned I only had three before. Incidentally I really only need 2 so if we can take the two small drives- the unallocated one (3.72GB) and the 18.63GB one- and allocate them to c drive that will increase the windows partition.

I'm not familiar with doing this so let me know how. 

In addition, I have now downloaded JDownloader but I'm not familiar with how to use it. I've never needed such a program before. 

Sorry to seem so clueless, I really appreciate your support.

---

### Post by jtarin on 2010-10-02
To use your unallocated space for your C:\ drive you should use [Gparted]("http://gparted.sourceforge.net/documentation.php"). You can access it by booting from your Ubuntu CD. Do you have anything else on the other two partitions that you want to keep? If not delete all three partitions you will then have two partitions. One containing Windows, your C:\ drive and the other will be unallocated space. resize your Windows partition then create any other partitions you want.Do one step at a time then reboot for the next step. Before you resize your Win partition defrag the partition to move all data to the front. Read the documentation on Gparted thoroughly.After you have resized you Win Partition and before you create any other partitions,it would be a good idea to boot in to Windows a couple of time so it can do a disk check.

As for jDownloader here is a [tutorial]("http://tehparadox.com/forum/f28/jdownloader-tutorial-356876/")...a little dated but it will help with the 
basics.I didn't have a tutorial when I learned to use it.Just Google. 

Any help needed just PM or post back.

---

### Post by CaronMargarete on 2010-10-05
> **jtarin said:**
> OK I'm still not clear if your have WUBI or not. If you still have your Ubuntu CD boot with it and select "Try" from the Ubuntu menu when it gets to the desktop run Gparted from the menu System>Administrator>Gparted. Don't make any changes while in Gparted. Take a screenshot and post.Close Gparted and reboot.

Jtarin,

Today is a beautiful day! I finally got a full download and a successful burn and have successfully trialed Ubuntu and successfully taken a screenshot of Gparted as you requested 2weeks ago!

So... now what do I need to do? :D

---

### Post by CaronMargarete on 2010-10-09
> **Ozitraveller said:**
> How to restore Grub boot loader after installing Windows

[http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html](http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html)
[http://gamblis.com/2009/10/22/restore-ubuntu-grub-after-installing-windows-7/](http://gamblis.com/2009/10/22/restore-ubuntu-grub-after-installing-windows-7/)
Hope this helps

:)

Jtarin,

I've attempted to follow the instructions on the second link (the first being too advanced for me) and after I type sudo grub I get "command does not exist". Also tried sudo grub2 for sht's'n'giggles and got the same result.

Not sure now how to use the new live CD to access the partition win7 overwrote. Suggestions?

---

### Post by jtarin on 2010-10-09
Scroll down to ["Method #3 CHROOT" ]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")and use.

---

### Post by CaronMargarete on 2010-10-10
> **jtarin said:**
> Scroll down to ["Method #3 CHROOT" ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")and use.

Hey Jtarin, this was way too technical for me so I decided to just throw in the towel and install the new version.

Turns out that's all I needed to do to access the previous version!!! 

So technically I now have two Ubuntu OS and Win7 but I couldn't care less because I have my original system back fully intact. I can't believe it was as simple as that!

Thank you soooo very much for all your continual support! It's been a huge relief to have someone on board. Thought you might see this photo as interesting as I'd never seen your logo anywhere else until this...

---

### Post by jtarin on 2010-10-10
> **CaronMargarete said:**
>  Thought you might see this photo as interesting as I'd never seen your logo anywhere else until this...Quite unbelievable. :)

---

