---
title: "GRUB 1.97~beta4  can not boot"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by shadowlands on 2010-01-08
I am dual booting with windows xp.  I am usinga an acer computer.  I was running Karmic Kola.  I upgraded last night and now I can not get in to ubuntu.  I have no trouble getting in to windows.

The on screen message is: [ minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]

how do I correct this so i can boot into ubuntu (karmic?

I have tried searching the net and tried all the solutions I saw on the board, that do not require a live CD, and I can not figure out how to correct teh problem.

Any help would be greatly apperciated.( going to have a snack while I waite:popcorn:)

---

### Post by drs305 on 2010-01-08
If you can get to a grub prompt, which it seems like you can, have you reviewed instructions for trying to boot from the command line?
[https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

If you can type "ls" at the grub prompt you should see your partitions. If you type "ls /" and can see your root folders and "vmlinuz" and "intitrd" you should be able to get into your system without too much trouble.  A bit more work if the second command doesn't work, but still 'doable'.

---

### Post by shadowlands on 2010-01-08
the system will not recognize "sudo"

---

### Post by drs305 on 2010-01-08
You won't need "sudo". The grub prompt I mentioned is the prompt you end up at when the normal boot fails. If we are talking about the same thing, when the boot fails you should be left with either a "grub>" or "rescue?>" prompt.

---

### Post by shadowlands on 2010-01-08
Thanks I am know on the same page with you. I went looking online to find threads about the problem and they were all using "sudo" and other commands used in the regular terminal.  

Thanks for clearing it up.  

I am looking over it it now. 

when I type "ls" i see hard drives but the "ls/" command is not recognized by the computer.  > **drs305 said:**
> You won't need "sudo". The grub prompt I mentioned is the prompt you end up at when the normal boot fails. If we are talking about the same thing, when the boot fails you should be left with either a "grub>" or "rescue?>" prompt.

---

### Post by EssexEagle on 2010-01-08
> **shadowlands said:**
> when I type "ls" i see hard drives but the "ls/" command is not recognized by the computer.

Put a space between ls and the forward slash.

---

### Post by shadowlands on 2010-01-08
> **EssexEagle said:**
> Put a space between ls and the forward slash.

Thanks I did that, "ls /", and the command took.

Now what? :KS:popcorn:

---

### Post by drs305 on 2010-01-08
> **shadowlands said:**
> Thanks I did that, "ls /", and the command took.

Now what? :KS:popcorn:

Refer to the link in post #2. It explains how to boot via the grub command line. If you are seeing files, you should be able to use that guide to enter the remainder of the commands to get your system to boot.

---

### Post by shadowlands on 2010-01-08
Thanks

---

### Post by shadowlands on 2010-01-08
When I type in ls i get : (loop0) (hd0)(hd0,5)(hd0,1)

when I type in "c"

I get the following message:error unknown command 'c'
and i have no clue how to decode or utilize the rest of the information on the page.

---

### Post by drs305 on 2010-01-08
> **shadowlands said:**
> When I type in ls i get : (loop0) (hd0)(hd0,5)(hd0,1)

when I type in "c"

I get the following message:error unknown command 'c'
and i have no clue how to decode or utilize the rest of the information on the page.

You are already at the command line so you don't need to type the "c". I'll take a look at the doc to make sure it's clear. You just type in the commands in bold. In most cases, as you type them nothing will happen. The information is being recorded by the system. After you enter all the commands, you press CTRL-X or type boot (in some cases) and the system will act on all the information you have entered previously.

Also since you mentioned "loop" you are probably using wubi. This is important for 'helpers' to know when trying to troubleshoot things. Note that there is a special (longer) command for wubi installs when you type the "linux" line. It's mentioned in the doc.

If none of this is making sense the best thing is to get onto the Ubuntu IRC channels so we can help you "live". I'll pull up that link in a moment.

Added: Here is a HOWTO I wrote about XChat, one of the popular IRC clients. If you can use it in your situation, of course:
[https://help.ubuntu.com/community/XChatHowto]("https://help.ubuntu.com/community/XChatHowto")

Ubuntu IRC in general:
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")

---

### Post by BinaryFeast on 2010-01-08
I had the same problem, but managed to fix it. There are basically two ways you can deal with this: You can boot as it is now, if you type in the commands needed to boot manually. This is what I used:

```

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro

initrd /boot/initrd.img-2.6.31-14-generic

boot

```Change "sda3" to the name of the drive you installed Ubuntu on (possibly sda1 if you installed it on the C drive in Windows) and 2.6.31-14 to your preferred kernel verion (although this one will likely work, if not change "-14" to "-15" or something similar). You will then need to do this every time onwards.

Then there is the proper fix for this problem: There is a patch to the file wubildr (or maybe it was wubildr.mbr) that I found on one of the bug report discussion pages. If you can find that patch (I'm looking for it right now), download it and replace the file of the same name on the (most likely) C drive in Windows. You can do all this from within Windows.

EDIT: OK, I'm not sure if I can find it again. But you could keep googling for it (I don't really have time right now). Though I found another fix: Read [https://bugs.launchpad.net/wubi/+bug/477169/comments/70](https://bugs.launchpad.net/wubi/+bug/477169/comments/70) and [https://bugs.launchpad.net/ubuntu/+bug/477169/comments/84](https://bugs.launchpad.net/ubuntu/+bug/477169/comments/84), maybe also some of the other comments there. Take a look at that and see if it can help you.

---

### Post by drs305 on 2010-01-08
BinaryFeast,

Thanks for the information on the bug fix. There have been a lot of problems with wubi in the past few days, probably because of the kernel update. Posting the bug link if you can find it is going to help a lot of frustrated wubi users.  :-)

---

### Post by shadowlands on 2010-01-08
U guys are so great!!  :popcorn:

---

### Post by drs305 on 2010-01-08
> **shadowlands said:**
> U guys are so great!!  :popcorn:

I'll take that as a "it worked". I am in the process of reformatting some of the CLI help instructions on the community doc to make it easier to follow.

---

### Post by BinaryFeast on 2010-01-08
I found it! [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

This is what I used to fix the problem. Have not had any problems since.

---

### Post by MM7 on 2010-01-08
Hi.  First post for me.

Basically I started using Ubuntu 9.10 2 weeks ago.  I've never used Linux before and have found it a very pleasing experience.

Tonight I was prompted to do an update (50 something Mb).  I think it was a security update.  I rebooted as instructed and now I can't get into Ubuntu. I get the same as the originator of this thread.

I have tried the commands previously posted and the post #12 code made me get lots of text coming up on my screen and then stopped.

To be honest, I have never ever done any code stuff and I am a complete novice at stuff like this.  Is this the end of Ubuntu for me as I haven't a clue what to do?  I don't understand drive numbers or any code what so ever.

How do I continue my enjoyable experience with Ubuntu?

Any help appreciated.  Thanks.

ps.  When I say I don't understand codes, I really do mean that.  I just need something to type in to get it going again, hopefully.

EDIT:  I have checked out the links posted but they are way too advanced for me and far too much info for me to take in.  BTW, I don't like this auto destruct feature with the updates.

---

### Post by drs305 on 2010-01-08
> **MM7 said:**
> 

ps.  When I say I don't understand codes, I really do mean that.  I just need something to type in to get it going again, hopefully.

EDIT:  BTW, I don't like this auto destruct feature with the updates.

I just got called to work so I don't have the time to make a detailed post, but for others willing to help: If you enter the commands and then see a lot of text, and then the boot stops it is usually because the value for "root=" is incorrect. The system can boot for quite a while before this issue becomes a show-stopper. There are two places where the user has to tell Grub where root is, and they both must point to the correct place.

Did the "ls" command provide results? How about "ls / "? If you were running the commands correctly, you may have to go back and run the "set prefix=" command first. The format is on the community doc page. 

Hopefully someone will come along to assist you.

Believe me, none of us likes it when updates don't work!!!

---

### Post by MM7 on 2010-01-08
Thanks for your response DRS35.

I can now proudly say I am posting this from Ubuntu.  WooHoo!!

I went back and re-read the link posted from BinaryFeast, backed up the wubildr file, pasted the new one and rebooted.  All working again.

BTW.  Where is a good starting point to learn about this coding malarkey?  I need somewhere to learn the basics.  I can see myself getting into this. :D

Thanks again.

---

### Post by BinaryFeast on 2010-01-08
> **MM7 said:**
> Hi.  First post for me.

Basically I started using Ubuntu 9.10 2 weeks ago.  I've never used Linux before and have found it a very pleasing experience.

Tonight I was prompted to do an update (50 something Mb).  I think it was a security update.  I rebooted as instructed and now I can't get into Ubuntu. I get the same as the originator of this thread.

I have tried the commands previously posted and the post #12 code made me get lots of text coming up on my screen and then stopped.

To be honest, I have never ever done any code stuff and I am a complete novice at stuff like this.  Is this the end of Ubuntu for me as I haven't a clue what to do?  I don't understand drive numbers or any code what so ever.

How do I continue my enjoyable experience with Ubuntu?

Any help appreciated.  Thanks.

ps.  When I say I don't understand codes, I really do mean that.  I just need something to type in to get it going again, hopefully.

EDIT:  I have checked out the links posted but they are way too advanced for me and far too much info for me to take in.  BTW, I don't like this auto destruct feature with the updates.

Hi. Here are some more detailed instructions. If you want to try the patch (which may be the easiest, assuming it works on your particular installation, otherwise it is easily reversible), do this:

1) Boot into Windows.

2) Download the following: [http://launchpadlibrarian.net/36920146/wubildr]("http://launchpadlibrarian.net/36920146/wubildr")

3) Find the drive/partition in Windows that you installed Ubuntu on. The default is the C:/ partition. ("Start"->"Computer"/"My computer"->Click on "C:").

4) Look for a file named "wubildr". Copy it elsewhere as backup (just in case).

5) Place the new "wubildr"-file you downloaded from the link above to where the old file was.

6) Reboot and Choose "Ubuntu" as usual. If you normally get to a menu prompting you to choose kernel and boot commands, then press "e" at the highlighted choice. Now you can check to see if the line contains the command "insmod ntfs", if so remove it and continue booting by pressing the key implied on the screen. If you do not get this menu, press "esc" while booting,

If this worked, as it did for me, then you shouldn't have to worry anymore. If the patch didn't do anything for you, then you can replace it with the old file again.

-----

And about the code in post #12: This is if you need to boot into Ubuntu as it is now. If the patch works for you, then you don't need to worry about it. But if you really just need to boot it anyway, I can try to help you if you give some more information on your hardware and the way you installed Ubuntu. It will likely not work if you typed in exactly as I did. That is because I don't have Ubuntu installed on the C:-drive (which in my case would be sda1), but rather the H:-drive, which is the 3:rd partition (sda3) on the single HDD of my laptop. Have you tried typing in everything I posted, but replacing "sda3" with "sda1"?

Partitions on HDD:s are named differently in Linux and Windows. We can help you figure out the name of the partition you have Ubuntu installed on if you tell us where in Windows you can find the folder named "ubuntu", how many HDDs you have, and how many partitions (also called "volumes") they have. If you have an older computer you may also need to replace the "sda" with "hda" in the commands. And if have it installed on a second or third physical drive, you may need to replace "sda" with "sdb" or "sdc" and so on.
-----

EDIT: Too late :D . Glad you fixed it!

---

### Post by BinaryFeast on 2010-01-08
> **MM7 said:**
> Thanks for your response DRS35.

I can now proudly say I am posting this from Ubuntu.  WooHoo!!

I went back and re-read the link posted from BinaryFeast, backed up the wubildr file, pasted the new one and rebooted.  All working again.

BTW.  Where is a good starting point to learn about this coding malarkey?  I need somewhere to learn the basics.  I can see myself getting into this. :D

Thanks again.

Well, at least I can try to explain what the lines here do. Basically it tells grub2 (the so called boot loader, that which loads the OS) where to find the files needed to boot Linux.

```

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro

```

This tells grub where on the root-partition the linux kernel (in this case "vmlinuz-2.6.31-14-generic") is located.  Then it tells it on which drive that root partition is, and the "loop="-part is meant to mount the virtual HDD (root.disk) that is placed in the folder "/ubuntu/disks" on that same HDD (this is a wubi-specific thing).

```

initrd /boot/initrd.img-2.6.31-14-generic

boot

```

This one tells it where on drive the file "initrd.img-2.6.31-14-generic" is located. It is a special file needed during the boot process, related to ram somehow. Not too sure about the specifics. Then you can guess what "boot" does":)!

---

### Post by shadowlands on 2010-01-08
naw, i am still having trouble but i am thankful that u guys would take the time to aid me.> **drs305 said:**
> I'll take that as a "it worked". I am in the process of reformatting some of the CLI help instructions on the community doc to make it easier to follow.

---

### Post by shadowlands on 2010-01-08
Thank you!!!  let me post my error so that others will not make the same goof.   these are three separate lines
```

Step 1.
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro



step 2.
initrd /boot/initrd.img-2.6.31-14-generic


step 3.
boot

> **BinaryFeast said:**
> I had the same problem, but managed to fix it. There are basically two ways you can deal with this: You can boot as it is now, if you type in the commands needed to boot manually. This is what I used:

[code]
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro

initrd /boot/initrd.img-2.6.31-14-generic

boot

```Change "sda3" to the name of the drive you installed Ubuntu on (possibly sda1 if you installed it on the C drive in Windows) and 2.6.31-14 to your preferred kernel verion (although this one will likely work, if not change "-14" to "-15" or something similar). You will then need to do this every time onwards.

Then there is the proper fix for this problem: There is a patch to the file wubildr (or maybe it was wubildr.mbr) that I found on one of the bug report discussion pages. If you can find that patch (I'm looking for it right now), download it and replace the file of the same name on the (most likely) C drive in Windows. You can do all this from within Windows.

EDIT: OK, I'm not sure if I can find it again. But you could keep googling for it (I don't really have time right now). Though I found another fix: Read [https://bugs.launchpad.net/wubi/+bug/477169/comments/70](https://bugs.launchpad.net/wubi/+bug/477169/comments/70) and [https://bugs.launchpad.net/ubuntu/+bug/477169/comments/84](https://bugs.launchpad.net/ubuntu/+bug/477169/comments/84), maybe also some of the other comments there. Take a look at that and see if it can help you.

---

### Post by MM7 on 2010-01-09
Just a quick note to say thank you to BinaryFeast for that excellent explanation of what the codes posted mean.  Nice one. 8-)

---

### Post by charlier653 on 2010-01-09
[CODEinitrd /boot/initrd.img-2.6.31-14-generic
[/CODE]

breakdown of the initrd part of the command, as i understand it:

init=initialize
r=ram
d=drive

this is needed prior to being able to access the disk because at this point in the boot process, the drive has no mount point. this gives a place for temporarily mounting the drive to enable access to the OS files.

the rest of the comand is just telling the bootloader where to find the file

---

### Post by MM7 on 2010-01-10
Just an update from me.

I'm now getting the message, "The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

I get this when I try to log into Ubuntu 9.10.  I can't get past the login screen.

Good experience of new operating system turned into really bad experience. :sad:

Any help appreciated.

---

### Post by MM7 on 2010-01-10
Can anyone help?  My finger is hovering over the uninstall Ubuntu button (I've had to reinstall 3 times in 2 weeks so not too impressed).

---

### Post by MM7 on 2010-01-10
No worries.  It's gone, uninstalled, deleted.

If anyone knows of a reliable Linux operating system that doesn't go wrong every other day then please let me know.  I'm bored of the slowness of Windows XP but at least it's reliable.

---

### Post by drs305 on 2010-01-10
> **MM7 said:**
> No worries.  It's gone, uninstalled, deleted.

If anyone knows of a reliable Linux operating system that doesn't go wrong every other day then please let me know.  I'm bored of the slowness of Windows XP but at least it's reliable.
MM7,

Sorry your first experience with Ubuntu was not a good one and it's obvious you are giving Ubuntu a fair chance. Timing seems to have been a factor, as it may be you tried Wubi just as a bug with the ntfs module was making the rounds and before the fix was released.

Most users have found the normal installation of Ubuntu very satisfactory. If you ever decide to try the more traditional way of running Ubuntu we would certainly like to see you return.

---

### Post by shadowlands on 2010-01-10
Is there a way to get the ubuntu version that came out before karmic so folk can switch back?  I had to reinstall and the kernel is now 17 not 14.

---

### Post by drs305 on 2010-01-10
> **shadowlands said:**
> Is there a way to get the ubuntu version that came out before karmic so folk can switch back?  I had to reinstall and the kernel is now 17 not 14.

If you are looking for Jaunty or earlier releases, go here:
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/")

If you are looking for a previous kernel, check in Synaptic to see if it is still on your computer or you can always get it from [http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic]("http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic")

---

### Post by Thorbear on 2010-01-16
I've installed ubuntu using the windows installer, on an NTFS partition (M: )
When I boot, I get to chose between Windows and Ubuntu.
When I chose Ubuntu, I get this:```
GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>_
```I've tried everything described earlier in this thread, but still get the same.
Help? =)

---

### Post by kansasnoob on 2010-01-16
Have a look here:

[http://ubuntuforums.org/showpost.php?p=8627484&postcount=12](http://ubuntuforums.org/showpost.php?p=8627484&postcount=12)

Better yet:

[http://ubuntuforums.org/showpost.php?p=8623043&postcount=24](http://ubuntuforums.org/showpost.php?p=8623043&postcount=24)

---

### Post by Thorbear on 2010-01-16
> **kansasnoob said:**
> Have a look here:

[http://ubuntuforums.org/showpost.php?p=8627484&postcount=12](http://ubuntuforums.org/showpost.php?p=8627484&postcount=12)

Better yet:

[http://ubuntuforums.org/showpost.php?p=8623043&postcount=24](http://ubuntuforums.org/showpost.php?p=8623043&postcount=24)
Well, thank you for the reply.
Altho, as far as I can tell, the solutions described in those two links, are the same as the ones described here, that I had already tried.

However, I unsinstalled Ubuntu, and reinstalled it, and now everything seems to be working fine =)

---

