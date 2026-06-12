---
title: "Building new PC - want to dual boot U and XP.  Please help"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by w@ntonsoup on 2009-04-26
I've never used any -nix anything before ever.  It's been MS-DOS, DR-DOS, Windows 3.0/95/98/ME/2K/XP/Vista for me over the last 24 years.  But, like most people, I am sick of the BS and have heard all of the praise heaped on Ubuntu.  That's my background.

I'm building a new PC from scratch because my current one is old and in shambles from AVG repairing a virus by completely farking up my XP installation.  I want the new PC to run both U and XP, and I'm happy to load Ubuntu first and XP down the road when I have the free time to install it and take the time off work to set it all up (sarcasm.  But XP is a pain to install as we all know.)

So how do I properly install Ubuntu on a brand new system while allowing me later to dual-boot install XP?  Or should I really do a preliminary install of XP first?  Please tell me what to do, oh Ubuntu gurus of the interwebs.  I am at your mercy.

---

### Post by Spiritous on 2009-04-26
> **w@ntonsoup said:**
> I've never used any -nix anything before ever.  It's been MS-DOS, DR-DOS, Windows 3.0/95/98/ME/2K/XP/Vista for me over the last 24 years.  But, like most people, I am sick of the BS and have heard all of the praise heaped on Ubuntu.  That's my background.

I'm building a new PC from scratch because my current one is old and in shambles from AVG repairing a virus by completely farking up my XP installation.  I want the new PC to run both U and XP, and I'm happy to load Ubuntu first and XP down the road when I have the free time to install it and take the time off work to set it all up (sarcasm.  But XP is a pain to install as we all know.)

So how do I properly install Ubuntu on a brand new system while allowing me later to dual-boot install XP?  Or should I really do a preliminary install of XP first?  Please tell me what to do, oh Ubuntu gurus of the interwebs.  I am at your mercy.

PLEASE Install Ubuntu first! 
[https://help.ubuntu.com/9.04/switching/installing-partitioning.html](https://help.ubuntu.com/9.04/switching/installing-partitioning.html) for patitioning
[https://help.ubuntu.com/9.04/switching/installing-get.html](https://help.ubuntu.com/9.04/switching/installing-get.html) for disk
[https://help.ubuntu.com/9.04/switching/installing.html](https://help.ubuntu.com/9.04/switching/installing.html) for more information on installing

---

### Post by DracoJesi on 2009-04-26
you want to boot me o.0
 *points to title*

---

### Post by 4Orbs on 2009-04-26
If it were me, and I felt that I would really need XP at some future time, then XP would be installed first. That way I would never need to mess with the XP partition again (except maybe resizing it smaller to make more room for a fresh Ubuntu install or triple booting and distro hopping). On the other hand, if I were keeping XP simply as a security blanket while evaluating Ubuntu, then Ubuntu would still be installed second (because it's so quick and easy to install, again and again).

---

### Post by freak42 on 2009-04-26
GO with the preliminary XP install first, afaik it's much easier to install ubuntu after windwos in a dualboot setup. 

You just have to slap XP on there (which shouldn't take long on a new computer anyhow) and proceed with installing ubuntu.

hth

---

### Post by w@ntonsoup on 2009-04-26
That was my assumption - I'll install XP and then setup everything for Ubuntu per the instructions.  Appreciate the advice.

---

### Post by telmac on 2009-04-26
within that type of thing, I have been unable to install any othe operating system on my ubuntu machine.

---

### Post by MrWES on 2009-04-26
> **w@ntonsoup said:**
> I've never used any -nix anything before ever.  It's been MS-DOS, DR-DOS, Windows 3.0/95/98/ME/2K/XP/Vista for me over the last 24 years.  But, like most people, I am sick of the BS and have heard all of the praise heaped on Ubuntu.  That's my background.

I'm building a new PC from scratch because my current one is old and in shambles from AVG repairing a virus by completely farking up my XP installation.  I want the new PC to run both U and XP, and I'm happy to load Ubuntu first and XP down the road when I have the free time to install it and take the time off work to set it all up (sarcasm.  But XP is a pain to install as we all know.)

So how do I properly install Ubuntu on a brand new system while allowing me later to dual-boot install XP?  Or should I really do a preliminary install of XP first?  Please tell me what to do, oh Ubuntu gurus of the interwebs.  I am at your mercy.

Don't know what your uses are for XP, but you might also consider installing XP in a VirtualBox.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

Bill

---

### Post by powel212 on 2009-04-26
I can't promise that my way will work for you but this is the best way I know for someone new to Ubuntu. I have used this method many many times and it is easy.

The best thing is to have 2 separate hard drives. One for operating systems and one for data. If this can not be accomplished then 3 partitions on one drive will also work.

Install xp first. When you first start the xp install use the advanced partitioning feature on the install disk. Example on a 300G drive create one partition 100G for xp, and a 80G partition for Ubuntu and the final 120G for data. *It is important to create the partitions with different sizes because it will be easier to identify the drives in the future if you ever run into trouble with them*.

The xp partition and the data partition can be formatted to NTFS, But, "important", leave the 3rd 80Gig partition unformatted as a blank partition. We will deal with it later.

At this point you can run the rest of the xp install.

After the xp install is 100% complete and you are happy then you can insert your Ubuntu "Live" CD and boot from it "try Ubuntu without changes to my computer"

Once booted and running from the Live cd, chose install.

enter the appropriate information, country, language etc but when you arrive at the partition screen you will have a choice where to install Ubuntu. 

This is the important part and this is why we left that unformatted space before. You can now chose to install Ubuntu to "the largest continuous free space" In doing so Ubuntu will now install to the empty space we left unformatted. 

Allow the rest of the install to run and reboot.

Upon reboot you will be greeted with Ubuntu's Grub screen where you will be given a short list of options to boot from. there will be Ubuntu at the top and Windows xp at the bottom. Just use the arrow keys to select the system you want to boot. 

Now you are almost done. But once you have booted into Ubuntu for the first time from the hard drive you won't see the xp partition on your desktop so we need to install a little applet so all your partitions will be mounted automatically. 

Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications"

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to; enable read and write to internal and external drives.

the next time you boot all your drives will appear on the desktop.

I hope that helps.

Powel

---

### Post by Spiritous on 2009-04-26
> **MrWES said:**
> Don't know what your uses are for XP, but you might also consider installing XP in a VirtualBox.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Bill

Just from experience its seriously alot easier if you do ubuntu then XP, though you can do it other way round... Just my opinion :)

---

### Post by powel212 on 2009-04-26
If Ubuntu is installed first then after installing xp Grub will need to be restored. Not a big deal but this process can be a bit intimidating for newer users. But with xp in first and the correct preliminary partitioning is done then there is no need to *sudo gedit grub files* etc. When I am introducing friends to Ubuntu I try to keep it nice and simple and give them GUI options for editing, installing, etc. I hope this way they will find Ubuntu closer to what they are used to. Linux is very powerful but lets let our new users ease into it.

Respectfully

Powel

---

### Post by BugFixBug on 2009-04-26
One disadvantage of installing XP after you already installed Ubuntu is that xp will replace GRUB with its own bootloader. so after you installed XP you wont get a list of installed OS'es but only XP (or any other windows OS you installed along with XP) will be bootable.

So you will have to reinstall the grub bootloader.
[this describes how to reinstall the GRUB bootloader.]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by theozzlives on 2009-04-26
You can run XP in a [VirtualBox]("http://www.virtualbox.org"). Otherwise I'd say XP first and specify half your drive for XP leave the other half free for Ubuntu. I tried to do XP after the fact and it named my C: drive F:.

---

### Post by Sidewinder1 on 2009-04-26
Doesn't XP also format the entire drive on which it is to be installed? That has always been my impression, necessitating two separate drives or XP being installed first. I may be wrong...It's been a while since I installed any M$ products; at least on machines that I own.
BTW, The above is correct: XP installs bork GRUB.
Side

---

### Post by Ticketoride on 2009-04-26
> **w@ntonsoup said:**
> So how do I properly install Ubuntu on a brand new system while allowing me later to dual-boot install XP?  Or should I really do a preliminary install of XP first?
My personal Preference has been to install each OS as a Primary Partition on 2 separate HDD Drives. In this Fashion the Installation Order doesn't Matter, but the Win Drive would have to be disconnected so that the GRUB Boot Loader doesn't get piled onto the Win Partition, while installing Ubuntu.

I already run a dual Boot Win2k/XP on HDD 1, for which I have Restore Images going back several Years which would knock out Linux in the Event I'd have to use them again at some Point, and the Win2K/XP Images are interdependent on each other.

Of all the Headaches I have had with 8.04/9.04, boot up Problems was never one of them, although the Final Release 9.04 never did install a Bootloader and had to be scratched and re-installed again.

In this Fashion you'll loose 30 Seconds of your Life negotiating the Drive Boot Order via the BIOS every Time would want to load the other OS.

---

### Post by powel212 on 2009-04-26
During the xp or vista or win7 setup you can configure partitions before install. However if this option can not be utilized for any reason one can also use the Ubuntu live cd's Gparted to setup the partitions before the initial xp install. Gparted is easy to use and there are lot's of posts on how to use it.

p.

---

### Post by powel212 on 2009-04-26
To "Ticketoride"

If in the future you find yourself wanting to run a fresh install. You might want to try a triple boot using Grub. I have set up machines to do this before. Then no switching in the BIOS is necessary.

Using one drive for the OSs 

First create the 3 partitions

second install xp

second install Win2000(NT)

this will create a windows boot loader dual boot.

Last install Ubuntu

When you reboot now you will have a nice clean Grub with ubuntu, win2000 and xp 

The same thing can be done with other OSs as well. Even a triple boot; win7, OSX, and Ubuntu

p.

---

### Post by SuperSonic4 on 2009-04-26
> **Sidewinder1 said:**
> Doesn't XP also format the entire drive on which it is to be installed? That has always been my impression, necessitating two separate drives or XP being installed first. I may be wrong...It's been a while since I installed any M$ products; at least on machines that I own.
BTW, The above is correct: XP installs bork GRUB.
Side

Perhaps but it's easily circumvented by using a live CD to make an ntfs partition and forcing XP to reside on there :]

---

### Post by wizard10000 on 2009-04-26
> **BugFixBug said:**
> One disadvantage of installing XP after you already installed Ubuntu is that xp will replace GRUB with its own bootloader...

I don't do dual boot machines any more but when I did I always preferred to use a Windows bootloader to call grub rather than the other way around - that way I could reinstall either OS without trashing my boot sector.

Here's how you do it -

First, install grub on the first Linux partition instead of on the MBR - then use dd to make a copy of that boot sector like this:

 dd if=/dev/sdaN of=linux.bin bs=512 count=1

where /dev/sdaN is the location of your first Linux partition.

Save linux.bin to a thumb drive.

Okay, now install Windows, which will trash grub - but fear not, we'll fix it.

Once you've got Windows running copy linux.bin to the root directory of your c: drive and edit boot.ini to add an entry to call grub like this:

 c:\linux.bin="Ubuntu 9.04"

Easy, yes?

---

### Post by powel212 on 2009-04-26
Easy for us. But let's go easy on the newcomers.

Anyone wondering what dd is:

man dd gives us;

```


DD(1)                            User Commands                           DD(1)

NAME
       dd - convert and copy a file

SYNOPSIS
       dd [OPERAND]...
       dd OPTION

DESCRIPTION
       Copy a file, converting and formatting according to the operands.

       bs=BYTES
              force ibs=BYTES and obs=BYTES

       cbs=BYTES
              convert BYTES bytes at a time

       conv=CONVS
              convert the file as per the comma separated symbol list

       count=BLOCKS
              copy only BLOCKS input blocks
 Manual page dd(1) line 1/149 13%


```

p.

---

### Post by wizard10000 on 2009-04-26
> **powel212 said:**
> Easy for us. But let's go easy on the newcomers.

You're absolutely right - this is an absolute beginner forum.

My bad  :)

---

### Post by Ticketoride on 2009-04-28
> **powel212 said:**
> If in the future you find yourself wanting to run a fresh install. You might want to try a triple boot using Grub. I have set up machines to do this before. Then no switching in the BIOS is necessary.

Using one drive for the OSs 

First create the 3 partitions

second install xp

second install Win2000(NT)

this will create a windows boot loader dual boot.

Last install Ubuntu

When you reboot now you will have a nice clean Grub with ubuntu, win2000 and xp
Thats exactly what I don't want to do, and why I keep Linux & Windows completely separate from each other. Tons of daily Threads about Grub Errors are more than ample Testimony of what I don't want to do.

I think the last Complication I read about was about IDE/SATA Conflicts and nothing would boot either OS after installing Linux. No thanks, I prefer the 30 Seconds of BIOS Nuisance over Booting Complexities any given Day.

Keeping it simple ...

---

### Post by wizard10000 on 2009-04-28
> **Ticketoride said:**
> Thats exactly what I don't want to do, and why I keep Linux & Windows completely separate from each other. Tons of daily Threads about Grub Errors are more than ample Testimony of what I don't want to do.

If you've got multiple operating systems on a machine *something* has to tell your hardware which OS to boot.  That can be a Windows bootloader, a Linux bootloader like grub or lilo or a third-party bootloader.

IMO the "30 seconds of BIOS nuisance" isn't a real great idea as there shouldn't be more than one partition in a computer with the boot flag set.  Some hardware will support it, some won't - but just sticking two bootable hard drives in a machine and switching them around with a BIOS call probably isn't the best way to do something.

Believe me, I do understand your hesitation here.  More years ago then I care to remember I built this bizarre quad-boot machine with Win 3.1, Win 95, OS/2 and Linux on it just because I could - I think a lot of geeks go through this phase.  Used a utility I don't think they make any more called System Commander to manage the whole mess.  I've gotten a whole lot smarter since then  ;)

Have you given any thought to just running Windows in a virtual machine?  Beef up the Linux system a little bit to where it's got enough stones to run XP in a VM like VirtualBox and you've got everything you need.

BTW - I played around with a Windows 7 beta in VirtualBox here and this machine's kinda wimpy - old hyperthreading 2.8GHz Dell Precision Workstation with only a gig of ram and Windows 7 ran well enough in a VM to play around with it a little.

Talk about someone having too much time on their hands - here's a screenshot of *four* OS running on the same desktop cube.  I did this about a year and a half ago just to prove I could - My main machine had Windows XP running in a VM and my test box had Vista running in one - I used a remote desktop application to display the test box in a fullscreen window on the cube.

[IMG]http://ebassist.com/pix/desktop-virtualbox-both.jpg[/IMG]

Neither of these machines dual booted  ;)

Good luck -

---

### Post by lkraemer on 2009-04-28
Well,
Everyone has lots of good ideas.  But, no one posted any good
Dual Boot Sites URL's with more information for the newbie.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


Here are some additional comments about Dual Booting.

Each Physical Hard Drive has a limit of 4 (Maximum) Primary Partitions.
So, if Xp is loaded first, and there is a Recovery Partition, then two
remain for Linux (/ and Linux-Swap).  Yes, you can use extended partitions
but I usually don't.  Or, if you have XP as the first parition, then you
can have Root (/), and home, and Linux-Swap.  Swap is typically two times
your available RAM.

And for Dual Boot Systems you will eventually need SuperGrub.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Having done both, I'm in favor of VirtualBox running on a Linux Host,
with a Guest OS of XP, for those moments you absolutely must use XP.

lkraemer

---

### Post by powel212 on 2009-04-28
Okay "Wizard 10000" Now you've got me curious. I have tried to run a dual boot Ubuntu, OSX on my current hardware but couldn't get OSX to recognize some crucial to operation hardware. But looking at your "Cube" I am wondering if I can set up OSX in a virtual box??? You know any good tutorial sites on how to accomplish this. I have not done much virtual Boxing as I find wine takes care of the few MS needs I occasionally come across. 

My question again is good tutorial sites for running OSX inside Ubuntu.

Thanks for your post and picture.

BTW I actually have no use whatsoever for MAC OS at all but I would love to run the virtual box just to show my mac head friends how they waste their money. haha

Nice

Powel

---

### Post by poltr1 on 2009-04-28
I installed XP opn my laptop first, then Ubuntu.  When I installed XP, I knew I wanted to install Ubuntu, so I left some unpartitioned space when I partitioned the hard drive.  After installing XP, I then installed Ubuntu, which found the unpartitioned space and partitioned it.  It's been working fine for me ever since.

---

### Post by wizard10000 on 2009-04-28
> **powel212 said:**
> Okay "Wizard 10000" Now you've got me curious. I have tried to run a dual boot Ubuntu, OSX on my current hardware but couldn't get OSX to recognize some crucial to operation hardware. But looking at your "Cube" I am wondering if I can set up OSX in a virtual box??? You know any good tutorial sites on how to accomplish this. I have not done much virtual Boxing as I find wine takes care of the few MS needs I occasionally come across. 

My question again is good tutorial sites for running OSX inside Ubuntu.

Thanks for your post and picture.

BTW I actually have no use whatsoever for MAC OS at all but I would love to run the virtual box just to show my mac head friends how they waste their money. haha

Nice

Powel

I don't think you can, as Apple's license agreement requires that OS X be installed on Apple hardware - don't know whether anybody's actually done it.

---

### Post by poltr1 on 2010-03-19
I recently attempted installing XP on a system already running Ubuntu.  (This is not the same system I'm referring to in my previous post on this thread.)

First I used gparted to create an NTFS partition.  Then I ran the XP install disk.  Then after Windows was installed in that partition, I had to reinstall grub from the Ubuntu distro CD, so that both OSes could be found.  Windows has a bad habit of not playing well with others.

---

