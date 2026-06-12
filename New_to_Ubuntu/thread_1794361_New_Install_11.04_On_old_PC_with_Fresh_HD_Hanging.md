---
title: "New Install 11.04 On old PC with Fresh HD Hanging"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Randy Flagg on 2011-06-30
I just got an old Dell with 256MB Ram and Celeron processor.  The original HD has the click of death so I am trying to install 11.04 to a new HD.  I did a low level format of the drive with an HD utility but no matter what I do the install just sits on the start screen with the icon spinning.

Is there something else I have to do to prep the HD?

---

### Post by raja.genupula on 2011-06-30
check ubuntu specifications once 
i think you need 512 mb of ram

---

### Post by Randy Flagg on 2011-06-30
Is there possibly a lighter version of Ubuntu that might be okay with 256Meg?

---

### Post by wildmanne39 on 2011-06-30
> **Randy Flagg said:**
> Is there possibly a lighter version of Ubuntu that might be okay with 256Meg?Hi, you can try xubuntu or Lubuntu, both are lighter then 11.04 natty. You could also try the 10.04 Xubuntu, or an alternate install cd of one of the distrobutions. I am going to give you a link for low memory install but I do not think it is needed.
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by egalvan on 2011-06-30
> **Randy Flagg said:**
> I just got an old Dell with 256MB Ram and Celeron processor...

HOW old is the Dell?

>  I am trying to install 11.04 to a new HD.

The machine may be too old to see the new drive...

>   **I did a low level format** of the drive with an HD utility but no matter what I do the install just sits on the start screen with the icon spinning.

"low-level formats" went the way of MFM drives...
all software avaliable to "regular" users will only do "high-level" formats...
"low-level" is done at the factory (or shop) with special equipment... not generally available (or affordable) by mere mortals.

> Is there something else I have to do to prep the HD?

I use dban to fully wipe any drive I use.
dban can be found at dban.org

And about 30 minutes ago, i tested an old IBM ThinkPad T40 with **256MB** RAM and **no HD**... 
**used a 10.04LTS LiveCD** to do a "Try Without Installing".
Ran sloooooooow, but it ran. Allowed me to test the hardware.

Try disconnecting the HD and boot the CD...
Let us know what happens.

---

### Post by dFlyer on 2011-06-30
You need to try a lighter version of Linux. I believe Unity uses a mim of 512 meg.

---

### Post by Kixtosh on 2011-07-01
> **dFlyer said:**
> You need to try a lighter version of Linux. I believe Unity uses a mim of 512 meg.Never a truer word, take note Randy! I've played around quite a bit with various options on older machines (the two "worst" ones are in my signature).

Basically, I would advise:

1) Use only LTS (Long Term Support) releases. There's no sense trying to update such old computosaurs with every six  month release. Every two years is quite often enough! The current one is Lucid Lynx 10.04.

2) If possible, by an extra stick of RAM from eBay or somewhere. Try to get to 512MB or above. It's a huge improvement over just 256MB. This is probably a $20 investment (it was for me, the last time I tried). There is no need (or real advantage that I can notice) to having 1GB of RAM or more in these older machines (unless dual booting with Windows).

3) Any LXDE desktop is going to be better than a full Ubuntu installation. The "pseudo-cloud" Peppermint is wonderful, especially if you are always connected to the web, and can make use of the built in menu links that offer seamless access to office applications from Google (word processor, e-mail, spreadsheet). Lubuntu is wonderful, but more like a "classic" O.S., with office applications residing normally, on your hard drive. Xubuntu is just as wonderful IF you add the LXDE desktop, instead of the default Xfce. All of these are great alternatives to Wary Puppy if you have at least 512MB of RAM.

4) Wary Puppy 512 is a specific solution for old machines, and it's  wonderful! It is, by far, the easiest way to get up and running with  Linux, as long as you can boot from a CD drive. There is no need to  remove Windows or create special partitions either. It is not as fast to  boot as any LXDE version of Ubuntu or Xubuntu, but [COLOR=DarkRed]it is probably the  best option today for just 256MB of RAM or less, and a PII 500MHz[/COLOR]. It includes a super light browser  and fast, lightweight office applications. Please note that after saving  certain small files to your hard drive (including Windows NTFS or FAT  partitions, if need be), that take up less than 1GB altogether, Puppy  will boot faster.

How fast is the CPU on this old PC? A complete installation of Ubuntu Lucid Lynx works perfectly with 768MB of RAM and a 1GHz PIII CPU. With even those lowly specs, I would prefer to loose ten seconds of boot time and still have a full version, rather than any lightweight distro. I would consider those specifications a minimum for using OpenOffice or LibreOffice, otherwise use the lighter and faster AbiWord and Gnumeric applications.

Ubuntu, and all of the LXDE options mentioned above, will take less than one minute to boot; fewer than ten seconds to shut down. Wary Puppy will require slightly more than one minute to boot, and about fifteen seconds to shut down.

A link to Wary Puppy:

[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

A link to more of my musings (which I simply can't get enough of!) in another thread from almost a year ago (before Wary Puppy was released):

[http://ubuntuforums.org/showpost.php?p=9711681&postcount=38](http://ubuntuforums.org/showpost.php?p=9711681&postcount=38)

---

### Post by wep940 on 2011-07-01
I have an old Dell 2650 laptop, and it hangs like that when I try 10.04, 10.10, 11.04.  Can't use the keyboard or the mouse and I have to power off to reset things.  I was told in my thread it is the old nvidia built-in graphics, so you may also want to check that.

I don't know why, but for some reason OpenSuse (another Linux distribution) runs fine (I just have to figure out how to get my wireless working).

So, check your video as well - it could be it's sharing part of your main memory, and if so, the amount of main memory actually available to the OS could be considerably less than 256mb.  If this is the case there is usually an option in the BIOS setup screens to set the amount of video memory - you may want to try setting it to a lower limit.

---

### Post by amjjawad on 2011-07-01
With 256MB of RAM, better stay away from GNOME. Forget Unity for sure.

[http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)
It's a bit old but you'll find lots of other alternatives.

You could also have a look at this: [http://distrowatch.com/search.php?category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active)

I would strongly recommend **Lubuntu 11.04** (which is way better than 10.04). It's one of my favorites.

Slitaz and antiX are great too but both are not based on Ubuntu.

Even Xubuntu might be slow. Never tired it on 256MB.

---

### Post by wep940 on 2011-07-03
I don't know if it will work for your problem or not, but it's worth a shot.  I pressed F6 so I could get the boot menu, then added "apci=off" to the linux line for boot.  This turns off the power management - which my 2650 laptop only partially supports.  Adding this fixed my problem and I now have full mouse and keyboard control and the system no longer appears frozen.

---

### Post by Randy Flagg on 2011-07-04
Wow, I really appreciate all the info.  I am going to bookmark this thread for future use. Before reading this I decided to try another machine. It's an older CPU PII but I have 2 gigs ram for it. 

I tried loading ubuntu 11.04 and had the same problem. So I switched to xubuntu and the live disk seems to work fine and even picks up the HD.

The issue i am having now is (sorry for the repeat from another post) that xubuntu doesn't recognize my keyboard in the initial install screen (the one where it asks for the language). So it auto boots to the live cd. When the desktops loads my keyboard works and I can click on the install icon. I do that and it runs through a bunch of loading screens. Then brings me to a locked desktop where it looks like I am supposed to login but I can't.

---

### Post by Kixtosh on 2011-07-04
I think that in your case, it's well worth trying Wary Puppy. You can even install it on your hard drive if you wish (although that doesn't make Puppy faster than loading from a CD, because of the way Puppy works in RAM). Puppy only gets speed benefits when you save your user files so that the session is saved, and your configuration. It may well detect the keyboard you are having problems with. Using the usual "run Puppy from CD" method, you won't even have to delete or modify any existing O.S. to use it. The download is also much smaller than most other alternatives.

I think Lubuntu or Peppermint would also be worth a try for you, although it's probably less likely that they will do much better than Ubuntu or Xubuntu. Note: there is no current LTS release version of Lubuntu, so you can just use 11.04.

[http://lubuntu.net/](http://lubuntu.net/)
[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by Randy Flagg on 2011-07-04
I really would like to stick with the full version of xubuntu.  My specs are far off from yours.  I am running a PII with 2 gigs ram.  If I have to get a ps/2 keyboard to get it installed I will.

I just tried a different usb keyboard and that did't fix it.

---

### Post by jfbooth on 2011-07-04
I run Xubuntu 11.04 on an old Windows ME machine with 512MB and it 'just' runs fast enough to use.  I doubt Xubuntu would run on 256.

---

### Post by Randy Flagg on 2011-07-04
I am trying a different machine.  pII 2 gigs ram.  I just tried a ps/2 keyboard and it allowed me to install.  It just went to a blank screen with just the mouse cursor.  I am giving it a minute to see if it does anything from here.

---

### Post by Randy Flagg on 2011-07-05
Making progress, after a ton of google searching what I was reading lead me to believe that the problem with my videocard.

So, after some more reading, I finally tried hitting F6 and the install menu and choosing options nomode and ACPI off.

that got me part of the way there.  I get past the install updates online screen and I get a installation failed error.

Any ideas?

---

### Post by amjjawad on 2011-07-05
> **Kixtosh said:**
> I think **Lubuntu** or Peppermint would also be worth a try for you, **although it's probably less likely that they will do much better than Ubuntu or Xubuntu**. 

Lubuntu is much faster than Ubuntu. I have tested both on P4 with less than 512MB of RAM. 
Not sure about Xubuntu though. I don't like it much.

> 
Note: there is no current LTS release version of Lubuntu, so you can just use 11.04.
[]("http://peppermintos.com/")
Lubuntu 10.04 is based on Ubuntu 10.04 which is LTS. Same Core OS but it's just the Desktop Manager which is different. It's like a skin.
With each release of Ubuntu, there will be a release for Lubuntu and same goes for Kubuntu and Xubuntu.

---

### Post by Kixtosh on 2011-07-05
> **amjjawad said:**
> Lubuntu is much faster than Ubuntu. I have tested both on P4 with less than 512MB of RAM.  ...Definitely faster, I agree, but I wasn't commenting on that. I was commenting more on compatibility problems. Wary Puppy is very clever at detecting older hardware that doesn't work in Ubuntu or Lubuntu.

Xubuntu has not been very useful for me, although it is faster than regular Ubuntu on older material, _until_ I install the LXDE desktop from the Ubuntu Software Center first. Then it's at least 90% as lightweight as Lubuntu, and possibly better than Lubuntu in some respects.

10.04 Lucid Lynx is not officially a LTS release, by the way, where Lubuntu is concerned. It won't have Long Term Support with that distro. That may change with 12.04 LTS, if Lubuntu gets recognized as an "official" distro.

---

### Post by cre8ive65 on 2011-07-05
I believe i had the same machine, with a ram upgrade to 1gb ubuntu 10.04 ran perfect

---

### Post by Randy Flagg on 2011-07-05
Well, I have made a lot of progress but still don't have a full install.  I will try and make out the steps as I conquered them.  Where I left off was that I couldn't run the install from the desktop.  It would just take me to a locked login screen.

So, I got a PS2 keyboard which allowed me to get to the boot install.  That would hang after a couple of loading screens.

So I F6ed and selected nomodeset andno ACPI.  That got me to install screens but I would get a language error.

I assumed it was having problems copying files to the HD so I booted the Live CD and gparted the drive as ETC4.  (this was a fresh drive with fat32 partitions.

Oh, yeah I forgot somewhere in there I switched to Xubuntu 10.04. (I tried lubuntu with no luck)

Now, I basically get through a whole install except for the restart.  when i go to restart the PC hangs and I have to hard boot.  When I reboot I get the grub rescue prompt.

There is obviously and issue with the grub.cfg but I can't figure out why.

Trying a couple of different things now.

---

### Post by amjjawad on 2011-07-06
I have read the whole thread all over again to understand what's going on with you.

Let's see ...

> **Randy Flagg said:**
> Well, I have made a lot of progress but still don't have a full install.  I will try and make out the steps as I conquered them.  Where I left off was that I couldn't run the install from the desktop.  It would just take me to a locked login screen.


1- What Distro are you trying to use right now? Try to use the lightest Distro and if one did not work for you, there are at least 10 other alternatives to try out - check my previous post at page1.

2- After you downloaded the iso file from the website of ... say Lubuntu 11.04 or 10.04 ... have you checked [**md5sum**]("https://help.ubuntu.com/community/HowToMD5SUM")?

3- NOT SURE I HAVE READ THAT YET. Are you sure your CD Drive is working probably?

4- When you burned the LiveCD, make sure the Burn Speed is as slow as possible. I prefer 8x.

5- One of the previous suggestions by one of the posters was to unplug your new HDD and try the LiveCD without it. Have you done that?

6- If there is something wrong with your CD Drive, you may need to try the LiveUSB but if your machine does not have that ability (to boot from USB), then you need to either:
**[Plop]("http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")**
or
Connect your HDD to another machine, install the system and plug it back to where it was. However, don't expect much. I had tired that with 12 years old broken laptop (P2 and 64MB RAM) for a month or more ... at the end, only Linux Mint LXDE 9 worked. I guess I posted the thread at page1. Your machine is much better than mine ;)


> I assumed it was having problems copying files to the HD so I booted the Live CD and gparted the drive as **ETC4**.  (this was a fresh drive with fat32 partitions.
I think you mean ext4 :)

While you are on GParted, go to Device Menu (if I'm not wrong) and then Partition Table. Try to re-create a new partition table, and then try to start partition your HDD "before" the installation.

You need 3 partitions
/ (root) which should be ext4
/home (home partition) which should be ext4 too.
and SWAP which is swap-Linux (remember, as long as your machine is old and your RAM is just 256MB, I prefer to choose more than 512MB as swap. I would go for 1GB.

Once done, start to boot from LiveCD and see what will happen.
 

> Oh, yeah I forgot somewhere in there I switched to Xubuntu 10.04. (I tried lubuntu with no luck)

What do you mean by "no luck"? have you tired Lubuntu 11.04 or 10.04?


> Now, I basically get through a whole install except for the restart.  when i go to restart the PC hangs and I have to hard boot.  When I reboot I get the grub rescue prompt.

There is obviously and issue with the grub.cfg but I can't figure out why.

Could you please explain how did you install?

Is Linux the only OS on that machine? or you're dual-booting with Windows?

You need to provide more details so that we could help you and understand your problem better :)


By the way, one of the suggestions by one of the posters was that your old machine may not be able to deal with the new HDD. That's also could be the reason but perhaps it's not exactly what is going on with you.  Just a thought!

Waiting for your reply for my above Qs :)

---

### Post by wep940 on 2011-07-06
Regarding the new disk drive and the older PC:

Most older PC's used IDE as the hard drive interface.  The BIOS was setup such that the interrupt to handle disk I/O meant it could not address more than 130gb.  I ran into some very strange problems when I tried to install to another old laptop until I researched this quite a bit.  To get around the problem, I had to create a "dummy" partition at the END of the disk to logically use the disk from 130gb to the end.  This means that no addressing will try to address more than 130gb.  After that partition is created, THEN create the Ubuntu partitions in the remaining space at the beginning of the drive.  

So, for example, if this new drive is say 250gb, and your partitions are such that any part of Ubuntu is above the 130gb limit this could be causing all kinds of problems for you.  Say for instance you put swap at the end of the drive - big problem!  Same if root or home goes above that 130gb.  This would mean that the existing partitions would need to be removed, a "dummy" partition of 120gb created at the END of the disk, then the Ubuntu partitions created in the empty space at the beginning of the drive.

I won't say this is all of the problem, but it's possible it is some of it depending on the size of the new drive.  As I said, I had all kinds of strange things happen.

---

### Post by amjjawad on 2011-07-06
> **wep940 said:**
> As I said, I had all kinds of strange things happen.

Believe me, you're not alone ;)

---

### Post by Randy Flagg on 2011-07-06
I am going to try and answer all the questions here. 

I am currently trying xubuntu 10.04.

I haven't tried the md5 check. The directions I found for it were way confusing (even fir Linux). Also the the original ubuntu disk was a known good disk. 

Considering 90 percent of the install works I think my cd rom is good.

I turned down the burn speed to 10x. This is lowest my sys will go.

I am now able to consistently boot into the live cd of xubuntu 10.04 or 11.04.

I have tried lubuntu 11.04 but it wouldn't install. This was probably because I needed to turn noacpi and nomodeset on. 

I after research late last night and reading your emails. I am convinced this is a hd issue. I am using 300 gig drive. 

So I think I will try three things today. 

First, recreate the partitions a described above. Can anyone give more specifics of the partition setup?

Second install to a 40gig drive I have. 

Third upgrade my ancient bios to something that supports larger HDs.

---

### Post by wep940 on 2011-07-06
Yeah, if you put in a 300 gig drive and the PC is old enough, that will cause all kinds of problems.  First look in your BIOS set up screens and see what it has detected the hard disk as, particularly it's size.  You also need to know the drive is IDE, not SATA.  When you got the new 300gb drive was it IDE or SATA?  If it's not IDE this limit does not apply.

If it were me, and it's an IDE drive, and I was suspecting this was the problem, I'd first put in a driver smaller than 130gb.  If you install anything bigger, the space over 130gb will just be wasted space - you can't address it.  So in your example, you'd be wasting 170gb of you 300gb drive. 

If you do stick with the 300gb drive you'll be wasting the space, but you could do the following:


[LIST]
[*]boot the live CD
[*]start the install
[*]when it gets to partitioning specify manual
[*]get rid of all existing partitions
[*]create a partition of about 12gigspecify as EXT4 and mount point of /
[*]create a partition of about 1 gig for swap - specify as swap
[*]create a partition of about 115gig or little less, specify as EXT4 and mount point /home
[*]create a partition that uses all the rest of the space on the drive - it won't make any difference what you do with it, but make sure it is *NOT* marked for formatting
[*]continue on with the install process
[/LIST]
That should get you going.

BTW - you probably won't find a BIOS for an older system to change it to support the larger drives.  For those interested, this is the difference between IDE and EIDE.

---

### Post by Randy Flagg on 2011-07-06
Well I now have a working xubuntu 10.04 setup.  I gave up on the PII machine.  It may have worked in original condition but with me adding new parts everywhere it just wasn't working out.

So I went back to celeron with 256meg ram. I think the only issues I had with that machine was fixed by using 10.04 and setting the nomodeset and acpi flags at install.

The install was a lot quicker and xubuntu seems to be running pretty quick. So I am pretty happy with it.  I even set the partition to the whole 300 gigs. I haven't checked to see if have access to all of it yet but at least it installs and boots.

So I ordered a gig of ram for it and am working on setting it up with openvpn.

Thanks for all the help!

---

### Post by wep940 on 2011-07-06
> **Randy Flagg said:**
> Well I now have a working xubuntu 10.04 setup.  I gave up on the PII machine.  It may have worked in original condition but with me adding new parts everywhere it just wasn't working out.

So I went back to celeron with 256meg ram. I think the only issues I had with that machine was fixed by using 10.04 and setting the nomodeset and acpi flags at install.

The install was a lot quicker and xubuntu seems to be running pretty quick. So I am pretty happy with it.  I even set the partition to the whole 300 gigs. I haven't checked to see if have access to all of it yet but at least it installs and boots.

So I ordered a gig of ram for it and am working on setting it up with openvpn.

Thanks for all the help! 

I know you just got done with a successful install of xubuntu - congratulations by the way! - but if you want to see if the large disk works, there is a way to find out.  Again, this goes on the assumption the drive is IDE (or PATA as it is sometimes called).  This will involve blowing away what you currently have, but if you're game:

- repartition the disk
- place a swap partition of say 1 gig at the END of the disk
- place a EXT4 partition of about 10 gig at the end of the disk as well
- leave the rest of the disk empty - this way you have a big empty space at the beginning of the drive and all of the partitions would be above the 130gb limit
- continue with install 
- see if it boots up - if so, you must not have the size limit

---

### Post by waynefoutz on 2011-07-06
> **Randy Flagg said:**
> Well I now have a working xubuntu 10.04 setup.  I gave up on the PII machine.  It may have worked in original condition but with me adding new parts everywhere it just wasn't working out.

So I went back to celeron with 256meg ram. I think the only issues I had with that machine was fixed by using 10.04 and setting the nomodeset and acpi flags at install.

The install was a lot quicker and xubuntu seems to be running pretty quick. So I am pretty happy with it.  I even set the partition to the whole 300 gigs. I haven't checked to see if have access to all of it yet but at least it installs and boots.

So I ordered a gig of ram for it and am working on setting it up with openvpn.

Thanks for all the help!


Try the LXDE version of PCLinuxOS on that PII. Wary Puppy is a good choice as well.

---

### Post by Randy Flagg on 2011-07-07
> **wep940 said:**
> I know you just got done with a successful install of xubuntu - congratulations by the way! - but if you want to see if the large disk works, there is a way to find out.  Again, this goes on the assumption the drive is IDE (or PATA as it is sometimes called).  This will involve blowing away what you currently have, but if you're game:

- repartition the disk
- place a swap partition of say 1 gig at the END of the disk
- place a EXT4 partition of about 10 gig at the end of the disk as well
- leave the rest of the disk empty - this way you have a big empty space at the beginning of the drive and all of the partitions would be above the 130gb limit
- continue with install 
- see if it boots up - if so, you must not have the size limit

I may try this for fun.  I have bunch of those 300gig disks.  But I am a little confused.  What I was considering trying was making all the partitions before the 125gig mark or so.  I never really did that.  I thought the partitions could only be 130 gig or less.

Wouldn't what your describing fail obviously?  If everything is at the end of the disk I would assume there is no way it would read.

Oh yeah this is IDE.

---

### Post by wep940 on 2011-07-07
If indeed it's IDE, and the computer is old enough, you won't be able to address that beyond 130gb unless the specs for your computer say it EIDE instead of IDE.  So, if you're positive, then no you don't need to run the test.  I just thought it might be fun, if you don't mind, to try it and see what you get for errors.  At one point in a similar situation I had grub fail with a weird error code that ended up being from the not able to address beyond 130gb problem.

---

### Post by Randy Flagg on 2011-07-08
I tired it with another 300gig drive.  Same result.  I made sure all partiitions were under the first 120 gigs and nothing.

I am trying it now with a SATA EIDE controller for fun.

---

### Post by wep940 on 2011-07-08
> **Randy Flagg said:**
> I tired it with another 300gig drive.  Same result.  I made sure all partiitions were under the first 120 gigs and nothing.

I am trying it now with a SATA EIDE controller for fun.

So are you saying you tried the test on the 300gb drive and it failed as expected, and when you placed all partitions under the 132gb limit everything worked?  That's what I would have expected, so I hope that's what you mean. 

Dave ;)

---

### Post by amjjawad on 2011-07-08
Why not using an Old IDE HDD and save your time and energy ? :)
Just a thought.

I have many if you want ;)

---

### Post by Randy Flagg on 2011-07-08
> **wep940 said:**
> So are you saying you tried the test on the 300gb drive and it failed as expected, and when you placed all partitions under the 132gb limit everything worked?  That's what I would have expected, so I hope that's what you mean. 

Dave ;)

No it did not work as expected.  EIDE with my MOBO is no good.  The new HD controller doesn't work either.

---

### Post by Randy Flagg on 2011-07-08
> **amjjawad said:**
> Why not using an Old IDE HDD and save your time and energy ? :)
Just a thought.

I have many if you want ;)

I have at least a dozen old HDs and amazingly none of them are old IDE.  I may try and get like a super simple HD controller.  Or just bag it.  I got the other machine all up and running with Xubuntu 10.04 and OpenVPN works sweet.

So this machine is just something I am playing with.

---

### Post by wildmanne39 on 2011-07-09
Hi, I play with them to sometimes just to see if I can get them to work.

---

