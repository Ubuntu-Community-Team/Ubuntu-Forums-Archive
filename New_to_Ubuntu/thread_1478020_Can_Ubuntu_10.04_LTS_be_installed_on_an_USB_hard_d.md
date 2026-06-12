---
title: "Can Ubuntu 10.04 LTS be installed on an USB hard drive"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by suomalainen on 2010-05-09
Ubunteros,

I have a Seagate Expansion USB hard drive to which I would like to install Ubuntu 10.04LTS. I really did try to find info on the net to do this but failed.

Would anyone here happen to have done such an install on an Seagate Expansion drive????

I'd really like to know if it can be done..

Thank you very much!!!

---

### Post by Penguin Guy on 2010-05-09
I've got it on my flash drive right here - although it's just a copy of the liveCD rather than a properly installed version. I used [COLOR="Green"]System -> Administration -> Startup Disk Creator[/COLOR].

---

### Post by suomalainen on 2010-05-09
Hi,

I would really live to do a full blown install of Ubuntu so I have something solid to work with!

Thanks

---

### Post by Dougie187 on 2010-05-09
I know you can install it, the only thing that would be an issue would be grub. I'm not quite sure how that would work.

---

### Post by philinux on 2010-05-09
I would imagine that the option would be to choose advanced at the last stage of install and specify grub be installed to the EXT drive. As long as your machine can boot from usb. You could also then run update grub on your main machine to pick up the EXT install.

Never done it so speculating.

---

### Post by Dougie187 on 2010-05-09
> **philinux said:**
> I would imagine that the option would be to choose advanced at the last stage of install and specify grub be installed to the EXT drive. As long as your machine can boot from usb. You could also then run update grub on your main machine to pick up the EXT install.

Never done it so speculating.

I seem to remember people discussing this previously, but haven't found the threads yet.

Don't you somehow need your local install of grub to detect the external drive to boot to it? Or can you use two separate grubs? I don't really understand how that would work.

I guess in my mind, this is essentially the same thing as installing ubuntu on two separate partitions on your computer, just one has to be removable. So in the situation you are describing, that would be like installing grub on both partitions. And I don't get how you would tell your computer which grub to boot to.

I think it wasn't a big issue if the External drive was ALWAYS plugged in when you boot to grub. But if it's not there when Grub wants to see it, then grub flips out. Either way, I'll do some searching.

EDIT:
This might help
[http://ubuntuforums.org/showthread.php?t=814048](http://ubuntuforums.org/showthread.php?t=814048)

[http://ubuntuforums.org/showthread.php?t=366562](http://ubuntuforums.org/showthread.php?t=366562)

[http://ubuntuforums.org/showthread.php?t=345693](http://ubuntuforums.org/showthread.php?t=345693)

---

### Post by cj.surrusco on 2010-05-09
I have install previous releases on a flash drive before. I didn't need to do anything different, I just installed grub in the bootsector of the flash drive, which it does by default, I think. And of course, your computer need to support booting by USB.

---

### Post by QLee on 2010-05-09
[QUOTE=Dougie187]
Don't you somehow need your local install of grub to detect the external drive to boot to it? Or can you use two separate grubs? I don't really understand how that would work.

I guess in my mind, this is essentially the same thing as installing ubuntu on two separate partitions on your computer, just one has to be removable. So in the situation you are describing, that would be like installing grub on both partitions. And I don't get how you would tell your computer which grub to boot to.
[/QUOTE]

It not essentially the same, it's similar. It's the MBR of whichever drive is identified as (hd,0) at boot time that determines where GRUB looks for the boot partition. philinux's suggestion (as stated) assumes a system capable of booting from USB drives and in the configuration detailed, one would use the system BIOS boot order to choose which drive was booted first. Since each separate drive and MBR would have a bootloader pointing to the boot partition on the same drive, it would work and I believe some of the regulars here operate that way.

It's probably still to be avoided installing GRUB2 (GRUB-PC) to a partition like we used to do with legacy. There is a new and different method to chainload.


There are a lot of different methods of multi-booting, one has to choose one they understand and can accomplish. I still go with the old method of a separate boot partition and that works too, but I don't recommend it unless the user understands and has a use for it. With GNU/Linux we have a great deal of choice.

---

### Post by dakra137 on 2010-05-09
YES, there is another alternative to USB Startup Disk Creator, if what you want to do is really use what you create, rather than use it to install onto another system:

What you don't want:

[INDENT]Normally, when INSTALLing onto a USB drive, 10.04 Lucid Lynx does not install the grub bootloader by default onto the target drive. Instead, it will update grub on the existing boot drive to include the linux instance on the USB drive.[/INDENT]

What you want:

[INDENT]When installing onto the USB drive, after specifying the root and swap partitions on the USB drive:
[INDENT]Click on ADVANCED and specify installion of the boot manager onto the USB drive.[/INDENT][/INDENT]

Hint:
When using ubuntu from the usb drive, for maximum portability, do not activate any special drivers for the video card on the machine you installed at. When I did, and then booted the USB stick at a server with a minimal video capability, a warning message popped up about running in some crippled mode.

---

### Post by crjackson on 2010-05-09
> **suomalainen said:**
> Ubunteros,

I have a Seagate Expansion USB hard drive to which I would like to install Ubuntu 10.04LTS. I really did try to find info on the net to do this but failed.

Would anyone here happen to have done such an install on an Seagate Expansion drive????

I'd really like to know if it can be done..

Thank you very much!!!

I did this and it was wack at first.  It trashed my Grub on my regular drive even after selecting the ADVANCED options and telling it to put grub on the USB drive.

The final solution for me was to simply 

1) disable all drives in the system except the optical drive.

2) Select the USB drive and install as normal.

3) Boot to the USB drive when done.

Then you can enable all your normal drives, and when booting to the USB always use the computers boot options menu to select the USB boot drive.

When booting to internal drives, always unplug the USB drive for the entire boot process.

There may be an easier way, but I couldn't find it when I was doing the same as you.

Good Luck.

---

### Post by suomalainen on 2010-05-10
Has anyone else tried something? It's strange but when I use the Ubuntu partitioning tool I can select and partition my hard drive which Windows XP resides on. However, when it comes to the USB external hard drive I can only see it and NOT partition it...

I really would like to hear more ides or successes of what others here have done...

Thank you!

---

### Post by cj.surrusco on 2010-05-10
Do you mean that that you are trying to edit the partitions on the usb drive or you are booted onto the usb drive and are trying to edit the internal drive?

---

### Post by suomalainen on 2010-05-11
What I mean is that I have a 750 GB external hard drive. This HDD has about 400 GB of data on it. Thus, it needs to be partitioned to preserve the data but also to allow for the installation of Ubuntu.

I'm also wondering that once I figure out how to partition this drive <IF THIS IS THE CORRECT METHOD> Can I simply do a simple install> Cause I wonder if I need the / and swap and home folders?

Any help anybody can offer me is greatly appreciated.

Thank you!!!!!

---

### Post by cj.surrusco on 2010-05-11
I would download a GParted boot cd and burn it to a disc. With that, you'll be able to resize the partition that is already on the external disc and add a new ext3 or ext4 partition for / and home. Or you could add two extra partitions, one for / and one for home.

---

### Post by suomalainen on 2010-05-12
Thanks cj.surrusco!

So as I understand the GParted boot CD is a tool I can use to partition the external hard drive?

If I'm understanding everything now correctly. I can reduce the size of the current partition that the data I have already occupies and then created a partition for the Ubuntu O/S, another for "/" and one for "home". BUT how large should the last two partitions be for "/" and "Home". Also, do I need partitions for GRUB or SWAP????

Finally, once the relevant partitions are created will Ubuntu install to them automatically or what???

Thanks for your continued support!

---

### Post by cj.surrusco on 2010-05-12
The size of the partitions is completely dependent on how much programs and other files (music, pictures, etc.) you want stored on the ubuntu partition. The way I partition my ubuntu is one large partition for Ubuntu install files and one smaller (around 2gb) for swap space. When you install ubuntu, mount the large file system that you made as "/". It will automatically add a home directory to that partition and you won't need to worry about a separate partition for home. Also, don't forget to mount the swap partition as swap during install.

---

### Post by cj.surrusco on 2010-05-12
refer to next post, sorry.

---

### Post by suomalainen on 2010-05-13
cj.surrusco,

What means "refer to next post, sorry. "

Did I miss something????

Also, How do you, "Also, don't forget to mount the swap partition as swap during install." This kind of stuff is new to me.

Thanks!

---

### Post by cj.surrusco on 2010-05-13
Ignore my last post that says, "refer to next post, sorry.". I accidently posted the same post twice.

And it will probably just be easier to start from the beggining of the installation process. Where are you in the process of installing ubuntu on the external drive?

---

### Post by suomalainen on 2010-05-14
cj.surrusco,

Right now I'm collecting information I need to know in as far as conducting the install of Ubuntu 10.04LTS onto my external USB drive.

Actually, I was under the impression at first that the install would be simple. For example, Load the live CD, partition the external hard drive accordingly and then install Ubuntu.

However, as I soon learned, I need to possess "Advanced experience" when messing with the advanced features within the install process. Then I also need to create "/", "swap" and home directories. So it seems the process is rather complex and involved.

So far, what I have gathered is that I can use gpart to create the Swap and "/" partitions. Then I can use the Live CD to install ubuntu to the "/" dircetory. Here Ubuntu will automatically create a "home" dircetory...

Does this sound like I'm on the right track?

Thanks once again!

---

### Post by cj.surrusco on 2010-05-14
suomalainen,

No problem for the help.

And yes, you are on exactly the right track as far as going about the installation. Start with the partitioning and get back to me when finished. I can write up a few steps for you:

1. Remove all hard drives except the external one (to avoid any confusion). 

2. Boot from GParted CD (You can also use a Ubuntu live CD because I'm pretty sure it has GParted already installed on it).

3. Shrink Existing partition to an appropriate size (I would leave about 30-40GB for the Ubuntu install).

4. Create a new partition for Ubuntu (Fill all of the now free space **except** for 2GB). Choose to format the new partition as ext3.

5. Use the remaining 2GB to create another partition. Choose to format that partition as "linux swap" or "swap"... I'm not sure exactly how it is worded.

Once you are there you should be ready to install Ubuntu on the drive.

---

### Post by suomalainen on 2010-05-15
cj.surrusco,

I attempted today to create the partitions. Attached is a screen shot from Gparted as to what I was able to accomplish. **Please note that I believe I set the Linux-swap as a primary partition.**

After I made the partitions I attempted to install Ubuntu and had to use the advanced features during install. It was all a bit tricky for me to do. I wasn't sure if everything was moving ahead accordingly or not???? Or what errors I may have made.

After install I rebooted my laptop with the LiveCD still in the tray. Ubuntu booted up. Even the broadband modem settings were retained and immediately working.

I re-booted again w/o the CD and this time received the following message straight away

**No bootable devices--Strike F1 to retry boot, F2 for setup utility.**

Please note that during all of this the Laptop HDD had been disconnected.

When the Windows HDD was installed back I could only see the G:/Joh partition on the external drive. When the Ubuntu Live CD was used I could see both the Joh partition and the Ubuntu 10.04 LTS partition.

I'm hoping that that Grub was installed to the wrong place and this is why I got the error message. If this indeed is the case, I would need precise instructions as to what to do... Really sorry but I need the step by step help...

Anyway, I look forward to your thoughts.

Thanks again for your support!

---

### Post by BT1 on 2010-05-15
Are you *really* having trouble with this? I install Linux on flash drives on a regular basis and have no issue but I haven't tried it with USB drives. What I do is, I use a live CD first and go to gpart, unmount the drive, then create a new partition table. Then I make 2 partitions usually, the root partition and a small home partition. I then restart with the alternative-text install CD and install that way because I'm more comfortable with it. I select the drive as the place to put the grub. Then after the install, it works fine but I wouldn't recommend it if you want speedy responses from your system, the live CD usually works better in that regard.

Now, taking two flash drives and making an Ubuntu RAID 0 install from them is where stuff gets complicated. You have to have three flash drives, and the alternate install CD to do that.

Try using the alternative-text CD. It's not a whole lot different when it comes to feeling your way around.

---

### Post by cj.surrusco on 2010-05-15
suomalainen,

Okay, well you need to make sure that your computer supports booting from a USB drive. Make sure the USB drive is plugged in and then go to your bios and see if "USB Drive" or something similar is in your boot order. Then put it to the top of the order. 

If the USB drive is set to boot first and you still get that error, I will explain to you how to install the bootloader to the bootsector of the drive.

---

### Post by Paddy Landau on 2010-05-16
> **suomalainen said:**
> Please note that I believe I set the Linux-swap as a primary partition.
Linux doesn't care whether your partitions are primary or extended -- even for your boot partition.

> **cj.surrusco said:**
> Choose to format the new partition as ext3.
Why not ext4? That's the new standard, isn't it?

---

### Post by suomalainen on 2010-05-16
cj.surrusco,

Thanks for coming to the rescue! My laptop can boot from USB and is at the top of the BIOS list. I even put the live CD to a USB stick and that always boots first when it is placed into a USB port.

I've noticed that **most of the time** that when I boot XP first and then do a Start--> Restart then Ubuntu will boot up provided the external USB it resides on is connected to the USB port. But this doesn't necessarily happen all the time.

If you can explain how to install the bootloader to the bootsector of the drive that would be great. Perhaps we can even confirm if it is there at all??? If it is, maybe the problem then is something else?

Paddy Landau, pointed out below that perhaps formatting should have been done in ext 4. Although I did it as ext3 does this make problems?

> Why not ext4? That's the new standard, isn't it? 

Thanks again for your trusted advice and insight.

Regards,

Suomalainen

---

### Post by ssj6akshat on 2010-05-16
try usbuntu live creator or unetbootin

---

### Post by bikodog on 2010-05-16
> **cj.surrusco said:**
> suomalainen,

No problem for the help.

And yes, you are on exactly the right track as far as going about the installation. Start with the partitioning and get back to me when finished. I can write up a few steps for you:

1. Remove all hard drives except the external one (to avoid any confusion). 

2. Boot from GParted CD (You can also use a Ubuntu live CD because I'm pretty sure it has GParted already installed on it).

3. Shrink Existing partition to an appropriate size (I would leave about 30-40GB for the Ubuntu install).

4. Create a new partition for Ubuntu (Fill all of the now free space **except** for 2GB). Choose to format the new partition as ext3.

5. Use the remaining 2GB to create another partition. Choose to format that partition as "linux swap" or "swap"... I'm not sure exactly how it is worded.

Once you are there you should be ready to install Ubuntu on the drive.

cj.surrusco's method is the same method that I have used on seagate usb drives. The key is removing your other drives before install so that no changes are made to MBR. Install from liveCD; partition your usb drive as you would a conventional installation. When complete, reinstall drives. As long as you can boot from usb, it works flawlessly.

---

### Post by cj.surrusco on 2010-05-16
As far as using ext3 instead of ext4, that is just my preference from experience with both. I have used ext4 and it has become corrupt, however I have has no problems whatsoever with ext3. The few advantages of ext4 are that it can hold *very* large files and file systems. You wouldn't need that type of support on your USB drive.

As far as installing grub to the bootsector of the drive,

**1.** Remove all other drives

**2.** Boot from the live CD

**3.** Open up a Terminal

**4.** Start Grub
```
sudo grub
```

**5.** Find the boot info
```
find /boot/grub/stage1
```
(That should give you a result, something like (hd0,1)

**6.** Use the last result as the root for installation. 
```
root (hd0,1)
```
***Note yours may be different than (hd0,1). Use whatever your result was in step 5

**7.** Finally, install to the bootsector.
```
setup (hd0)
```
***Use the same result you used in step 5, but without the comma and second number

Hope this helps

---

### Post by cj.surrusco on 2010-05-16
I probably should just put together a tutorial at this point, is there already one out there?

---

### Post by scouser73 on 2010-05-16
I think that you would need to look in the BIOS settings and make sure that the external drive you have Ubuntu on is the primary drive & you'd need to disconnect the internal drive for it to work.

This post tells you about installing a previous version of Ubuntu onto an external hard drive; [http://ubuntuforums.org/showpost.php?p=436420&postcount=1](http://ubuntuforums.org/showpost.php?p=436420&postcount=1)

---

### Post by debianlinux on 2010-05-16
simple way to do is to take out your harddrive inside you desktop/notebook... go to bios and set dvd drive to be the 1st to boot then 2nd usb drive... if you have internet connection, plug in the lan cable as well..  now you may do the installation process.. once finished, boot to usb drive several times, run nesessary updates, check all driver correctly installed.. satisfied? go to bios setup again, change the boot order again but make sure "boot to harddrive" is set after usb drive.. done

---

### Post by suomalainen on 2010-05-16
cj.surrusco,

If you develop a tutorial it would be good to note that with the Live CD you need to install

sudo apt-get install grub

And only afterwards will grub run.

Unfortunately, I'm stuck on step #5:

> 5. Find the boot info
Code:

find /boot/grub/stage1


I get the following error:

[B]grub> find /boot/grub/stage1


Error 15: File not found[/B]

I've tried to look up online what to do but haven't been too successful.

Any ideas?

---

### Post by cj.surrusco on 2010-05-16
> **suomalainen said:**
> cj.surrusco,


I get the following error:

[B]grub> find /boot/grub/stage1


Error 15: File not found[/B]



I think the reason may be that Grub *2* is installed on the external USB. Grub 2 is the new standard.

I would try an alternative approach to this now. You are able to boot onto the external drive with the live CD in, correct? I mean by booting from the CD and choosing "boot from hard disk" from the CD menu.

If you are able to do that, try installing grub2 from that point.

---

### Post by suomalainen on 2010-05-16
This web site has some good info relating to my error 15

See:

[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

However, everything is spoken in terms of sda while I'm seeing sdb

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       84452   678360658+   7  HPFS/NTFS
/dev/sdb2           84453       90918    51938145   83  Linux
/dev/sdb3           90919       91201     2273197+  82  Linux swap / Solaris


I wonder if in my case I'm hd0,1 or hd1,1???? KINDA CONFUSED????

Regarding:

> You are able to boot onto the external drive with the live CD in, correct? I mean by booting from the CD and choosing "boot from hard disk" from the CD menu.

The CD menu you refer to isn't offered. I can only trial Ubuntu or install. Regardless of whether i'm in XP or 10.04 if I do a re-boot w/o a cd my external usb with Ubuntu will boot up automatically.

HOw exactly is grub 2 installed and to where????

Does any of this help????

---

### Post by cj.surrusco on 2010-05-16
You are in a difficult situation, because you have no root to install grub from

You may be best trying to reinstall ubuntu using the same procedure but this time insuring that grub is installed to the mbr. 

At the end of the installation there should be an "advanced options". Enter that and ensure that grub will be installed to the mbr or root of the drive instead of the ubuntu partition.

---

### Post by suomalainen on 2010-05-16
cj.surrusco

Where you able to look at:

[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

What would the numbering look for me??? Is it hd0,1 or hd1,1????

It is also stated that:

> You can also reinstall Grub in your GNU/Linux partition, only if this GNU/Linux partition is “primary” and you have another boot loader installed at the MBR(in case of more than one GNU/Linux operating systems) through which you can boot this primary partition. To do that, give this command at the terminal:

What do you think?

---

### Post by cj.surrusco on 2010-05-16
I do not know enough about grub2 to help you because I use grub legacy. But to answer your question, it would be (hd1,1) since you are on sdb.

---

### Post by bennachie on 2010-05-16
This is one of those jobs that used to be easy, and seems to have become much harder since Grub2 arrived. You might like to work your way carefully through an installation of, say, Fedora 13RC on an external USB drive to see just how the process of placing Grub1 on the drive should operate.

Remember to precede the installation by formatting the external drive with an MBR (disk utility will do the job nicely).

---

### Post by cuberts on 2010-05-16
> **suomalainen said:**
> Ubunteros,

I have a Seagate Expansion USB hard drive to which I would like to install Ubuntu 10.04LTS. I really did try to find info on the net to do this but failed.

Would anyone here happen to have done such an install on an Seagate Expansion drive????

I'd really like to know if it can be done..

Thank you very much!!!
Yes, it is very easy to do.
I recommend that you go to 
pendrivelinux.com

and download the program at the very bottom. It is a program which automatically compiles the ISo image for you

---

### Post by Paddy Landau on 2010-05-17
> **suomalainen said:**
> ... perhaps formatting should have been done in ext 4. Although I did it as ext3 does this make problems?
No, it won't create problems. ext4, apparently, is more efficient than ext3, but I'm not entirely sure of that. You can [convert ext3 into ext4]("https://help.ubuntu.com/community/ConvertFilesystemToExt4"), but you get the benefits only for new files, not for files already on the partition. If you haven't yet used the partition, I'd suggest that you simply reformat it to ext4.

> **cj.surrusco said:**
> I have used ext4 and it has become corrupt...
When Canonical first released ext4 with Ubuntu, there were some unfortunate bugs. I understand that they have all been fixed.

> **cj.surrusco said:**
> I probably should just put together a tutorial at this point
Yes, please! If you post the URL here, then we'll know where to find it.

> **debianlinux said:**
> simple way to do is to take out your harddrive inside you desktop/notebook...
That can be a real problem. If I have a laptop under guarantee, then opening it up will invalidate it. Further, I'm not knowledgeable about hardware, so doing that is likely to destroy my laptop!

---

### Post by Abhinav K Sahdev on 2010-05-17
I tried installing Ubuntu 10.04 LTS on a usb 2.0 8gb flash drive.
i did it with livecd using guided partitioning using entire usb partition.(full install not live one)(just chose sdb from the drop down menu in the setup). everything went smoothly. the only problem was that it runs too slow for me from a usb drive. the usb i had formatted in ext3.

---

### Post by Kizerkaze on 2010-05-17
I have been searching for a solution also and I've stumbled across this forum which is leading closer to the answer, but apparently not close enough, it is possible to install the Ubuntu 10.04 LTS Operating System to an external storage device such as a USB or HDD.

There is another forum post related to this that has most of it right but there are a few hic ups that come along with it, but, there are many different methods of doing this. If your using a virtual machine that emulates Ubuntu as a live CD and then installing it onto the external device whether it may be a USB or HDD, or, just using a live CD (Download and burned to a disc or just delivered to your door) and installing it that way.

One of the most important points you must remember is that when you are going to install a OS onto a external device is to delete ALL partitions, the easy way of doing this is to go into Ubuntu through the live CD (use any method, just as long as it can boot from it), and go to System -> Administration -> Disk Utility and unmount then format to "Don't Partition". This way Ubuntu will install the recommended format for you.

Now if you cannot remove your HDD from your laptop suomalainen, don't worry about it, it doesn't change anything, all it changes is the "dev/sda, sdb, sdc, etc." depending how many drives you are using during the installation, make sure you select the one with the storage name next to it.

And finally, when installing OS's to a external storage device make sure that it is capable of doing so, I have experimented with many storage units and only some of them are able to boot:- 1. The brand is the quality of the device in which it can boot properly
[CENTER]              2. Check to see if it has a reset module built in, if it does then it is not recommended.

[LEFT]I hope this helps to all and if you need any answers to your questions please reply to this forum post and not to my email.
[/LEFT]
[/CENTER]

---

### Post by Paddy Landau on 2010-05-18
> **Abhinav K Sahdev said:**
> usb i had formatted in ext3.
From what I've read about USB flash drives, ext3 is an inefficient format, because of the way flash drives store data internally. I've read that FAT32 is about the best format you can get for it.

I may be wrong on this, as I'm not an expert, so perhaps someone can clarify.

> **Kizerkaze said:**
> Now if you cannot remove your HDD from your laptop suomalainen, don't worry about it, it doesn't change anything, all it changes is the "dev/sda, sdb, sdc, etc." depending how many drives you are using during the installation, make sure you select the one with the storage name next to it.
Thanks for posting, Kizerkaze. Doesn't it change the grub on your laptop's hard drive, so that when you remove the external USB drive, you can no longer boot from it?

---

### Post by cronmiller on 2010-05-18
I took a formated drive, removed my Win-XP drive and installed Ubuntu on my laptop.  I found a "plop bootmanager", burned a CD because my laptop BIOS does not support booting from USB.  I booted from the "plop" with the Ubuntu drive in an Apricorn USB adapter.

I now have a Grub2 problem.  The laptop must be booted with the plop CD to avoid a Grub Recovery error, can't find drive.  I am busy trying to resolve the Grub2 problem so the laptop boots Win-xp
when the plop CD is not present.

It appears that Grub got on my Win-xp drive while I was booted up via plop.  I fear the total loss of the ability to boot the Win-xp if I mess with some of the GRUB2 commands in Ubunto.

---

### Post by Greblok on 2010-05-19
I had a lot of trouble with Grub2 when I tried to compile my own USB isntall.
Ended up with using the following tutorial:
[http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/](http://mintarticles.com/read/operating-systems-articles/how-to-install-portable-linux-ubuntu-on-a-bootable-usb-flash-drive-from-sun-virtualbox,13641/)

Easy and working install.
Maybe it could be of help to someone. :)

---

### Post by Kizerkaze on 2010-05-19
Your welcome Paddy Landau, to answer your question, yes and no depending on what method you use. If you tell me what you want to do I'll reveal the recommended method to the user if necessary.

Cronmiller, you may have done the wrong thing, no offense, and if you are capable to remove the HDD unit from your laptop, then why not remove it entirely while installing the OS on the USB drive? Also how did the grub2 protocol write itself if you have removed the drive? If your BIOS cannot support booting from another source then why would you proceed? Please use caution and study on what your about to do, this goes for all of you users who want to do things like this. Just a word of advisement.

Congratulations Greblok on your success, I hope you check the comments down the bottom before you think twice with the tutorial next time.

A final word, the grub2 problem is usually a (hd0,0) => (hd0,1) => (hd1,1) issue, what happens is when you install a 3rd party OS it registers any other OS and bootable device and orders them accordingly, if you only have a USB unit and a live CD in a system then the OS will register the USB as sda instead or sdb, sdc and so on.

Again I hope this helps.

---

### Post by Paddy Landau on 2010-05-20
> **Kizerkaze said:**
> Your welcome Paddy Landau, to answer your question, yes and no depending on what method you use. If you tell me what you want to do I'll reveal the recommended method to the user if necessary.
Thank you.

What I was thinking when I saw this thread is something that I've been wanting to do for a while.

I *think* that this is what the OP wanted, and it's what I want...

To create a bootable partition on the external USB drive, so that I can take the USB drive somewhere else and boot off a different computer (something like a Live CD, but as a proper install).

And to do this *without* changing the original hard drive in the laptop, so that when the USB is not attached, the laptop will boot normally off its own hard drive.

I hope that I've made sense.

---

### Post by suomalainen on 2010-05-20
Paddy Landau,

You understood correctly what I wanted to achieve. At the moment I can boot Ubuntu 10.04. the only deal is that I need to go into BIOS upon boot up and disable the internal HDD and then my usb will boot up.

what I wish to happen is that I can simply plug in my usb before power-up and have the boot process to Ubuntu 10.04 take over automatically.

Earlier in this post there were some recommendations as to how this could be done but I only received error 15 messages....

And now I don't even know if it was wise to partition my drive into 3 separate partitions as instructed. Simply because in the end nothing positive was achieved....

but who knows, maybe someone with great expertise can lead the way????

---

### Post by Kizerkaze on 2010-06-02
Then here is a link that you might like:

[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

Please take note that I did not create this tutorial, this tutorial is owned by the maker who created it and is not affiliated with me in any way.

---

### Post by suomalainen on 2010-06-02
Oh no...

Peppermint didn't install
Lubuntu didn't install
Mini version of Ubuntu didn't install

In each case the software attempts to install but then with hours gone by just hangs....

What do you think? Take this old pc to the field and..........

---

### Post by alphaamanitin on 2011-10-13
Well this is super old, but what the hell.  I boot Ubuntu 9.04 through 10.04 LTS off of a Segate 320 gb USB HD.  What I did is use the entire USB drive during the install of Ubuntu and installed grub to the USB drive.  After the install I plug it in when I want to run linux on my laptop.  I have a Gateway, so I set the BIOS up to boot USB hard drives first, then internal harddrives then cd-roms.  Course, by bios is buggy and does not always recognize the external HD so I always hit F12 for my gateway laptop to give me the boot options.  If the external HD isn't there I tell reboot, and keep going until the Seagate HD shows up in the boot menu and I then boot the linux install.  Absolutely no problems, ever.

AlphaA

---

### Post by suomalainen on 2011-10-14
Your correct alphaamanitin and it works just as you say.

---

