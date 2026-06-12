---
title: "[SOLVED] New Guy with filesystem troubles in 8.04"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by aer0usa on 2009-01-10
Hi.
It's my first time, please be gentle. :)
A little about me: I used to be a Mac-head back when System 7 was a big deal. Then, I reluctantly started using Windoze when I got a 'real' job as a . More recently, PortableApps for Windoze got me interested in Open Source software, and so I'm giving Ubuntu a try.
I got a used IBM NetVista M42 and a 40GB drive rescued from a cast-off DVR. I've installed Hardy Heron from the DVD in "The Official Ubuntu Book", 3rd edition.
I created a "Desktop User" profile for when I'm just using Ubuntu and not administering.
Mostly, this seems to be working OK, until I tried ripping some music to the hard drive with Sound Juicer in my desktop user profile. Some music ripped OK, but some ripped very slowly, and eventually gave me an alert box saying something like it couldn't create the file stream. Sorry I didn't write down the exact message.
I restarted the computer, and it wouldn't start Ubuntu. After Grub, I eventually got a blank black screen, and nothing else. I restarted again, and used the Grub menu to start in Recovery Mode. Recovery Mode claimed to find a problem with the filesystem, and then claimed to fix it, and I was able to start Ubuntu then.
However, the problem with the failure to start has recurred several times since then, and the Recovery Mode claims to find and fix the same problem each time. Something about an 'inode' having a zero 'dtime'.
I also rebooted from the Live DVD and ran a check on the hard drive using gparted, which claimed the hard drive was OK.
In addition, the desktop user has been acting strange, giving me empty alert boxes, and not able to pull up Help.
Overnight, I let Update Manager update everything that it wanted to. But this morning, I was welcomed by the blank black screen again.
So, I'm not sure what to do.
*Do I have a bad hard drive?
*Should I delete the desktop user I created and make a new one?
*Is ripping music to the hard drive the problem, or did it just bring a problem to light?
Sorry about writing a whole novel here, but I don't yet know what I don't know. I'm not sure what other information is needed to fix this problem, so please let me know what else is needed.
I don't have a lot of personal stuff on the new computer yet, so I could just wipe the drive and start again if that's the best solution, but I thought I would ask if there's another way.
Thanks a LOT in advance!!
Eric

---

### Post by Catalyst2Death on 2009-01-10
So, it looks like you may want to reinstall:
[http://ubuntuforums.org/showthread.php?t=121005](http://ubuntuforums.org/showthread.php?t=121005)

also check:
[http://linuxmafia.com/faq/VALinux-kb/deleted-inode-has-zero-dtime.html](http://linuxmafia.com/faq/VALinux-kb/deleted-inode-has-zero-dtime.html)

If these aren't your errors, then we need more information.  I'm not sure what you mean by a desktop user... You should just be able have a normal user account with sudoer privileges and a strong password.  Ubuntu doesn't let you have access to the root account which is the super-user system administrator.  You access root priveleges by running as a super-user using ```
sudo <my admin command>
```
I don't think ripping music caused this problem, but it may be a result of the problem.  I'm not sure what could have caused the low performance ripping the cds.  Are they scratched?  In either case, wiping it may be the best way to fix it.  Make sure that your install DVD was burned cleanly and doesn't have any errors. (there's an option when you boot to the DVD to check for errors)

---

### Post by aer0usa on 2009-01-10
Thanks C2D. Cleaning the CD? Huh, worth a shot!
I understand that the default user account is different from root. I was under the impression (and I can't really recall where I got this impression) that for your ordinary day-to-day use of the system, you should use a user account without admin privileges, what I called a "desktop user". Don't recall where I got that term either. Like I said, I'm a new guy, and have quite a bit to learn about Linux.
I'll consider reinstalling. Seems like there ought to be another way to fix the filesystem, though. Especially if it's so easy to break!
Thanks!

---

### Post by Zill on 2009-01-10
I initially used the ext3 filesystem for my first Linux installations.  After I had a few crashes with it, unsuccessfully trying to fix the various cryptic "inode" error messages, I gave up and used reiserfs instead.

Since then, I have found the reiserfs filesystem to be very robust on all my PCs and it has not given me any problems at all.  No inode messages and no "lost and found" directories full of unrecoverable files. ;-)

If you do decide to reinstall then you could do worse than give reiserfs a try - you may quite like it. :-)

---

### Post by Kellemora on 2009-01-10
Hi aer0

Welcome to the wonderful world of Ubuntu!

I cut my teeth on Apple, LISA and MAC, used WANG for commercial reasons then got roped into the PC world for decades.

I only started using Ubuntu about 3 months ago!
For this OLDSTER it was a whole new ballgame with lot's to learn.
Nonetheless, within only a month I felt confident enough to convert my entire office over to Ubuntu.  I guess I should note that I looked into and tried CentOS (RedHatClone) and Debian also.  But Ubuntu climbed to #1 in record time because of the support and quality of the distro.  Each year it moves ahead further than Windows could in a decade.  So the gap is closing very rapidly.  Were just waiting for hardware manufacturers to wake up and see the light!  Then the Doze will have a run for their money, hi hi.........

You didn't mention which version of Ubuntu you have installed.
The latest Stable version of Ubuntu is known as Hardy Heron, version 8.04 LTS (the LTS stands for Long Term Support!), Hardy will be supported long after 8:10 intrepid is in the grave.

Although some call 8:10 stable, it's still experimental.  I think we get to download it, in order to work out the bugs and once the bugs are out, it may be re-released as 9.04 LTS a truly stable version.  Not sure if this is how it works, but it sounds logical anyhow.

My point only being, if you are using Intrepid 8:10, and you plan on reinstalling, you may want to consider 8.04 which seems to work rather well.  8.10 seems to be for those who love headaches and want the latest and greatest to play around with.
Although few will agree with me I'm sure, hi hi.......

Also, if you reinstall, you will probably want to consider keeping your /home directory on it's OWN Partition.  That way you can install and mess around with the distro all you want without loosing your settings and having to reload all of your user data each time.

Since you like to rip music, (although I'm talking through my hat here, not knowing about doing such things, although I handle monstrous file size images daily from DVDs), you may want to set aside a separate partition just to handle the files you are reading or writing to CD's, DVD's, etc.  We do this with large images that are often larger than a single CD can even hold!  They download and load for processing so much faster, and when we finish our work to them, the creation of user usable size files from the master also runs a whole lot faster.  Then when we rewrite the completed image back to a CD or DVD it usually runs without a hitch.  Whereas when we were just using a folder within the /home directory for this, it was much slower and quite often an image would become corrupt, not in the file but on the CD or DVD.  We assume it was due to a lag time while writing as the computer performs many operations while writing to a CD or DVD besides just the burning operation.  By image I meant a photographic type image, not a machine code image!  One of our jobs here is restoring old photographs manually, but using computers, just not in automatic mode, hi hi........  At 1 to 1 an image might be the size of the side of a barn, just so we can work at film grain level to produce a flawless reproduction that could be printed at 12x18 with no pixelation of any kind present in the printed image.  Also there are other projects that require such magnification as well that you normally cannot achieve digitally.  But if I said, even though an image is converted to digital, if it's from quality film, often it's possible to read the name on the wristwatch someone is wearing in a crowd of 100 people in the image.
I think music and video CD's and DVD's fall darn near into this same class of image size by comparison.

There are many different programs you can use in Ubuntu, some are better than others, but harder to use or get used to.  There WILL be a learning curve to get used to how things work in Ubuntu.  It's slightly different than many other Linux disto's!  I will say, different in a better way, since I've tried others.

I may not be able to solve your problem, but as you see, there are hundreds of guru's here ready and willing to help out, and FAST TOO.

One last suggestion.
Use something more appropriate in the Title of your post, so that the guru with the knowledge of the problem will spot it faster.  OH, sorry, I see you are using 8.04, missed that!
But since it seems your primary problem is burning a DVD, perhaps you should include that in a Title and keep separate questions separate.  I think they will get answered faster by someone (not like myself) who KNOWS what they are talking about.

Again, Welcome!

TTUL
Gary

---

### Post by aer0usa on 2009-01-10
Zill,
Thanks, yes ext3 blew chow on me again, so I re-formatted and re-installed with reiserfs. I'll give it a shot. Thanks!

ext3 seems a little 'fragile' for what is supposed to be a robust OS. Easy to break, hard to fix. I may be wrong about that, but that's my impression so far.

---

### Post by aer0usa on 2009-01-10
Hey Gary, thanks for your reply.

Umm, actually my subject line outlines my problems pretty well:
1. I'm having filesystem trouble
2. I'm a new guy (probably the bigger of the two problems)

I'm not trying to burn a DVD. No worries, though, I gave you a lot to wade through. :)

As I just mentioned to Zill, I have just re-formatted and re-installed. I wish I had seen your reply first, though, since I hadn't thought to put my /home directory on a separate partition. That makes a lot of sense. I'm still in the experimental phase, though. I'll probably by wiping the disk and re-installing again before I'm through, so I'll take that advice then. Except, how do I tell it which partition to put the /home directory on? Is that the 'mount point' field in the partition editor?

That's interesting work you're doing, and using Ubuntu to do it is that much more impressive! After only three months experience with it? I agree, though, that the best way to learn something is to dive in to the deep end. 

Thanks again for the reply, see you around the forums!!
Eric

---

### Post by handydan918 on 2009-01-11
> **aer0usa said:**
> Zill,
Thanks, yes ext3 blew chow on me again, so I re-formatted and re-installed with reiserfs. I'll give it a shot. Thanks!

ext3 seems a little 'fragile' for what is supposed to be a robust OS. Easy to break, hard to fix. I may be wrong about that, but that's my impression so far.

Having used ext3 for the best part of a decade, I suspect that what you are experiencing as "too fragile" is 8.10. I would recommend sicking with the LTS releases. They are the only one that even approach "stable", in the Debian sense of the word.

---

### Post by blackened on 2009-01-11
> **aer0usa said:**
> ...As I just mentioned to Zill, I have just re-formatted and re-installed. I wish I had seen your reply first, though, since I hadn't thought to put my /home directory on a separate partition. That makes a lot of sense. I'm still in the experimental phase, though. I'll probably by wiping the disk and re-installing again before I'm through, so I'll take that advice then. Except, how do I tell it which partition to put the /home directory on? Is that the 'mount point' field in the partition editor?...

During installation, you'll come to the point where the partition manager starts (as you've dealt with when you used reiser instead of ext3), if you choose to manually set up the partition table, you first set the partition for /, then optionally for swap, then if you create a third partition it will usually (IIRC) automatically fill in the mountpoint as /home. If it doesn't, then you can just manually set the mountpoint.

This method is tremendously beneficial if you make a habit of breaking things that necessitate a clean install of the root filesystem.

Also, where windows has administrators and normal users, we often refer to those distinctions as root, superuser, and regular user. Root is an explicitly specified account (which is disabled by default in Ubuntu, for good reason), where superuser has all the powers of root, but is only used (via preceding commands with *sudo*) on a temporary basis to make changes to system files (software installation etc.), and regular or normal user is just that: only able to make changes to files that are owned by him/her (typically those in their /home/*username* directory) or belong to a group that s/he belongs to.

Glad to see you're getting around well and enjoying yourself.

---

### Post by Zill on 2009-01-11
> **handydan918 said:**
> Having used ext3 for the best part of a decade, I suspect that what you are experiencing as "too fragile" is 8.10. I would recommend sicking with the LTS releases. They are the only one that even approach "stable", in the Debian sense of the word.

I must agree with the OP that ext3 *does* seem to be "fragile".  My early experience with ext3 on Mandrake and then Ubuntu was punctuated by various filesystem corruption problems.  It can be quite daunting for a newbie to see messages "about an 'inode' having a zero 'dtime'."  While it may be possible for a Linux "guru" to fix these problems, it isn't easy for a newbie!

I also doubt if such errors are related to the OS version.  I think it is far more likely that they are attributable to the filesystem.

Nevertheless, I certainly agree that it is best to use LTS releases - I am still running Dapper for a little while longer. ;-)

---

### Post by handydan918 on 2009-01-11
> **Zill said:**
> I must agree with the OP that ext3 *does* seem to be "fragile".  My early experience with ext3 on Mandrake and then Ubuntu was punctuated by various filesystem corruption problems.  It can be quite daunting for a newbie to see messages "about an 'inode' having a zero 'dtime'."  While it may be possible for a Linux "guru" to fix these problems, it isn't easy for a newbie!

I also doubt if such errors are related to the OS version.  I think it is far more likely that they are attributable to the filesystem.

Nevertheless, I certainly agree that it is best to use LTS releases - I am still running Dapper for a little while longer. ;-)
I guess this is one of the points where personal experience is radically different. I have used Ubu very little in comparison to everything else, and NEVER suffered any issue with ext3. C'est la guerre...

---

### Post by Zill on 2009-01-11
handydan918:  Maybe ext3 has become more robust since I last used it. :-)

Anyway, I'm glad it works for you and, presumably, many others as it shows that freedom of choice is one of the best features of GNU/Linux.  We can choose what works best for each of us, freeing us from the rigid tyranny of other, closed source, operating systems. ;-)

---

### Post by Kellemora on 2009-01-11
Hi Eric

WHEN you are partitioning your hard drives, that is when you name the partition for it's particular use, such as swap or /home or / etc.

It's much easier to start out with /home on a separate partition, than to move /home later.  Since /home is where you store everything except some system things, it should be your biggest partition.  I usually set up my system partitions first THEN use ALL THE REST of the Space left on the HD and partition that for /home

And being a Noob myself, there are some things I haven't delved into trying to figure out yet.  Since work takes precidence over pleasure, most of my time has been spent making sure the my income end stays stable, hi hi...........
I'm also and olde geezer who often gets tangled up with these confounded computin' contraptions, hi hi........

I used to do my calculations on a MANUAL hand cranked FRIDEN MACHINE and/or on a Log/Log/Duplex/Decitrig Slide Rule!
And a LOT of times, it was FASTER than one of these computin' contraptions when they are acting up!

TTUL
Gary

---

### Post by aer0usa on 2009-01-11
Hi everyone,

Thanks again to all of you for your replies.

Somehow, the notion that I'm using 8.10 has crept into this thread. I'm using 8.04. I HAD been wondering, however, whether it might be beneficial to try to upgrade to 8.10, so the input about 8.10 has helped me.

After switching to reiserfs, wouldn't you know it, it started acting up again. This time, fsck told me that there are bad blocks on my hard drive. That may very well be the real source of my problems. 

I also started getting GRUB Error 18. I looked that one up and what I found seems to say that the content the hard drive is trying to read can't be read, often because the hard drive is larger than the BIOS can address and the content is beyond the BIOS' range, or something like that. Since the hard drive HAD worked OK for a while, and then stopped, I'm guessing that I'm looking at a drive that's at the end of its useful life.

I had another HD sitting around. I had already installed 8.04 on it w/ext3, so I'm giving it a try. This hard drive is only half the size of the first one I tried (20GB vs 40GB), but if it works, that'll be OK.

I think I'll mark this thread 'solved' because I think I was dealing with a hardware issue rather than a software issue. I've learned a lot here, though. Thanks!

I still feel that I'm in the experimental phase, and may yet do another clean install. If/when I do that, how large should the / partition be? Will it tell me? Will it be large enough for me to add more software later?

Thanks again to all of you, a good online community makes learning a lot easier and more enjoyable!

Eric

---

### Post by Zill on 2009-01-11
aer0usa:  As fsck is reporting bad blocks it does look like your drive is dying so it should be replaced asap. :-(

As has already been suggested, stick to LTS releases if you want rock-solid reliability.  Have your /home on a separate partition to make it easy to re-install or upgrade the OS when necessary.  Although "personal" config files are kept in /home, "system" config files are in /etc so I also keep copies of these for reference when upgrading.

Regarding the / partition, I find 10GB to be quite adequate but you could always increase this if you intend to install every app available!

Good luck.

---

