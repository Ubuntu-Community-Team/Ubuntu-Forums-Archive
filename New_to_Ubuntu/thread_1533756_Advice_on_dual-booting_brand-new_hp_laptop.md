---
title: "Advice on dual-booting brand-new hp laptop"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Andavane on 2010-07-18
I have a new HP DM1 1106sa (11.6" screen)
and want to dual boot with Ubuntu 10.04.
HD 320 GB.

When I went to install Ubuntu alongside, I found the following which I have written down by hand as I couldn't print screen it:

===============================
First partition (in blue):
Windows7 (loader)
(/dev/sda1) - 208.7 MB
===============================
Second partition (in green):
(/dev/sda2) - 307.1 GB
===============================
Third partition (in orange)
Windows Vista (Loader)
(/dev/sda3) - 12.7 GB
===============================
===============================


I see nearly all the Hard Drive space is taken up with NTFS partition.
I also attached a shot of what the Windows sees when booted, not showing the first partition.

I want to retain the Wondows 7 as part of the dual-boot, and to have at the ready for when I get frustrated with a few things in Ubuntu such as configuring my printer-scanner every time the distro changes, or for certain things when you can only use Windows, such as my friend's State Bank of India net Banking which only works properly on Internet Explorer.

Apart from these few things, I'd only be on Ubuntu which I infinitely prefer.

I imagine I can shrink the large partition by 150 GB and use that for Ubuntu. Suggestions would be welcome before I proceed.

I imagine I can happily delete the third partition, the vista bootloader?

---

### Post by mike555 on 2010-07-18
Use Win7 to shrink the partition (it might take a few times ,win7 doesn't like to give up space),restart , then with the Ubuntu live cd use gparted to make a partition in the extra space(S) format it and make a note of it's name (SDA2 or what ever)then install Ubuntu to that partition using manual install .........

 The vista area is probably recovery ... also make sure to make recovery discs before you do anything ...

---

### Post by Darkness Des on 2010-07-18
That's almost exactly the same install process I went through on my laptop, but I found out something about Windows 7: It gets pissed if it's not in the MBR and corrupt it. It won't erase GRUB and put itself, it'll just corrupt GRUB and every other boot loader on the system. So I recommend using the alternate install disc and installing GRUB to your Ubuntu partition and use EasyBCD (link below, you need to sign up for their free forums account to download it) to add Ubuntu to Windows 7 Boot loader. 10.04 uses GRUB2, which is auto detected by EasyBCD. Meaning you don't have to memorize the partition number.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by hhh on 2010-07-18
> **Andavane said:**
> I have a new HP DM1 1106sa (11.6" screen)
and want to dual boot with Ubuntu 10.04.
HD 320 GB.
Nice looking netbook!

> I imagine I can shrink the large partition by 150 GB and use that for Ubuntu. Suggestions would be welcome before I proceed.
Yes. Shrink it with GParted and then format it as ext4. It is HIGHLY recommended that you then immediately boot into Windows, which will then recommend a disc check that you should let run and allow Windows to boot normally. After that you can mess with the new empty partition at will. During the installation choose "Install Ubuntu onto the largest free continuous space".

> I imagine I can happily delete the third partition, the vista bootloader?
NO!!! Comparing your screenshot with what you posted from GParted it's a recovery partition... I bet your HP didn't come with a Windows installation disc. Leave it alone.

-edit- I haven't heard about that MBR problem with Windows 7. Others have had success with the normal install method, I'd try that first...
[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)

BTW, defragment the drive before you shrink it.

---

### Post by wilee-nilee on 2010-07-18
> **Darkness Des said:**
> That's almost exactly the same install process I went through on my laptop, but I found out something about Windows 7: It gets pissed if it's not in the MBR and corrupt it. It won't erase GRUB and put itself, it'll just corrupt GRUB and every other boot loader on the system. So I recommend using the alternate install disc and installing GRUB to your Ubuntu partition and use EasyBCD (link below, you need to sign up for their free forums account to download it) to add Ubuntu to Windows 7 Boot loader. 10.04 uses GRUB2, which is auto detected by EasyBCD. Meaning you don't have to memorize the partition number.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

this way is the hardest and most likely to fail method. Using grub as the final bootloader is much easier.

---

### Post by Old_Grey_Wolf on 2010-07-18
If you haven't already, use HP's utility to make a backup of Windows 7 install CDs/DVD. Something can go wrong during an OS install.

---

### Post by Andavane on 2010-07-18
Thanks for the replies, Guys!
No sweat, I haven't done anything yet.
Having a sleep on all this first, then hope to do something tomorrow.
The machine has an external cd/dvd drive, so backups could I guess be made
(although I've never had to use them except on one occasion, when they didn't work! :lolflag: )

Haven't used Windows for 3 years till now, and must say found it very annoying as it tried to force me into doing all sorts of things I didn't want to : one thing, tho: there was a HP thing offering the option of using the net without booting into an OS - no idea what that was. 

I installed the Avast free version antivirus, refused Norton Internet Security ~ What a load of bumph and spam just to use a PC - Sheeesh!

PS: hhh: "Nice looking netbook!"
Thanks - very easy one with limited reach and light at 1½ kg.
Actually it's not a netbook as it has a hard drive - it's an ultramobile notebook or something, offered at a good price at Staples, and for some reason the till rang up £20 less than the displayed price. The checkout girl said: Better make off with it quick!

---

### Post by YesWeCan on 2010-07-18
This is timely. I just discovered Virtual Box: [http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)
[http://www.virtualbox.org/manual/ch01.html#id2606105](http://www.virtualbox.org/manual/ch01.html#id2606105)

This is a Sun/Oracle product. I have created a virtual machine on my 10.04 host and installed and run OpenSuSE 11.3. It is awesome (VB not OpenSuSE) and it takes a lot for me to say that. Check it out as an alternative to faffing about with dual boots and Windows upgrade grub conflicts and so on.

My suggested alternative is that you remove Windows completely, then install Ubuntu then VirtualBox and then install Windows as a "guest" OS. VB makes a virtual hard disk for it which is really just a big image file on your Ubuntu filesystem, wherever you want it. This way you can keep Windows happy in its own creche :p and still have all of its features as if it were running on a dedicated PC. Speed loss depends on your RAM and CPU; RAM allocation is user configurable and so are the number of CPU cores.

Watching Iron Man 2 trailer on SuSE operating within a Ubuntu window. AMD64 4200+ dual core and 2GB RAM only:

---

### Post by Andavane on 2010-07-18
> **YesWeCan said:**
> This is timely. I just discovered Virtual Box: [http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)
[http://www.virtualbox.org/manual/ch01.html#id2606105](http://www.virtualbox.org/manual/ch01.html#id2606105)

This is a Sun/Oracle product. I have created a virtual machine on my 10.04 host and installed and run OpenSuSE 11.3. It is awesome (VB not OpenSuSE) and it takes a lot for me to say that. Check it out as an alternative to faffing about with dual boots and Windows upgrade grub conflicts and so on.

My suggested alternative is that you remove Windows completely, then install Ubuntu then VirtualBox and then install Windows as a "guest" OS. VB makes a virtual hard disk for it which is really just a big image file on your Ubuntu filesystem, wherever you want it. This way you can keep Windows happy in its own creche :p and still have all of its features as if it were running on a dedicated PC. Speed loss depends on your RAM and CPU; RAM allocation is user configurable and so are the number of CPU cores.

Watching Iron Man 2 trailer on SuSE operating within a Ubuntu window. AMD64 4200+ dual core and 2GB RAM only:

Been meaning to try VB for some time ~ although I'm not very good at commands and stuff --
But hey mate! - if I completely remove Windows as you suggest, how can I then install it?  #-o

---

### Post by YesWeCan on 2010-07-18
I installed VB and had SuSE booting  within 10 minutes. It's easier than installing Ubuntu. No special skill required.
But if you don't have a Windows install CD yur stuffed. :x

---

### Post by Nesaskewatch on 2010-07-18
I'm just going to add my two bits here, as I had a nightmare fubar when I resized windows with GParted.  **_Make sure you make two (2) sets of 7 recovery disks!_**  The first set I made had an error and they were useless.  Had a brilliant chap (srs5694) that should be _God_ not told me to make a second set, I would have lost 7!  Also, definitely use the partition management utility in 7 to resize 7.  Failure to comply will result in grief.  As suggested earlier in this thread, keep shrinking it down with the 7 utility until you get the size you want.  7, or any M$ OS for that matter, gets really snotty if you try and take it's space in the sandbox away.  Just be happy if you can reclaim more than half the disk.  Then have fun using GParted to make as many partitions as you wee heart desires!  I've got so many now that I need a map to boot it up.  Just remember to create an extended partition to contain all your new volumes or you will use up the primary drive numbers.  (4 max)

Have fun!

I had put Gedit where GParted should have been.  Brain failing...  Daisy, Daisy.  Give me your answer do...

---

### Post by Andavane on 2010-07-19
> **Nesaskewatch said:**
> I'm just going to add my two bits here, as I had a nightmare fubar when I resized windows with Gedit.  **_Make sure you make two (2) sets of 7 recovery disks!_**  The first set I made had an error and they were useless.  Had a brilliant chap (srs5694) that should be _God_ not told me to make a second set, I would have lost 7!  Also, definitely use the partition management utility in 7 to resize 7.  Failure to comply will result in grief.  As suggested earlier in this thread, keep shrinking it down with the 7 utility until you get the size you want.  7, or any M$ OS for that matter, gets really snotty if you try and take it's space in the sandbox away.  Just be happy if you can reclaim more than half the disk.  Then have fun using Gedit to make as many partitions as you wee heart desires!  I've got so many now that I need a map to boot it up.  Just remember to create an extended partition to contain all your new volumes or you will use up the primary drive numbers.  (4 max)

Have fun!

Oh my, Groan....:(
The very *thought* of doing all that is itself a nightmare! Being physically disabled, I'd have to get in help for changing all those disks. Mmmm feeling stuck. I might phone up the Linux Emporium and ask their advice. I believe this one could be returned for a refund... haven't really done anything with it. Maybe I can post it to them to do, as they do linux all the time...

just wanted a dual-boot machine....

Just gonna creep into the corner for a bit....   :cry:

---

### Post by hhh on 2010-07-19
Isn't this a case of too many cooks spoiling the pot? Have you tried resizing the partition, at least? Have you looked into restoring the Windows MBR if anything messes up? Have you looked into backing up your personal files on an external drive or online? If you can do those three things, you should be all right.

BTW, for restoring the Windows MBR in case of a Grub "Error 17", I've always used Super Grub Disc. Does anyone know if S.G.D. works with the Windows 7 MBR?

---

### Post by Andavane on 2010-07-19
> **hhh said:**
> Isn't this a case of too many cooks spoiling the pot? Have you tried resizing the partition, at least? Have you looked into restoring the Windows MBR if anything messes up? Have you looked into backing up your personal files on an external drive or online? If you can do those three things, you should be all right.

BTW, for restoring the Windows MBR in case of a Grub "Error 17", I've always used Super Grub Disc. Does anyone know if S.G.D. works with the Windows 7 MBR?
So far, I've done nothing.
I know nothing about Windows MBR, as I haven't used Windows for 3 years.
All my stuff is kept in Dropbox, over several machines. Before doing anything on a PC, I go to the Dropbox site and unlink the machine I'm going to work on. Only when everything is working OK, do I relink it. I also keep all my stuff regukarly backed up to an external  hard drive.

> **YesWeCan said:**
> I installed VB and had SuSE booting  within 10 minutes. It's easier than installing Ubuntu. No special skill required.
But if you don't have a Windows install CD yur stuffed. :x

I'll see if I can make recovery CD's , or if not I can order recovery CD's from HP, I think.

Thanks to everyone for all the advice.
I'll be navel-gazing for the next 2 or 3 days while I let all this sink in,  :-|

---

### Post by Andavane on 2010-07-19
Well if it's works as simply as this guide looks, 

[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/]("http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/")

I'll have no complaints.

---

### Post by hhh on 2010-07-19
It should, that's why I posted it.

Report back if you go through with it.

---

### Post by candtalan on 2010-07-19
> **Andavane said:**
>  one thing, tho: there was a HP thing offering the option of using the net without booting into an OS - no idea what that was. 


Linux on the motherboard! LOL

---

### Post by anon.jdh on 2010-07-19
I use Virtualbox every day (at home and work) to test different operating systems, but there are severe limitations. It's not good for more than a "test drive and a tour."

Back to the original question at hand -if you put the Ubuntu disk in the drive while running Windows, you can install using Wubi so that it installs inside of Windows. This provides a dual-boot system, yet the O.S. can be un-installed from within Windows without any causing any trouble.

Another option is to wipe out the HD for a fresh Ubuntu install. This is the option I chose with my daughter's HP netbook. 

Really there's nothing that Windows will give you on that netbook you can't get with Ubuntu's UNE Edition:
[http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition)

---

### Post by colin.p on 2010-07-19
You could also install ubuntu on an external USB drive. It's not as portable, but still not too bad.
You install ubuntu to the external, and install grub to the mbr of the external drive. Then get your computer to boot usb first to get to grub, then into windows or linux.
The thing is, nothing gets installed to your computer at all. Leave the external unplugged and windows doesn't see grub/linux at all.
It's not as fast as an install to the internal drive, but still not too shabby.
I have 10.04 installed that way on my Dell 1545. Still alot faster than my dedicated 10.04 desktop.
I'm in the midst of downloading a bunch of different distros to play with in VB, which is alot easier than dual booting.

Colin

ps, I also had some issues with the atheros wireless card on my daughter's Dell 1012 XP netbook. Installed 10.04 netbook edition and the card worked properly first time, every time. I really don't know why they stopped using ubuntu and went to using XP home...

---

### Post by jfloydb on 2010-07-19
Give WUBI a try.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Nesaskewatch on 2010-07-19
> **Andavane said:**
> 
Just gonna creep into the corner for a bit....   :cry:

Ack!  I'm sorry!  I didn't mean to terrify you!  LOL  ;)

What I wrote isn't nearly as bad as it looks...  And you definitely could get a set of recovery disks from the store you bought the system from.  It's bloody annoying the bandits don't provide them anymore!  Good to have regardless of whether you go dual or not.  The simple method would be to use the partition utility in 7 and shrink 7 as much as it will let you.  The GUI is very easy to use, so don't be intimidated.  After rebooting and verifying that 7 still works, then reboot with the live CD (or DVD) and choose to install to the empty space.  Just select ext4 as the filesystem.  The installer will make things easy.  

Try [here]("http://ubuntuforums.org/showthread.php?t=282018&highlight=dual+boot") for a nice tutorial on partitions.  [This]("http://www.psychocats.net/ubuntu/wubi") is another great place to look for easy instructions for dual booting.

Don't be intimidated!  It's really quite easy.  And lots of folks in here will help should you need it.

Cheers!

---

### Post by Andavane on 2010-07-20
> **Nesaskewatch said:**
> Ack!  I'm sorry!  I didn't mean to terrify you!  LOL  ;)

What I wrote isn't nearly as bad as it looks...  And you definitely could get a set of recovery disks from the store you bought the system from.  It's bloody annoying the bandits don't provide them anymore!  Good to have regardless of whether you go dual or not.  The simple method would be to use the partition utility in 7 and shrink 7 as much as it will let you.  The GUI is very easy to use, so don't be intimidated.  After rebooting and verifying that 7 still works, then reboot with the live CD (or DVD) and choose to install to the empty space.  Just select ext4 as the filesystem.  The installer will make things easy.  

Try [here]("http://ubuntuforums.org/showthread.php?t=282018&highlight=dual+boot") for a nice tutorial on partitions.  [This]("http://www.psychocats.net/ubuntu/wubi") is another great place to look for easy instructions for dual booting.

Don't be intimidated!  It's really quite easy.  And lots of folks in here will help should you need it.

Cheers!

No problem ~ I get bored in the corner, and went through all the stuff again, and was pleased to find I understood it all far better. It all starts *in here* (the brain) and after I'd rebooted it (i.e. the brain, i.e. **slept**) I found it all started to make sense. It musta been the sheer deluge of info which overwhelmed me. Planning to put by ½ day free of commitments for this.

Will think more on't and report back! B-)

=========================================
NB: I heard that a modern day man's cerebral data throughput in ONE DAY is more than that of a rustic worker 400 years ago.

I can well believe it!

---

### Post by Andavane on 2010-07-21
_Recapitulating on the Plan_

OK I will use one of the following 2 methods and have a follow-up question:

(i) Use the windows partitioner to shrink the big partition and make space (after defragging twice) before installing Ubuntu.

(ii) Go into windows and Use Wubi.

My question: 

Will there be any intrinsic difference between the Ubuntus I end up with, bearing in mind that Ubuntu is my main OS (not having used Windows for three years) and that I will only use windows when I have to such as the Indian online banking, or reading DRM e-books which don't allow one to use linux?

---

### Post by candtalan on 2010-07-21
> **Andavane said:**
> 
Will there be any intrinsic difference between the Ubuntus I end up with, bearing in mind that Ubuntu is my main OS (not having used Windows for three years) and that I will only use windows when I have to such as the Indian online banking, or reading DRM e-books which don't allow one to use linux?


One thing I would personally want to avoid at all costs is doing online banking using Windows. If a bank would not allow me to use a secure operating system then I would change my bank.


The WUBI faq is here
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
you may note that having used wubi the installation is less robust in certain circumstances such as sudden loss of power.

---

### Post by Andavane on 2010-07-24
Well guys - this has been a very interesting thread for me, with some fascinating links.

A few points:

Waited for my DVD-R's to arrive and,


> **Nesaskewatch said:**
> I'm just going to add my two bits here, as I had a nightmare fubar when I resized windows with GParted.  **_Make sure you make two (2) sets of 7 recovery disks!_** ...

Not possible, mate ~ Windows only granted permission to make ONE DVD set. Never mind.

> **jfloydb said:**
> Give WUBI a try.

[http://wubi-installer.org/](http://wubi-installer.org/)

Indeed, that's what I did, and it was just about the easiest thing ever, and both system are working fine. Wubi just went and installed itself in a folder called ubuntu; & Windows had no idea what had happened - isn't even aware on booting that anything has happened to the disk ;) It burrowed a ext4 area well, which windows cannot see at all!

Oh just one thing when doing it this way: near the end of the ubuntu installation, you do need to tick that box telling it not to pur a GRUB (it's the scenario where it is running in a special environment). I think if I hadn't ticked it, it would have gone on to make a GRUB, although am not sure.

Of course, this not preclude me from using other methods such as making partitions in the future if I wish, but I see very little reason for doing this atm.

Cheers for all the help!!

PS: > **candtalan said:**
> One thing I would personally want to avoid at all costs is doing online banking using Windows. If a bank would not allow me to use a secure operating system then I would change my bank.


In fairness to the State Bank of India, it was that Java Runtime needed to be installed via a terminal command, and agreeing. Now it's running fine in Firefox.

---

