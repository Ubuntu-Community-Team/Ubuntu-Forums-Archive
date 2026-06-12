---
title: "how many partitions?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by pauligit on 2009-01-12
My question is the following: how many partitions should I create for an 8.04 desktop installation? What would be the best for a home user? (Note: I will keep all my "important" files at a second disk, under fat partitions able to be read by Windows XP.)
Cheers,
P

---

### Post by kestrel1 on 2009-01-12
You can let Ubuntu do all the work or create three partitions:
1) OS partition (mount point /)
2) Users partition (mount point /home)
3) Swap

---

### Post by HotShotDJ on 2009-01-12
Absolute minimum for Ubuntu is 2... one for the main filesystem and a second (RAM X 2) for swap.  It is highly recommended that you use 3.  For home use, the following works very well:

Root (/): 10 - 15 Gig
Swap: The amount of RAM you have times 2.
Home (/home): The remainder of the space you have left.

Of course, you haven't told us how much space you will be committing to your Ubuntu installation, so these guidelines may not fit your particular needs.

You do NOT need to set these things up ahead of time.  You can do it as part of running the Installer.

---

### Post by whoop on 2009-01-12
Ubuntu by default creates two partition:
os and user on one, swap on the other.
Some people prefer to create three partitions. One for OS, one for user and one for swap.

If you are just a beginner, maybe go with the default installation scheme (two partitions). Especially if you have a separate driver/partition already.

Once you figure out how much space you use (and where you use it) you can always change your setup.

One of the reasons people use three partitions is that they don't have to wipe there user directory when the do a complete (re-)install.

---

### Post by kestrel1 on 2009-01-12
> **whoop said:**
> 
One of the reasons people use three partitions is that they don't have to wipe there user directory when the do a complete (re-)install.
Which is very useful. If you need to re-install for any reason or just upgrade, your settings are saved. So if you installed Thunderbird, when you re-install there is no need to setup your email accounts etc.

---

### Post by kansasnoob on 2009-01-12
Sounds like a dual boot with Win XP, just do this:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Actually you seem advanced enough to be beyond that, but IMHO there is no need for a separate home partition! Just go to "home" sometime and tick on "show hidden files". Quite often those "hidden" files are not compatible with an upgraded install, and not even with a fresh install if something got messed up.

I like to keep all of my important data on separate partitions or even separate drives!

---

### Post by HotShotDJ on 2009-01-12
> **kansasnoob said:**
> IMHO there is no need for a separate home partition! Just go to "home" sometime and tick on "show hidden files". Quite often those "hidden" files are not compatible with an upgraded install, and not even with a fresh install if something got messed up.This is simply not true.  After over 7 years of using Linux as my primary OS and not only upgrading versions, but switching between distributions (Mandrake, RedHat, SuSE, Gentoo, Kubuntu, and now Ubuntu) I STILL have the same /home directory that I had back when I first started.  It has survived through about 4 hard drives, 3 computers, and all those switches between distributions and version upgrades.  Yes, occasionally one needs to delete some of the configuration files, but it does not happen very often, and when the occasional problem does occur, it is very simple to fix.

Of course, having a separate /home partition does NOT replace the need for frequent and reliables backups of your important data.  In that respect, kansasnoobb is right.

---

### Post by cb34 on 2009-01-12
with my 500gig drive i do:

primary /boot 256megs
primary swp 2gigs (i have 2gigs ram.)
primary / 10gigs
extended
logical /var 5gigs (i'm realizing that 10gigs here would be better for me.)
logical /home 50gigs
logical /home/username/data 400gigs

then i link the /tmp directory to /var/tmp

just the way i do it. :)

---

### Post by kestrel1 on 2009-01-12
> **HotShotDJ said:**
> This is simply not true.  After over 7 years of using Linux as my primary OS and not only upgrading versions, but switching between distributions (Mandrake, RedHat, SuSE, Gentoo, Kubuntu, and now Ubuntu) I STILL have the same /home directory that I had back when I first started.  It has survived through about 4 hard drives, 3 computers, and all those switches between distributions and version upgrades.  Yes, occasionally one needs to delete some of the configuration files, but it does not happen very often, and when the occasional problem does occur, it is very simple to fix.

Of course, having a separate /home partition does NOT replace the need for frequent and reliables backups of your important data.  In that respect, kansasnoobb is right.

I am with you on this one.

---

### Post by HotShotDJ on 2009-01-12
> **cb34 said:**
> i do:
primary /boot 256megs
primary swp 2gigs (i have 2gigs ram)
primary / 10gigs
extended
logical /var 5gigs
logical /home 50gigs
logical /home/username/data 400gigsThat almost looks like a small server setup to me.  A little light on the Swap... but with 2G RAM, probably sufficient (I'd do 1.5 X RAM with anything over 1G RAM, but thats just me).  I used to use a separate /boot partition so that it could be unmounted after the system booted up (just an added precaution against a fubared system rendered unbootable by a stupid mistake), but I'm not sure if that would work with Ubuntu.  Since /boot remains mounted in Ubuntu, is there any advantage to having it separate?

---

### Post by cb34 on 2009-01-12
i did the boot partition for safety, and im running debian right now actually.

and i didn't make a bigger swp because i have never seen the swap being used more than maybe 25% under heavy load and doing lots of things. i dont feel the need for a bigger swp on my system so far.

and i set a seperate /var partition because there is alwayz log files and small files being written there, so keep it seperate from the root. and instead of a tmp partition, link all the small files it writes in /tmp to /var/tmp.. so the var partition is everything that changes all the time.

---

### Post by Montblanc_Kupo on 2009-01-12
This is something I've been trying to get a definitive answer to... and more importantly... some rationale behind the choices for putting each partition where and how big and what type (primary, logical, ... magical? hehe)

Ideally right now I want to have winxp for somethings I can't run in linux, ubuntu/kubuntu as a primary OS and possibly gentoo because I want to mess with it... or some other OS's.

I've seen a lot of conflicting information on how to set up drive partitions, and lots of them say "just do it this way.... trust me..."... but no reasoning WHY you put a /home or /boot or whatever... and where they are located on the drive.

Currently I have this setup but I'm sure it's not optimal:
180gb drive

* WinXP 90gb (already installed before I started messing with linux)
* unpartitioned space (I plan on adding more linux distros to play with)
* /boot partition (500mb)... saw some guides that talked about needing one... so I figured better safe than sorry.
* / partition with everything installed from ubuntu (about 50gb)
* /swap (1gb I believe) right at the end of the disk

The apcmag link that kansasnoob posted was one that I found which was actually very helpful for getting the basic concepts (had to learn about editing the GRUB... saved My *** on reinstalling windows when it died heh)... but other than that... it's hard to find any good solid information out there.

One of the things that I really dig about installing linux was (at least with ubuntu distros) it would import my user settings (pidgin, accounts, etc.) when I install from other distros and even windows... so the idea of having a home partition that you can keep through multiple installs sounds great... wish I'd known more about that before I installed the first time. Hopefully I can fix My drive up how it should be and not lose anything.

If anyone has information about optimal multi-boot installs and explanations for why each choice is made... that would be awesome. :)

---

### Post by kestrel1 on 2009-01-12
Slightly off post, but have you considered using virtual machines for different OS's.
I use Virtual Box to test other Linux distro's & it is very useful.

---

### Post by cb34 on 2009-01-12
VirtualBox is awesome! :guitar:

---

### Post by kestrel1 on 2009-01-12
Certainly is.
That way you could play around with drive configurations & not do any real harm.

---

### Post by HotShotDJ on 2009-01-12
> **Montblanc_Kupo said:**
> I've seen a lot of conflicting information on how to set up drive partitions, and lots of them say "just do it this way.... trust me..."... but no reasoning WHY you put a /home or /boot or whatever... and where they are located on the drive.Yes.  This can seem frustrating.  The thing is, Linux is used in so many different ways... single user, multi-user, server, desktop, PC, Laptop, etc... each with its own needs and different "optimal" configurations.  So, really, there is no single "best" way to set things up.  I'm a believer in keeping things as simple as possible for a given set up.  So, when somebody asks for a "best" set up for home use, I'm most comfortable giving them the answer I gave previously... /, swap, and /home with reasonable (yet not etched in stone) defaults of 10/RAMX2/Remainder.  If someone is tight on hard drive space, I might tweak those settings a bit.

---

### Post by HotShotDJ on 2009-01-12
> **kestrel1 said:**
> Slightly off post, but have you considered using virtual machines for different OS's.
I use Virtual Box to test other Linux distro's & it is very useful.Absolutely a great recommendation!  I use and recommend VirtualBox instead of dual-booting (unless you need 3D accelerated graphics for something like gaming... and even THAT is being worked on by the VB developers).

---

### Post by cb34 on 2009-01-12
> **HotShotDJ said:**
> Absolutely a great recommendation!  I use and recommend VirtualBox instead of dual-booting (unless you need 3D accelerated graphics for something like gaming... **_and even THAT is being worked on by the VB developers_**).ooooo aaaaa.. i cant wait!! :D that's great news!

---

### Post by kestrel1 on 2009-01-12
> **cb34 said:**
> ooooo aaaaa.. i cant wait!! :D that's great news!

I second that.

---

### Post by HotShotDJ on 2009-01-12
> **cb34 said:**
> ooooo aaaaa.. i cant wait!! :D that's great news!VirtualBox 2.1 already has experimental OpenGL support for Windows guests (doesn't work with other guests... yet).  See: [http://www.phoronix.com/scan.php?page=news_item&px=NjkzOA](http://www.phoronix.com/scan.php?page=news_item&px=NjkzOA)

---

### Post by ugm6hr on 2009-01-12
> **HotShotDJ said:**
> So, when somebody asks for a "best" set up for home use, I'm most comfortable giving them the answer I gave previously... /, swap, and /home with reasonable (yet not etched in stone) defaults of 10/RAMX2/Remainder.  If someone is tight on hard drive space, I might tweak those settings a bit.

This is a fair guide - and one I use too.

Although I never dedicate more than 1GB swap (irrespective of RAM), since I never use the Suspend / Hibernate options.

Additionally, there is apparently a theoretical speed increase at the end (i.e. centre) of a HD disk, so some people recommend having swap at the end of the HD (since swap needs to be fast).  I have no idea if it's true, but can't hurt to position it there.

---

### Post by HotShotDJ on 2009-01-12
> **ugm6hr said:**
> Additionally, there is apparently a theoretical speed increase at the end (i.e. centre) of a HD disk, so some people recommend having swap at the end of the HD (since swap needs to be fast).  I have no idea if it's true, but can't hurt to position it there.Yes.  This is actually true.  But for most systems, the speed difference is not noticeable.  In fact, if it IS noticeable, that means that your system is accessing swap too much, and you should buy more RAM.

You can also speed up swap by making sure that it does not span across platters.  But who wants to try to figure THAT one out for a speedup that you'd never even notice. :)

---

### Post by cb34 on 2009-01-12
i have no real clue if this is normal or not, but i put my swp near the beginning because i figure if any data needs to run through the swp partition, it should be close to the root and var dirs to keep everything fast.. i dont suspend or anything like that.. but i just made this up as i went along reading all over the place investigating so dont really know. but my system since last install and setup. is way faster.. or maybe it's because i'm using reiserfs for all my partitions that made the just in performance dont know. :) basically.. dont know anything. lol

---

### Post by Montblanc_Kupo on 2009-01-14
I've been dual booting because at first I hadn't messed with virtual box, but yeah, I do want to use 3D accel and see what the FULL speed of the OS really is, etc. I have the drive space to mess with having several installs so it's fine. I run winxp in virtualbox now and it's great. Saves Me having to reboot for everything but Adobe apps. Seamless mode is slick beyond belief heh (a little buggy, bust still great).

I hear what you're saying about "no best way"... I can see where you're coming from. I think it would be helpful if, as I was saying, there was an easily accessible guide that explained what each partition is for (ie, home does this, root does that, boot is for etc...) for new users to try to make informed choices about what each one is and how to partition. I'm by no means a "new computer user" or "not tech savvy"... but I am new to the black magic mystery world of linux's dark underbelly. ;) I sussed out what I was supposed to do through some googling and educated guesses, but actually *knowing* what each is for would be kinda nice. :)

---

### Post by HotShotDJ on 2009-01-14
> **Montblanc_Kupo said:**
> I think it would be helpful if, as I was saying, there was an easily accessible guide that explained what each partition is for (ie, home does this, root does that, boot is for etc...) for new users to try to make informed choices about what each one is and how to partition.Really, its not about what each partition is for, but what each directory is for. Once you know this, the partitioning options start making more sense.

In Unix-Like operating systems, such as Linux, all directories are attached to the root (/) directory.  Some examples are:
[LIST][*]/boot           for files required for the boot process
[*]/bin               for binary (executables),
[*]/dev               for device files,
[*]/etc               for system wide configuration files, 
[*]/tmp               for temporary files, and
[*]/home              for home directories of individual users 
[/LIST]

Check out [http://www.pathname.com/fhs/pub/fhs-2.3.html#BOOTSTATICFILESOFTHEBOOTLOADER](http://www.pathname.com/fhs/pub/fhs-2.3.html#BOOTSTATICFILESOFTHEBOOTLOADER) for more information (probably more than you wanted. :))

---

### Post by Montblanc_Kupo on 2009-01-14
Yeah, the problem is I run into confusing situations where there isn't much feedback or explaination... like:

I've seen lots of guides say to have a "/boot" partition all by it's onesies... so for lack of any reason not to, I partitioned that way. It appears that linux is more than happy to put it's file there and freak out if there isn't enough space... but it seems as though it's booting from the / (root) partition... when grub finds stage1... that's where it wants to look.

Now, I've been using computers for the last 30 years... and I've never really known the difference between primary, extended, logical, magical, imaginary, parochial, ceremonial, or any other type of partition type you can come up with (I realize this isn't a linux only thing, but still it seems to make a difference since other operating systems can't seem to deal with anything more than 1 partition anyway hehe). 

It's needlessly confusing IMHO.

Just to try to redirect My incoherent babbling heh, back to something useful (I appreciate all the info by the way)...

If I make a partition for /home... I should be able to attach that to ANY future install of linux much how I simply point it at the existing swap partition for each install and it says okay?

Is there any reason to have a separate /boot partition? Why would you want to do that or why not?

Any reason to put linux / windows / os x / whatever first second third whatever on the disc?

Where DO My socks go when I put them in the dryer?

If I have multiple partitions ... say a separate partition for /home... am I going to run into permissions errors if I have two separate partitions each with a different linux installed on it accessing that directory (ie, multi-booting but sharing a single /home)?

When I have multiple OS's... should those be primary, logical, extended... whatever kind of partition?

Ideally here is My setup:

primary os: my favorite flavor of linux (right now ubuntu)
necessity os for adobe: windowsxp
play space to install other os's to test: kubuntu, arch, gentoo, and fedora-core on the plate right now.

I have 1gb of ram... My experience has been that it never uses more than 100-200 mb of ram... although in retrospect I can see that it would need more to suspend the computer. I made a 1gb swap space not knowing any better... would this be the cause of the crashes on hibernate / suspend I've seen?

I'm sorry if I'm being dense, I've gotten a little bit of it figured out from what you guys have said before... but more information is always good.

I appreciate whatever anyone has to say... answer as much or as little as you like. hehe

Thanks in advance. :)

---

### Post by HotShotDJ on 2009-01-14
Let's handle the absolutely most profoundly important inquiry first:
> **Montblanc_Kupo said:**
> Where DO My socks go when I put them in the dryer?This mystery of mysteries is answered in the Revelation Of The Lost Prophetess Of AOL in the sacred writings of [The Invisible Pink Unicorn]("http://www.palmyria.co.uk/humour/ipu.htm") (May Her Holy Hooves Never Be Shod)> Also ye may know that ye have been especially blessed if you find that one of your socks has gone missing. Surely a sign from Her Horniness. If anyone questions why ye are missing a sock, simply reply "My Mistress had need of it." No one is certain what She does with the socks, but rejoice for ye were chosen to make this sacrifice.Now, moving on...
> **Montblanc_Kupo said:**
> 
If I make a partition for /home... I should be able to attach that to ANY future install of linux much how I simply point it at the existing swap partition for each install and it says okay?

Is there any reason to have a separate /boot partition? Why would you want to do that or why not?
Regarding /home... yes, you can attach it to any future install (I have done it many times).  BUT, be aware that you may run into permission problems.  However, it is very easy to fix by issuing a simple chmod command as root.  Occasionally you may need to delete/edit configuration files, but again, its pretty easy to correct these problems as they occur.

Do NOT, however, try to get several different installations to use the same /home partition.  This can cause all kinds of problems -- especially with permissions.  If you are going to be running 2 or 3 different installations of Linux on the same machine, each will need its own /home.  You can share documents between them, perhaps by creating a partition that you could mount at /home/shared (or some such place).

As far as a separate /boot partition, this can be done as a security measure.  Some Unix/Linux systems mount /boot as read-only just for the booting process, and then once the kernel is loaded and the system has properly booted, it unmounts it. However, since Ubuntu does not unmount it after booting, I don't see much point in doing it.  Others disagree with me, and you should consider their opinions as well.
> **Montblanc_Kupo said:**
> 
Any reason to put linux / windows / os x / whatever first second third whatever on the disc?Windows likes to be on the first primary partition of the first disk listed in your BIOS... in Linux terms, on /dev/hda1 or /dev/sda1.  I don't know if it still holds true with Vista, but it certainly was with 2000, and I'm pretty sure with XP.  The SWAP partition for Linux is best put on a primary partition. (EDIT: This statement may be in error based on newer information.  The information I can find suggests that either a primary or extended/logical partition is fine for your swap partition.)  Beyond that, place things where ever it is convenient for you.  Some have suggested that you can speed things up by making sure that certain partitions are at the end of the physical disk.  While I'm sure there is some truth to that idea (laws of physics make it at least plausible), there are so many other variables that it is unlikely to make much of a difference in all but a very few rare cases.

---

### Post by ugm6hr on 2009-01-14
> **HotShotDJ said:**
> The SWAP partition for Linux is best put on a primary partition.

Really? Why?

The reason I ask, is that the Ubuntu "Guided" installation, even if using the entire disk, actually deliberately puts it in a Logical partition.

i.e.
sda1 = /
sda5 = swap

If there is a benefit in putting swap in a Primary, this seems nonsensical on Ubuntu's part.

---

### Post by HotShotDJ on 2009-01-14
> **ugm6hr said:**
> If there is a benefit in putting swap in a Primary, this seems nonsensical on Ubuntu's part.I recall years ago having read that a primary partition in best for swap... and I remember that the logic seemed sensible to me.  Since I can't remember the source of this information, I started searching.  Everything I can find says that it doesn't matter.  Since I can't back up that statement with anything but my (admittedly aging) memory, I'll have to retract my original answer.

---

### Post by cyan on 2009-01-19
> Do NOT, however, try to get several different installations to use the same /home partition. This can cause all kinds of problems -- especially with permissions. If you are going to be running 2 or 3 different installations of Linux on the same machine, each will need its own /home. You can share documents between them, perhaps by creating a partition that you could mount at /home/shared (or some such place).

I thought one of the main advantages of moving /home to its own partition was because it allowed you to install separate distros (perhaps one stable and one bleeding edges) and still access your files and settings.  By modifying fstab to point to the same /home for multiple installs, is that a bad thing?

---

### Post by Andreas1 on 2009-02-13
> **ugm6hr said:**
> Additionally, there is apparently a theoretical speed increase at the end (i.e. centre) of a HD disk, so some people recommend having swap at the end of the HD (since swap needs to be fast).  I have no idea if it's true, but can't hurt to position it there.

um, isn't it the other way around for modern disks, since they have more sectors in the outer tracks?
[http://tldp.org/HOWTO/Partition/requirements.html#SwapSize]("http://tldp.org/HOWTO/Partition/requirements.html#SwapSize") (see "where should i put my swap")
i also read that it would be intelligent to place swap in the middle (edit: not geographically in the center, but virtually, amidst other partitions) of the disk or near other busy areas anyway to decrease average travel distance for the heads, which is more important than being on the fastest tracks.
that being said, i basically have no idea of those things and i might be wrong as well, researching that topic brought forth an amazing spectrum of incompatible and contradictory views, all of them presented with the certainty of an expert.:)

---

