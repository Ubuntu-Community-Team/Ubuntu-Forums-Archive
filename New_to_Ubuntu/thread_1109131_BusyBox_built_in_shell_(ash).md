---
title: "BusyBox built in shell (ash)"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by jcm1107 on 2009-03-28
When installing Ubuntu I get the following screen

Loading, please wait...



BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

and if I type help I get commands but I have tried alot of them with no luck.Please help!!!! oh and I erased and reformated my hard drive because I thought my windows xp was the problem. I am new to linux and want to try it this is my first try.

---

### Post by Bachstelze on 2009-03-28
This usually happens when Ubuntu and your hardware are not good friends. Things you can do:

-> Search the forums or Google to see if someone has had the same problem as you on the same hardware. Maybe they solved it and shared the solution.

-> Try the Alternate CD, with the text installer. Less pretty, but also less likely to fail on you.

-> Try Ubuntu 9.04 beta. Better have a beta Ubuntu than no Ubuntu at all. ;)

---

### Post by jcm1107 on 2009-03-28
I have searched these forums for the last week and alot of peple have this problem but either don't know how to solve it or their solutions didn't work for me. My hardware is cd/dvd burner floppy drive wd 320 gig ide hard drive with an adapter to sata because my mother board only hase one ide connector and I used that on the cd/dvd burner I have an xfx630i motherboard and I left the cards in the pci slots soundblaster sound card and linksys wireless adapter I am using on board vidieo

---

### Post by presence1960 on 2009-03-28
> **jcm1107 said:**
> I have searched these forums for the last week and alot of peple have this problem but either don't know how to solve it or their solutions didn't work for me. My hardware is cd/dvd burner floppy drive wd 320 gig ide hard drive with an adapter to sata because my mother board only hase one ide connector and I used that on the cd/dvd burner I have an xfx630i motherboard and I left the cards in the pci slots soundblaster sound card and linksys wireless adapter I am using on board vidieo

Here is a quote from a thread :
> original promlem was the bios
i did reasearch and learned to use the f6key and type in the cod "all_generic_ide" this allows meto run the live cd. 

Here is the link : [http://ubuntuforums.org/showthread.php?p=6940688#post6940688](http://ubuntuforums.org/showthread.php?p=6940688#post6940688)

---

### Post by jcm1107 on 2009-03-29
could you tell me where to type "all_generic_ide" at? also I have found that other people get this same busy box message and there are several different common problems that cause it. Also I found that at the first screen you see after you select laguage if you press F6 and delete "quiet splash and then try to install it shows what is being checked and I found that it kept saying ultra-DMA/32 end request: I/O error over and over also it said sector 128 logical block 16
and I think that is my hard drive. Hope this might help someone or mabe help someone help me. I still haven't solved my problem just getting closer I hope.

---

### Post by jcm1107 on 2009-03-29
I also found that the busybox we are getting is part of the non graphical type only boot. It looks like a dos program you have to type everything I tryed booting from that and the busybox looks like an extension of some sort of that. You can hit Esc in at the first installation screen to get to the non graphical boot screen.

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> could you tell me where to type "all_generic_ide" at? also I have found that other people get this same busy box message and there are several different common problems that cause it. Also I found that at the first screen you see after you select laguage if you press F6 and delete "quiet splash and then try to install it shows what is being checked and I found that it kept saying ultra-DMA/32 end request: I/O error over and over also it said sector 128 logical block 16
and I think that is my hard drive. Hope this might help someone or mabe help someone help me. I still haven't solved my problem just getting closer I hope.

Boot the Ubuntu Live CD. Immediately after you select language press F6. you will see a line at the bottom of your screen. change "quiet splash" to > splash all_generic_ide then press enter.

---

### Post by jcm1107 on 2009-03-29
I just tried the all_generic_ide and got the same error. I have tried changing from ide to raid in bios also with no luck

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> I just tried the all_generic_ide and got the same error. I have tried changing from ide to raid in bios also with no luck

Sorry it didn't work. I had the same problem with Mint 5 and that did the trick. Did you try downloading the text based installer? At this point it can't hurt to try a new avenue.

---

### Post by jcm1107 on 2009-03-29
Ubuntu 8.1 is what I am having trouble installing. I just succesfully installed ubuntu 7.1 and I am updating files on it now I thought I might try that and then upgrade to 8.1 if I can later. Is this possible? and also why did the older version install with no problems and the new version would not install at all? someone needs to fix the problem that everyone is having. I have read ALOT of forums and alot of people are having the same thing as me happen. For different reasons it seems.Such as the all generic ide fix works for some but not others switching to raid in bios works for some and nothing worked for me yet. I still want to try the newest version if someone can help, please?

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> Ubuntu 8.1 is what I am having trouble installing. I just succesfully installed ubuntu 7.1 and I am updating files on it now I thought I might try that and then upgrade to 8.1 if I can later. Is this possible? and also why did the older version install with no problems and the new version would not install at all? someone needs to fix the problem that everyone is having. I have read ALOT of forums and alot of people are having the same thing as me happen. For different reasons it seems.Such as the all generic ide fix works for some but not others switching to raid in bios works for some and nothing worked for me yet. I still want to try the newest version if someone can help, please?

you might want to try 8.04 since 7.10 is coming up on it's end of life. it will no longer be supported I believe come April 18. Hardy 8.04 is a LTS and very stable.

---

### Post by jcm1107 on 2009-03-29
I also forgot to mention I did try installing from the text based installer, it was an option at the first instalation screen after language

---

### Post by jcm1107 on 2009-03-29
I am going to try that because I saw it is the long term support version but I already have the other burned to a cd and I saw that other people have the same problem with the 8.04 Lts version

---

### Post by jcm1107 on 2009-03-29
I just tried the old version to see if it would work. This is my first time trying to use anything but windows. I have used windows since 1998 and I know my way around a computer, but I have never used linux before

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> I just tried the old version to see if it would work. This is my first time trying to use anything but windows. I have used windows since 1998 and I know my way around a computer, but I have never used linux before

I would go with Hardy 8.04. As long as you are willing to try, it will all be worth it. Tis how it goes installing an OS on a machine. Most people who use Windows have the OS pre-installed for them so they never experience what it is like to install an OS. Sometimes it can be a lot of work.

---

### Post by jcm1107 on 2009-03-29
I have installed win98 and xp many times over and know my way well through that and this installation is not much different. I know computers pretty well and have erased and reformatted my hard drive before several times because of viruses now I am good at getting rid of viruses without having to do that but I wanted to try linux. Also I herd that it is more secure and you don't get viruses as bad as windows. I can't wait to see if this is true.

---

### Post by jcm1107 on 2009-03-29
Also I will try the hardy 8.04 could you give me a good download location? if not I can search for it

---

### Post by jcm1107 on 2009-03-29
Also do I need to erase the 7.1 to install or can I upgrade to it? and what is the easiest way to run linux any version with windows xp? would I want to install linux first or xp first? witch one should I use to partition my hard drive? and what file system is best for linux? ntfs,fat 32, ect...

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> Also do I need to erase the 7.1 to install or can I upgrade to it? and what is the easiest way to run linux any version with windows xp? would I want to install linux first or xp first? witch one should I use to partition my hard drive? and what file system is best for linux? ntfs,fat 32, ect...

Here is where I download my iso from, but there are other locations. [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

I would do a clean install, that is just my opinion and preference. just install over 7.10 or if you want format the partitions first. I use ext 3 for linux. it is a journalized file system and really hardly fragments at all. Linux can read NTFS but you don't want to use that as your Linux file system. So you will be able to access your windows partitions but windows can not natively access Linux partitions. There are a couple drivers you can install to do this, but I don't like it given the security of windows. If you are in windows and have a breach then your Linux files are accessible. Granted no system changes can be made to your linux partition but your sensitive personal info can be accessed from windows. That's why I don't use that driver.

---

### Post by jcm1107 on 2009-03-29
could you tell me more about how I should do my hard drive partitions? Like install linux before I have xp installed. And should I use first or second partition for linux. is ext 3 a file system like ntfs and fat32 how do I get and use ext 3? do I do that before I install xp? Also I have the hardy 8.04 running right now and it is the only OS on my computer. It gave me the option to upgrade to it from 7.1 automatically. I know I have alot of questions but I am new to running two OS systems and new to linux. I want to tell presence1960 a big thanks for all your help!!!!!!!!!

---

### Post by presence1960 on 2009-03-29
> **jcm1107 said:**
> could you tell me more about how I should do my hard drive partitions? Like install linux before I have xp installed. And should I use first or second partition for linux. is ext 3 a file system like ntfs and fat32 how do I get and use ext 3? do I do that before I install xp? Also I have the hardy 8.04 running right now and it is the only OS on my computer. It gave me the option to upgrade to it from 7.1 automatically. I know I have alot of questions but I am new to running two OS systems and new to linux. I want to tell presence1960 a big thanks for all your help!!!!!!!!!

Ideally you should create your partitions first, then install windows to one partition. This will allow you to install Ubuntu without having to defrag windows.

Since Hardy is already installed, you should create a partition for XP using gparted from the Live CD or download the gparted CD from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

Please be aware that since you already have Ubuntu installed when you reinstall Windows it will wipe your GRUB (bootloader). But this is no problem, it is a simple process from the Ubuntu Live CD to restore GRUB.

I would suggest that download and burn a 8.04 Live CD (and the gparted CD if you choose that option). Then run this command from terminal>  sudo fdisk -l (that is a lowercase L not the number one)and post the output to this thread. Before you go ahead and look at partitioning you want to have all your ducks in a row and we want to see exactly what is on your hard drive as far as partitions and file systems go. sudo fdisk -l will provide that info for us.

---

### Post by jcm1107 on 2009-03-30
I have downloaded the Gparted and burned to cd I am downloading the ubuntu 8.04 right now and going to burn to cd when done. Just one question about what you said to do. You said run Sudo fdisk -l from terminal. What termanal do you mean? Do you want me to reboot from gparted cd? or run it in linux and what terminal? Sorry I am new to all this linux and dual os system stuff

---

### Post by jcm1107 on 2009-03-30
how do I put a screen shot on here? I took one after I did what you said to do with the fdisk and I can't get it to go in this message I see the icon to insert image but it asks for http url

---

### Post by jcm1107 on 2009-03-30
justin@Ubuntu:`$ sudo Fdisk -l
[sudo] password for justin:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be6c9

   Device Boot     Start      End       Blocks     Id    System
/dev/sda1              1     19830     159284443+   c     W95  FAT32 (LBA)
/dev/sda2   *      19831     38133     147018847+  83     Linux
/dev/sda3          38134     38913       6265350    5     Extended
/dev/sda5          38134     38913       6265318+  82  Linux swap /Solaris
justin@Ubuntu:`$

---

### Post by jcm1107 on 2009-03-30
the above is the result of me running what you said. I had to type it all in. I could't get a screen shot from the linux computer to come up on this message. Also just so you know I only want two partitions to run windows xp and linux. It apears I have more partitions than that. And also another dumb question, how do I change the screen resolution to above 640x480 I want 1440x900  60 Hz

---

### Post by presence1960 on 2009-03-30
> **jcm1107 said:**
> the above is the result of me running what you said. I had to type it all in. I could't get a screen shot from the linux computer to come up on this message. Also just so you know I only want two partitions to run windows xp and linux. It apears I have more partitions than that. And also another dumb question, how do I change the screen resolution to above 640x480 I want 1440x900  60 Hz

That will do for now. Next time highlight the text and right click and choose copy. Add the text to a post in the forums by right clicking and choosing paste where you want to place the text. This is called copy & paste.

Is the first partition your windows recovery partition? Let's clarify what you want to do. I think you want to dual boot correct? If so your best bet is to repartition your drive and install XP first. Then add Ubuntu. If you want to keep your current Ubuntu we can still do that too. We can get it set up the first way without extended partitions.

For the resolution go to System-> Preferences-> Screen resolution. If your native resolution isn't available you want to install the proprietary driver for your video card. We'll get to that bridge if necessary. First see if you can change the resolution as suggested.

Ok < i just saw you want only 2 partitions. You will have a minimum of 3: windows, /, swap.  and you might want to keep that one partition if it is a windows recovery partition. But that will be 4 so no need for an extended partition. You have plenty of room on that HDD. get back to me on how to partition that HDD so you can proceed with the install.

Sorry for the delay but I was at work.

---

### Post by fr0gg on 2009-03-30
hey, presence, wasn't sure if i should start a new thread, so sorry if i'm interrupting the current process you're involved in with jcm, but i'm having the same issues as he was when he first started. The BusyBox, please wait..is what i'm referring to. I tried the all_generic_ide command, i think it stopped prematurely as i get a "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)" as the last displayed entry..
I have just reformatted, installed XP, and am now trying to dual boot Ubuntu, already installed and partitioned it, but can't get to boot correctly..
thanks for any help you may be able to provide, and again, sorry if this is perceived as an intrusion.

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> hey, presence, wasn't sure if i should start a new thread, so sorry if i'm interrupting the current process you're involved in with jcm, but i'm having the same issues as he was when he first started. The BusyBox, please wait..is what i'm referring to. I tried the all_generic_ide command, i think it stopped prematurely as i get a "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)" as the last displayed entry..
I have just reformatted, installed XP, and am now trying to dual boot Ubuntu, already installed and partitioned it, but can't get to boot correctly..
thanks for any help you may be able to provide, and again, sorry if this is perceived as an intrusion.

When you say "can't get it to boot correctly" be more specific- exactly what happens? Does Ubuntu boot, does windows boot? what messages if any do you see? Does GRUB menu come up?

I have a few things going on at home currently but I will be checking back in from time to time tonight. But nevertheless follow up on this and there are literally many people who can help you on this forum. it doesn't matter who helps as long as it gets done.

No, this is not an intrusion for me. I can't speak for anyone else.

---

### Post by fr0gg on 2009-03-30
Alright, thank you. Yes, the GRUB menu comes up, XP boots fine, but like i said, when i select Ubuntu, is when the:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

screen comes up, and does not cease to display, to be specific, so Ubuntu never boots.

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> Alright, thank you. Yes, the GRUB menu comes up, XP boots fine, but like i said, when i select Ubuntu, is when the:

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

screen comes up, and does not cease to display, to be specific, so Ubuntu never boots.

I have only had this problem in Mint 5, which is the equivalent of hardy 8.04. What worked for me was to edit my menu.lst file like so:

```
title		Linux Mint x64, kernel 2.6.24-23-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=/dev/sdb2 ro splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-23-generic
```

Please take note, the only changes you should make are on the kernel line. Where yours says ro quiet splash change it to > ro splash all_generic_ide Do not edit anything else **GOT THAT?** Yours will say Ubuntu not Mint.

It did the trick in Mint 5, but never used it in Ubuntu because I never had to. Make sure you save the file, close it and reboot. If you don't have a backup copy of menu.lst I would create one before editing.

---

### Post by fr0gg on 2009-03-30
This is my first time really working with Linux, so bear with me heh, so i boot into the Live CD and create this file? I'm also not sure which specifics i would enter for Ubuntu in place of Mint..
Thanks mate.

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> This is my first time really working with Linux, so bear with me heh, so i boot into the Live CD and create this file? I'm also not sure which specifics i would enter for Ubuntu in place of Mint..
Thanks mate.

fr0gg, just to make sure it would work in ubuntu I changed my ubuntu entry in my file, i rebooted and it worked when I chose Ubuntu. First : **when you do get in the file and edit, the only thing you are going to change is located on the kernel line for ubuntu. Do not edit the recovery mode or memtest entries! at the end of that line (ubuntu) it should say ro quiet splash, you will change that to ```
ro splash all_generic_ide
``` DO NOT CHANGE ANYTHING ELSE!!!**

Boot into the Live CD. Open a terminal -> Applications > Accessories > Terminal....enter in terminal:```
gksu nautilus
``` when nautilus opens find your Ubuntu partition on the left pane. Select it. Do not choose Filesystem as this is for the Live CD. Go to boot (folder) > grub (folder) > menu.lst (file). open that file and change what i said to change. Again do not edit or change anything else except what I suggested. Save the file. Close all windows and restart. This should get you going. 

I gave you the GUI way since you are so new. The only terminal you need to use is to open nautilus with root priveleges. you may want to print this out for reference when you do this.

---

### Post by fr0gg on 2009-03-30
Right, thanks for providing the gui version of instructions..still know very few commands. However, i'm not seeing any other directories apart from File System..does this mean Ubuntu did not fully install or something?
I see root, Desktop, File System, Network, and then the flash drives i have inserted..

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> Right, thanks for providing the gui version of instructions..still know very few commands. However, i'm not seeing any other directories apart from File System..does this mean Ubuntu did not fully install or something?
I see root, Desktop, File System, Network, and then the flash drives i have inserted..

try root. BTW did you install Ubuntu to your hard disk fully or did you use wubi (install ubuntu inside windows)?

give me a minute or two, i am going to boot my Live CD. brb

---

### Post by fr0gg on 2009-03-30
Root contains no Boot folder. I'm almost certain i selected a full install..

---

### Post by jcm1107 on 2009-03-30
in reply to frOgg the nothing fixed my problem with Ubuntu 8.1 I am now Using Ubuntu 8.04

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> Root contains no Boot folder. I'm almost certain i selected a full install..

I booted into my live CD and ran ```
gksu nautilus
``` in terminal. All my partitions and external drives are showing in the left pane. I don't know why yours are not. I have a bunch too.  I have Mint / , /home, ubuntu/,
XP, win storage, usb backup, and all my flashcard readers in the left pane along with root and filesystem. So I am at a loss as to why your partitions are not showing in the pane in nautilus.

---

### Post by presence1960 on 2009-03-30
> **jcm1107 said:**
> in reply to frOgg the nothing fixed my problem with Ubuntu 8.1 I am now Using Ubuntu 8.04

Maybe you should try 8.04 Hardy fr0gg. it is a LTS and will be supported even after support for 8.10 Intrepid ends.

---

### Post by presence1960 on 2009-03-30
> **jcm1107 said:**
> in reply to frOgg the nothing fixed my problem with Ubuntu 8.1 I am now Using Ubuntu 8.04

you are up & running now I take it? GREAT!!

---

### Post by fr0gg on 2009-03-30
hmm, strange. Well just to make sure i'm doing the basic step correctly, changing boot order to boot to CD, and Ubuntu prompts for which language, I just let it sit until the timer ticks away, and then it boots me into Live session user, right? Yea, no partitions are showing up, XP or Ubuntu..

---

### Post by jcm1107 on 2009-03-30
I am willing to uninstall Ubuntu and repartition my hard drive I think I would rather do that. The other partitions I created with a program I got with the hard disk before I had any OS on the hard drive. I made two partitions one for linux and one for xp but when I installed the linux I think I messed up and created more. I would like to start fresh so I know my system is in good shape. I also liked what you said about xp not being able to mess with the linux OS that sounds good, and I guess it could be bad too if you wanted to transfer files, but I have an external hard drive. Oh and I have a licenced xp cd that I purchased along time ago. So I have everything ready. to completly erase the hard drive and repartition what would I do? boot from the gparted cd?

---

### Post by presence1960 on 2009-03-30
> **fr0gg said:**
> hmm, strange. Well just to make sure i'm doing the basic step correctly, changing boot order to boot to CD, and Ubuntu prompts for which language, I just let it sit until the timer ticks away, and then it boots me into Live session user, right? Yea, no partitions are showing up, XP or Ubuntu..

after the language choice choose try ubuntu without installing or with no changes to your computer

---

### Post by presence1960 on 2009-03-30
> **jcm1107 said:**
> I am willing to uninstall Ubuntu and repartition my hard drive I think I would rather do that. The other partitions I created with a program I got with the hard disk before I had any OS on the hard drive. I made two partitions one for linux and one for xp but when I installed the linux I think I messed up and created more. I would like to start fresh so I know my system is in good shape. I also liked what you said about xp not being able to mess with the linux OS that sounds good, and I guess it could be bad too if you wanted to transfer files, but I have an external hard drive. Oh and I have a licenced xp cd that I purchased along time ago. So I have everything ready. to completly erase the hard drive and repartition what would I do? boot from the gparted cd?

before we do that, back up all your data you don't want to lose onto that external drive. Also that sda1 partition is that windows or the windows recovery partition? it is formatted FAT which leads me to think it is a recovery partition.

---

### Post by jcm1107 on 2009-03-30
Well I have had the Ubuntu runing for a little while now but I was just wanting to know the best way of installing it and xp at the same time with as few partitions as it takes like one for eace and the boot partition or whatever. I just got off of work. I work second shift

---

### Post by fr0gg on 2009-03-30
> **presence1960 said:**
> after the language choice choose try ubuntu without installing or with no changes to your computer

Still nothing..any other suggestions or should i just start the Hardy download? Also, when i'm installing Hardy, will i just be able to partition over the Intrepid partition or will i need to remove the current partition somehow, if so..how would i go about that?

---

### Post by jcm1107 on 2009-03-30
the fat partition I formated with the hard drive installation cd it is fat because I was trying that after ntfs didn't work with the other ubuntu installation. I was just trying all sorts of different things to get it to work. I just want to erase and repartition. all my important data is backed up. The only thing I have done on the new ubuntu instalation is mess around checking stuff out. Oh and I have all the cds burned that I will need. I am ready to try this. and I have my computer sitting next to this one so I can still get on here for help.

---

### Post by presence1960 on 2009-03-30
> **jcm1107 said:**
> Well I have had the Ubuntu runing for a little while now but I was just wanting to know the best way of installing it and xp at the same time with as few partitions as it takes like one for eace and the boot partition or whatever. I just got off of work. I work second shift

Since you have a licensed XP CD you can begin partitioning the disk once you have everything you need backed up to that external drive. Once the backup is done figure out how much space you want to give XP, and how much for Ubuntu. You may want to consider a partition for data or storage but not necessary. If you go with just Xp and Ubuntu (my bad- even with a data partition) you can pop in the gparted cd and boot from that. I would disconnect any external drives here to prevent accidental data loss on them! Make sure you read and familiarize yourself with the instructions from the gparted cd site first. Delete all partitions until you have one big unallocated drive. Apply that. Then make your 2 or three partitions. Do this by right clicking and choosing new. a dialogue box will come up. choose the size, file system and if you like put in a label which will name your partition. XP use NTFS for filesystem, Ubuntu I would go with ext3. If you make a storage or data partition, your choice between NTFS or ext3. I would make XP the first partition. when these are set up click apply. Once the partitioner is completed you can exit the gparted CD. Then install Windows XP. This should kill a huge chunk of time. I am going to bed now. If you have any problems check back there are tons of people who can help. I'll check back in the morning. See if you can get XP installed then we can go from there.

---

### Post by presence1960 on 2009-03-31
> **fr0gg said:**
> Still nothing..any other suggestions or should i just start the Hardy download? Also, when i'm installing Hardy, will i just be able to partition over the Intrepid partition or will i need to remove the current partition somehow, if so..how would i go about that?

you can install over the intrepid partition.

---

### Post by jcm1107 on 2009-03-31
> **presence1960 said:**
> Since you have a licensed XP CD you can begin partitioning the disk once you have everything you need backed up to that external drive. Once the backup is done figure out how much space you want to give XP, and how much for Ubuntu. You may want to consider a partition for data or storage but not necessary. If you go with just Xp and Ubuntu (my bad- even with a data partition) you can pop in the gparted cd and boot from that. I would disconnect any external drives here to prevent accidental data loss on them! Make sure you read and familiarize yourself with the instructions from the gparted cd site first. Delete all partitions until you have one big unallocated drive. Apply that. Then make your 2 or three partitions. Do this by right clicking and choosing new. a dialogue box will come up. choose the size, file system and if you like put in a label which will name your partition. XP use NTFS for filesystem, Ubuntu I would go with ext3. If you make a storage or data partition, your choice between NTFS or ext3. I would make XP the first partition. when these are set up click apply. Once the partitioner is completed you can exit the gparted CD. Then install Windows XP. This should kill a huge chunk of time. I am going to bed now. If you have any problems check back there are tons of people who can help. I'll check back in the morning. See if you can get XP installed then we can go from there.

I ran the gparted, I created three partitions,the first for xp the second for linux the third for storage. I installed xp to the first partition no problem. I tried to install Ubuntu 8.04 and got the same busy box as when installing Ubuntu 8.1. So I am just going to install the Ubuntu 7.1 and upgrade to 8.04 again. I went through the install process and I am stuck at the partitioning section of the ubuntu installation. It keeps saying no root file system is defined. I don't know what the root file system is and don't see anything that says it.

---

### Post by jcm1107 on 2009-03-31
I could not get Ubuntu 7.1 to install when using the three seperate partitions so I used gparted to create one big partition and 7.1 is now installed on that. Ubuntu kept trying to make 2 partitions when installing the first time and it kept saying no root file system. It worked fine after I used one big partition. Now how can I use this big partition with Ubuntu on it and create a partition for xp?, Without loosing Ubuntu.

---

### Post by presence1960 on 2009-03-31
sorry I was in work and tonight is one of my daughter's TaeKwon Do nights. just got back home. I wish I was here, all you needed to do when trying to install Ubuntu was select a mount point. "/" is the root partition mount point. When you selected the partition to install Ubuntu you chose ext 3 as file system. At the bottom should have been mount point option. If you don't choose a mount point that's why you get that message about no root file system. Like the rest of us you live and learn. You can still get this set up so don't worry about it

Ok you have Ubuntu installed but have written over your XP install by installing Ubuntu to the entire disk correct? If that is correct you need to boot the Live CD and run gparted from the CD. System > Administration > Partition Editor. You want to resize the Ubuntu partition to create a partition for XP. Right click the Ubuntu partition and choose resize. You can use your mouse to grab the end of the partition graphic and slide it across to resize or use the numeric sizer. Once you have the size set click apply. This may take some time depending on how much you want to give XP, so be patient. Again do not have your external drives connected to insure there is no data loss on them. Almost always the partitioner works well, but whenever working with partitions there is the possibility something can happen to make you lose data. Don't chance it. Have everything backed up and your back up drive(s) unplugged. After the resize is complete format the new partition to NTFS for XP. Then install XP to the NTFS partition. Unfortunately this will overwrite GRUB. But it is a simple procedure to restore GRUB from the Ubuntu Live CD after XP is installed. But we'll cross that bridge when we arrive there.

To double check I understand what you did: 1) you installed Ubuntu to the entire disk overwriting your XP install. 2) you now have the whole disk allocated to Ubuntu, but want to install XP. If this is correct follow the directions. Any questions just shoot them over to this thread or PM me.

I know we work different shifts so be patient. There are a lot of people who can help you here if need be.

---

### Post by jcm1107 on 2009-04-02
I have xp installed on the second partition now. Now I can not boot Ubuntu as you said xp overwrote it. How do I get Ubuntu back now? also my xp installation is giving me problems installing everything! I can't get on the internet on it because the eather net driver will not update. Alot of stuff I try to open says not a valid win 32 aplication. I am sure it is because it needs updated but I cant get it on the internet to update. I have the cd that came with the motherboard and it fails when I use it to update the eather net and I manually selected the file to use that I need to. Xp has always been dificult with new hardware, I was amased how well Ubuntu worked the only thing that did not work automatically was my graphics because I couldn't change my screen resolution any higher than 400x 600 but everything else WORKED no install needed! I was amased! thats what I thought I would need windows for was all my hardware like printers and things but it seems Ubuntu is more compatible with windows hardware than windows is!!

---

### Post by presence1960 on 2009-04-02
Do this to restore GRUB from the Live CD:
> 1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

in #7 I would use setup (hd0). Give that a whirl to get grub restored. Once you get it restored boot into Ubuntu and go to System > Administration > Hardware Drivers. See if there are restricted drivers for your vid card. If so enable them.

---

### Post by jcm1107 on 2009-04-02
Ok now I have Ubuntu Back but it boots automatically how do I get it to where I have a choice of which OS I want when I first boot my system? Now I can't boot to XP. I got my resolution changed, I had to go to nvidia and download an xconfig tool and figure out how to run that. I finally got it. That was the only hardware problem I had with Ubuntu so far! I am amased because xp when I was in it is not wanting to install alot of things I need. I had that problem when I installed my motherboard but when I first installed my motherboard it recognized my wireless adapter and connected to the internet and I was able to get updates. Now after totaly reformating my hard disk it isn't recognizing anything. I know it just needs all the windows updates but I can't get it on the internet. Well help me get the option to get into xp and then I will go from there. So far I am loving Ubuntu anyway I will probably use it 95%-99% of the time, it seems way better than windows.

---

### Post by presence1960 on 2009-04-02
> **jcm1107 said:**
> Ok now I have Ubuntu Back but it boots automatically how do I get it to where I have a choice of which OS I want when I first boot my system? Now I can't boot to XP. I got my resolution changed, I had to go to nvidia and download an xconfig tool and figure out how to run that. I finally got it. That was the only hardware problem I had with Ubuntu so far! I am amased because xp when I was in it is not wanting to install alot of things I need. I had that problem when I installed my motherboard but when I first installed my motherboard it recognized my wireless adapter and connected to the internet and I was able to get updates. Now after totaly reformating my hard disk it isn't recognizing anything. I know it just needs all the windows updates but I can't get it on the internet. Well help me get the option to get into xp and then I will go from there. So far I am loving Ubuntu anyway I will probably use it 95%-99% of the time, it seems way better than windows.

You can hit ESC when it says loading Grub 1.5 to get the menu. Also you can install startupmanager which will allow you to customize settings for "startup" hence the name. You want to set a delay of x seconds and choose a default OS in startupmanager. It is a GUI program. Install it from terminal ```
sudo apt-get install startupmanager
``` you can then open it from System > Administration > Startup Manager.

After you get that done see if you get a GRUB menu and try to boot to windows. If it won't boot to windows...relax. Sometimes it is just a case of editing the windows entry in menu.lst file. Let me know. I am off to my daughter's TaeKwon Do class will be back on here around 9:30pm Eastern Time.Good Luck!

---

### Post by jcm1107 on 2009-04-02
Ok I have startup manager installed windows xp is not on the list, just 7 different Ubuntu startups that says Ubuntu 8.04.2, kernal 2.6.24-23-generic
and the only thing different on them is the numbers after kernal and one says mem test. Also you said I would need to set a delay of x amount of seconds is this the time out? and how many seconds should I use I used 3 seconds for now in timeout. going to reboot and see but I think xp won't boot. I tried to hit esc before to get the option and it only showed the different ubuntu options.

---

### Post by jcm1107 on 2009-04-03
> **presence1960 said:**
> You can hit ESC when it says loading Grub 1.5 to get the menu. Also you can install start upmanager which will allow you to customize settings for "startup" hence the name. You want to set a delay of x seconds and choose a default OS in startupmanager. It is a GUI program. Install it from terminal ```
sudo apt-get install start upmanager
``` you can then open it from System > Administration > Startup Manager.

After you get that done see if you get a GRUB menu and try to boot to windows. If it won't boot to windows...relax. Sometimes it is just a case of editing the windows entry in menu.lst file. Let me know. I am off to my daughter's TaeKwon Do class will be back on here around 9:30pm Eastern Time.Good Luck!

I rebooted and it did not give an option to boot windows. Only the different Ubuntu options. So what do I have to do to get 
windows to boot? And thanks for getting me this far I really appreciate all your help!

---

### Post by jcm1107 on 2009-04-03
hey I got my computer to let me select xp in the grub menu. I had to edit the menu.lst I found the information on here. before tonight I didn't even know what a menu.lst was, or anything about grub other than it was the boot loader. But anyway I got it and thanks presence for your help!!!!!!

---

### Post by presence1960 on 2009-04-03
> **jcm1107 said:**
> hey I got my computer to let me select xp in the grub menu. I had to edit the menu.lst I found the information on here. before tonight I didn't even know what a menu.lst was, or anything about grub other than it was the boot loader. But anyway I got it and thanks presence for your help!!!!!!

Glad to be able to help you get it all up & running. I see on other threads you are sharing what you know about this area. Don't be intimidated because you are fairly new. Because of the problem you had and the work you did to solve the problem you now have valuable info that some may not possess. Pass it on! I'll be seeing you in here. Stay in touch with PM or my email.

P.S. Why don't you rename the title of this thread by adding [solved] to the title since the solved button no longer works.

---

### Post by jcm1107 on 2009-04-04
I found my problem that caused the busy box!! so I wanted to put it here!!! The problem was in my bios settings, I tried putting them like I thought they should be, and then I tried both failsafe and optimized settings none of that worked!! so here is what worked. I found out that ubuntu does not work with udma on the cdrom drive, mine was on auto. Well here is a list of what I had to change in my bios and then I booted the cd and just went down to install without changing anything and it went perfect.Here is the list:

1:in the bios main page hit enter on my dvdrom drive it then give me options for TYPE and DMA MODE

2: Change type from auto to CD/DVD

3: Change DMA from auto to swdma2 (I don't know what this is but it worked for me) I do know it can't be UDMA mode and mine didn't work on auto

4: I went to floppy and put not installed (I have herd that Ubuntu sometimes keeps trying to find a floppy and won't install, so I unplugged mine)

5:turned acpi off ( I keep reading to turn it off at the installation screen so I thought I would in the bios, I didn't turn it off at the install screen)

and thats it, I didn't have to do anything except hit install to get it to install after changing my bios!!!

---

