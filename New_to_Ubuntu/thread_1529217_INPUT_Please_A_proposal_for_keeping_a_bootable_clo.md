---
title: "INPUT Please: A proposal for keeping a bootable clone"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by NTL2009 on 2010-07-11
I come from Mac OS9/OSX land, where making a bootable clone is a very simple and useful process (I used the SuperDuper! app for this). I (think I) have come to understand that the boot process is just different on Linux, so the approach must be different.

I've tried to review the different cloning options out there, I'm sure I have missed something, but they all seem to have limitations/issues for me. Like needing to restore back to the same drive (I want to just boot the clone and get to work if I need to), or requiring that the target drive partition is as large as the source drive, regardless of how full the source is, or editing of boot parameters afterwards, etc.

**So, my proposal:**

1) Create a fresh install on a removable USB HDD - this will be the 'target'. You would probably need to match the way your source was partitioned - that is, if home and root are separate partitions, then create seperate partitions on your target - I am not sure of this. Your target needs to be big enough to accommodate the 'used' size of the source, with a little wiggle room, but can be smaller or larger than the full source partition.

2) Assure that this install is bootable on your system, even if your 'source' HDD is dead/removed. 

3) Then use some tool (grsync?), to sync the target to get it to match your source. As I understand, some files do not need to be copied (so these should be skipped for speed/efficiency), and some files related to booting you DO NOT copy over - the target needs to maintain its own copies of these to boot properly.

Once synced, this clone should be able to be booted on another compatible hardware system, which can be a 'life-saver' in case of a hardware problem. 

So, does this sound reasonable, or has this wheel already been invented and I missed it? If not invented, can anyone help with a list of files to "optionally skip copy", and files to "must not copy"?

As an aside, I'm currently having some issues with steps 1&2 - I have a fresh install bootable on one machine, but I can't seem to move it to another and boot there. That thread is located[COLOR=RoyalBlue] [here]("http://ubuntuforums.org/showthread.php?p=9576650#post9576650"),[/COLOR] if interested. Hopefully, that issue gets resolved soon, I think it is a separate issue from this basic concept.

So I'd appreciate any feedback and/or support on this. If it is worthwhile and 'do-able' I'd be up to documenting the process for submission to the Ubuntu Community docs, or wherever makes sense. I prefer to use basic, time-tested tools (I think grsync qualifies?) for something so important.

Oh, and I did put this in the 'Beginners' thread, as it is my feeling that having a clean, bootable clone is one of the best things a beginner can do to build confidence in using a system. It has saved me a couple times in the Mac world - it is really a stress-reliever to be able to pull out a clone, boot it (on other HW if a HW problem) and just start working again until you can find time/money to troubleshoot/fix/replace a broken system.

-NTL2009

---

### Post by marshmallow1304 on 2010-07-12
[Remastersys]("http://www.geekconnection.org/remastersys/") can do that.  It creates a LiveCD in one of two ways:
a) a distributable copy with system files only
b) a full copy that includes personal files

You could do b then write the iso to a DVD or USB drive (size permitting).  Boot from it, install, and you're set.




Or you can just make a backup of your /home (using rsync or similar), do a fresh install, and copy back.  Then just [reinstall your packages]("http://www.ubuntugeek.com/clone-your-ubuntu-installation.html").

---

### Post by bodhi.zazen on 2010-07-12
I always use partimage for this task, although you can also use gparted.

The only issues you may have after restring a clone would be:

1. Configure the MBR. If you know how to restroe grub from a live CD this is easy.

2. Depending on where you place the clone when you restore it you may need to edit /etc/fstab .

---

### Post by john newbuntu on 2010-07-12
If you are familiar with the CLI, the tar command when run with the right options will compress your entire filesystem/s and restore it on any partition.  The only additional things that need to be taken care of are to reinstall grub/bootloader, regenerate UUIDs and update fstab if necessary.  The usual caveats apply - free space on partition >= size of original data and hardware compatibility.

remastersys can also do a backup and use it as an installable liveCD.

clonezilla and "dd" commands could also be used although these have some of the limitations you mentioned.

---

### Post by NTL2009 on 2010-07-12
Thanks for the replies. Now, if I understand them correctly, these suggestions _will_ get me backed up ( I was aware of most of these approaches from my research), but none of them meets my specifications - so it sounds like maybe I am not 're-inventing the wheel'?

To summarize, I want to be able to clone to an external drive, and be able to re-boot that and just use it. With the option of booting and using it on another computer in the case where my HW dies. No 'configuring the MBR, or restoring grub, or editing /etc/fstab, or  reinstalling packages' from one drive to another, and no requirement that the drive sizes match (assuming of course that I have enough drive space to hold the files used). If a failure occurs, one should be able to get up and running as fast as possible, and deal with the failure later.

So, unless I misinterpreted the proposals, it sounds like I'll need to 'invent' something. IMO, the Linux community really needs something like this, so us newbies can easily create a bootable clone of our systems right after we get them reasonably configured. It's a great 'safety-net'.  For most of us, that stage happens before we have time to learn about the entire boot process. That is rather intimidating. Yes, it can be learned, and I'm taking those steps now, but it should not be a requirement to get a bootable clone.

So, is my approach sound? Summary from OP:

1) Create a fresh install on a removable USB HDD - this will be the  'target'. It can be smaller or larger than the  full source partition.

2) Assure that this install is bootable on your system, even if your  'source' HDD is dead/removed. 

3) Then use some tool (grsync?), to sync the target to get it to match  your source. 

For #3, it sounds like I'd need some script in the tool to tell it what to skip, so as not to copy un-needed files, and not to write over the files that make that installation bootable on that drive. The initial install should provide all the 'boot-ability' function.

Am I off-base? I understand that these requirements I've outlined may not be the requirements that any of you see as needed. But IMO, that is because you are experienced and knowledgeable and comfortable with the tweaks and limitations of the other processes. But I truly believe that it would help people new to Linux, and would make life easier for many others. Can anyone help me determine the best tools and the file list? Maybe this should move to another area if it truly going to be a development process?

There was a time when car owners knew how to pull the spark plugs, place a 1/2 teaspoon of gasoline in each cylinder and retard the spark timing before they cranked the engine by hand. Some of these people scoffed at electric starters and chokes. All this 'edit, install, re-install' talk reminds me of those 'hand crank' days - fine for some, but most of us appreciate advanced, automated methods. Thanks.

-NTL2009

---

### Post by C.S.Cameron on 2010-07-12
```
dd if=/dev/sda of=/dev/sdb
```

Will make a bootable clone of device sda on device sdb.
All partitions on sda will be copied to sdb.
sdb must be as large or larger than sda.

---

### Post by bodhi.zazen on 2010-07-12
> **NTL2009 said:**
> So, unless I misinterpreted the proposals, it sounds like I'll need to 'invent' something.

Where did you get the idea you would need to "invent" something ? You were given several options, some command line, some graphical.

Remastersys is graphical and about as straight forward as it gets.

You do not need to "invent" anything, you need to evaluate the available tools and learn a few things about how Linux works, mainly grub2 and fstab.

You have several options that were not listed previously :

1. Gparted.

2. Clonzilla.

[http://clonezilla.org/](http://clonezilla.org/)

[http://clonezilla-sysresccd.hellug.gr/](http://clonezilla-sysresccd.hellug.gr/)

You would do best to check your "attitude" and preconceived notions at the door, they will not help you much.

---

### Post by john newbuntu on 2010-07-12
Lets assume for a moment that all these other ideas are complicated.
> **NTL2009 said:**
> 
So, is my approach sound? Summary from OP:

1) Create a fresh install on a removable USB HDD - this will be the  'target'. It can be smaller or larger than the  full source partition.

2) Assure that this install is bootable on your system, even if your  'source' HDD is dead/removed. 

3) Then use some tool (grsync?), to sync the target to get it to match  your source. 


1) looks good until the source partition starts getting bigger than target.
2) Certainly doable - may require tweaks (BIOS changes etc)
3) rsync or a gazillion other sync utilities will work provided as you mentioned you exclude a whole bunch of files like fstab, grub.cfg, block/character files, mounts and such.

Issue: In the event of a new grub uprade, how are you going to perform an MBR update and a DOS compatibiltiy region update if required.  These are outside your partitions/filesystems.  rsync has no control of it.  You could use dd or 'grub-install', which involves 'hand cranking' in your terms or do you want grub to stay out of sync from a bootloader perspective?

You could use raid1 on your system and replace it whenever one goes bad.  But that involves at least an extra drive and some work.

Keeping all these in mind, it sounds more complicated than what others have suggested.  I have used a slightly modified version of what CSCameron suggested at least a dozen times successfully.  I have also used Clonezilla to back up and restore both WinXP and Karmic successfully.  Yes they need some minimal tweaking but not anything at expert level.

---

### Post by QLee on 2010-07-12
[QUOTE=NTL2009]...
So, unless I misinterpreted the proposals, it sounds like I'll need to 'invent' something. IMO, the Linux community really needs something like this,... [/QUOTE]

Don't think that the experience you've had so far with Ubuntu is all of GNU/Linux. Of the tens of thousands of programs in Debian, Ubuntu developers have chosen some of the best and ones that will fit on a single install CD, with some more available in the repository for download after install. Your default install doesn't have everything. An example: When I install Debian I download the first 3 CDs (there are 31, including the ones that have the source files) to load the programs I want.

There are backup and recovery systems in "Linux" in addition to what's already been mentioned, mondo, backintime, to name just a couple.

Most of the time, people who are actually going to be able to successfully backup and restore are going to be able to do it with a live CD and their backup.

That said, nothing wrong with you crafting a personal solution, it's a good way to learn.

[QUOTE=NTL2009]Maybe this should move to another area if it truly going to be a development process?[/Quote]

Well, I wouldn't try to to what you are proposing in the A B Forum, but it's your choice, it could turn out to be a learning experience too.

[QUOTE=NTL2009]There was a time when car owners knew how to pull the spark plugs, place a 1/2 teaspoon of gasoline in each cylinder and retard the spark timing before they cranked the engine by hand. Some of these people scoffed at electric starters and chokes. All this 'edit, install, re-install' talk reminds me of those 'hand crank' days - fine for some, but most of us appreciate advanced, automated methods. Thanks.[/QUOTE]

Yup, most of the greasy handed GNU/Linux Geeks, have noticed that most newcomers are looking for a GUI way of doing things. However, in the other thread, you seem to want to learn how to retard or advance the spark.

---

### Post by NTL2009 on 2010-07-12
> **bodhi.zazen said:**
> Where did you get the idea you would need to "invent" something ? 

You would do best to check your "attitude" and preconceived notions at the door, they will not help you much.

Sorry if what I'm saying comes across as 'attitude' - I'm new to Linux, I'm looking for solutions that work as well or better than some I have used in the past on my previous systems. That seems natural, no?  Seems to me if they exist in 'that world', they could/should exist in the Linux world. And if they don't exist, perhaps I can have a hand in bringing them to life - I think that is the one of the underlying concepts of open source software, no?

And some of the responses I'm getting, though I'm sure are intended to be helpful, are making suggestions that are outside of the requirements I laid out. I know for example, that 'dd' will require an equal or larger partition. I'm looking for something w/o that restriction. Good info for reference, but it is not within my stated goals.

This is what leads me to thinking that I need to 'invent' something (maybe just a documented process with existing tools) to do what I hope to be able to do.

> **john newbuntu said:**
> Lets assume for a moment that all these other ideas are complicated.

1) looks good until the source partition starts getting bigger than target. 

Granted, we can't expect miracles (and I'd prefer not to compress for this approach - KISS is my motto for backups. I can live with that.

> 2) Certainly doable - may require tweaks (BIOS changes etc)Well, I'm trying to learn the ins/outs on that other thread. Hopefully this is simple in most cases, and I just have an anomaly with that PC901 setup.

> 3) rsync or a gazillion other sync utilities will work provided as you mentioned you exclude a whole bunch of files like fstab, grub.cfg, block/character files, mounts and such.Yes, this is what I am thinking - and if this is a reasonable approach, this is where I'd like to get some assistance from those with experience - exactly which files (maybe the whole boot directory?) should be skipped - if that is even the right question, I'm still too new to know.

> Issue: In the event of a new grub upgrade, how are you going to perform an MBR update and a DOS compatibiltiy region update if required.  These are outside your partitions/filesystems.  rsync has no control of it. ... or do you want grub to stay out of sync from a bootloader perspective?This is where my lack of knowledge is getting in the way. I don't know enough to know what I want to do, but I'll try to learn. 
  
So perhaps I'm being too simplistic, but if I have an install that boots, why would I want to change anything in the MBR or GRUB?

Hmmm, OK (and I'm on the edge of my understanding here....) I guess if there is a kernal update, that would need updates to GRUB so that it knows to present it in the menu? So maybe certain updates would just need to be done while booted in that cloned install?

> Keeping all these in mind, it sounds more complicated than what others have suggested. ....  Yes they need some minimal tweaking but not anything at expert level.Perhaps, but it does seem to provide something that these others don't - the ability to up & running after a problem with nothing more than plug in a drive, reboot, and select your external drive. And the installer is very easy for us newbies (watch that "Advanced" tab! ;)), and I think grsync looks pretty easy, and might be easily adapted to this with a simple script? So from a newbie perspective at least, it seem fairly simple. But again, my lack of knowledge might be distorting this.

While those tweaks may not seem 'expert level' to you - they have newbie heads spinning!

Thanks to all for the help & suggestions - NTL2009

---

### Post by NTL2009 on 2010-07-12
> **QLee said:**
> Don't think that the experience you've had so far with Ubuntu is all of GNU/Linux.

Absolutely! I know I've barely scratched the surface. That is why I posted this as 'looking for input' - nothing would make me happier than for someone to come along and say ' hey stupid, xxyyzz does exactly what you are asking for'! ;) So far, they don't seem to though.

> That said, nothing wrong with you crafting a personal solution, it's a good way to learn.

Yup, most of the greasy handed GNU/Linux Geeks, have noticed that most newcomers are looking for a GUI way of doing things. However, in the other thread, you seem to want to learn how to retard or advance the spark.

Well, I actually don't want to learn those nitty-gritty details, at least not now. But, if I need to learn them to get an install to reliably boot on my two computers here, then I will do what I must do. The alternative seems to be to decide that Linux is not ready for me yet, but I've seen far too much that I like about it to come to that conclusion w/o a fight. 

Heh-heh - what I really want to get to is booting this on the Intel MacBooks I have in our family - but those are EFI, and I'm just not ready to go there yet ;)

-NTL2009

---

### Post by QLee on 2010-07-12
[QUOTE=NTL2009]Absolutely! I know I've barely scratched the surface. That is why I posted this as 'looking for input' - nothing would make me happier than for someone to come along and say ' hey stupid, xxyyzz does exactly what you are asking for'! ;) So far, they don't seem to though.
[/QUOTE]

Well, yes, I've certainly seen that approach, Debian newsgroups come to mind. However, that approach is not encouraged here and is even a violation of the code of conduct for the forum.

[example]Hey, stupid, mondo does exactly what you are asking for. [/example]

Now I risk getting censured or banned. 

There are also commercial Linux backup solutions, cuz a enterprise can pay. Here in the free (as in free beer) OS world we get stuff for free and maybe it has to be assembled first before it does everything we want it to do. However, there are people who do the stuff for pay and often a company will hire one of them to craft a specific solution. But most just want "free" and sophistication at the same time. You're even different from most users who only want to push one button on their USB drive and have the backup done.

[Edit] Just so you know I used the example of mondo but I don't know if it has been upgraded to handle ext4 yet. If not it likely will be eventually.

---

### Post by NTL2009 on 2010-07-12
> **QLee said:**
> However, that approach is not encouraged here and is even a violation of the code of conduct for the forum.

Yes, I didn't mean that literally - it was a sort of self-deprecating humor aimed at myself and my current lack of knowledge (different from being stupid), probably bad form on my part - sorry.  I agree, no one should be calling anyone else anything that is disrespectful in any way in this forum. 

> But most just want "free" and sophistication at the same time.Sure, but if you think about it, there is (an unintended) paradox of sorts going on here. Most of what I see in Ubuntu is quite 'polished' and sophisticated. That is what drew me to it. In fact, I was shocked at how good it was - I was expecting something like Windows 2.0 ;) . OSX is normally held up as the 'gold standard' for UI, yet there are many places it falls flat on its face, and (IMO - this is somewhat subjective), Ubuntu surpasses it. The Ubuntu implementation of "Workspace Switcher" (though flawed when enabling Compiz), is heads and shoulders above OSX "Spaces" (which I was excited about until I tried to use it - it was more trouble than it was worth - too inflexible).

So when I see so much polish and sophistication in Ubuntu, often exceeding my OSX experience, I'm led to think there must also be easy ways to clone a bootable install (since I am used to doing that in OSX). If they aren't obvious, I'm at least going to ask to see if I'm just missing something (often the case). And if they don't exist, perhaps I can help create them, I really do believe newbies (I'm not sure if there is a better 'accepted' term for us?) would benefit from this. And I am willing to help. That is how new software gets developed, right? I'm not really a coder, but I do have certain abilities in terms of seeing needs, defining solutions (at the user level) and documenting them. Maybe I can contribute in that way. I know that many coders see documentation as an unplesant task, but I don't mind so much. And they aren't always the best to do it, as they have too much understanding to explain it to others. But I do need to get the basics to be able to translate it.

I also think that many times, coders and/or experienced users are in a "can't see the forest for the trees" position. Sometimes the perspective of a new user like me can shine a light in these areas? I've seen it in my own line of work, someone will say "Why don't you just do it this way?", and I start off with all the reasons why this and that, and then sometimes it's "Wait a minute, you are right why DON'T we do it that way?" (or it triggers another thought process).

So some may be reading my posts as being aggressive, or complaining or something, well OK, maybe they are a bit, but it is meant in the spirit of advancement. I hope that can be understood, it isn't always easy to get that intent across in a post.

> [Edit] Just so you know I used the example of mondo but I don't know if it has been upgraded to handle ext4 yet. If not it likely will be eventually.Thanks, I know mondo was something I've looked at before, maybe the ext4 thing is what stopped me, I'll take another look.

-NTL2009

---

### Post by Zill on 2010-07-12
> **NTL2009 said:**
> ...I'm not really a coder, but I do have certain abilities in terms of seeing needs, defining solutions (at the user level) and documenting them. Maybe I can contribute in that way. I know that many coders see documentation as an unplesant task, but I don't mind so much. And they aren't always the best to do it, as they have too much understanding to explain it to others. But I do need to get the basics to be able to translate it...
The FOSS community always welcomes users who can help write good documentation.  If you *do* want to get involved then I suggest you take a look at the [Ubuntu Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam").

Regarding your original suggestion, I have been using 100% Linux systems for over six years and never found a need for a "bootable clone".  I just use [SBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to keep automatic daily backups.  In the unlikely event of a HDD crash, it is then simply a matter of a quick reinstall followed by restoration of my latest backup.

---

### Post by NTL2009 on 2010-07-12
> **Zill said:**
> The FOSS community always welcomes users who can help write good documentation.  If you *do* want to get involved then I suggest you take a look at the [Ubuntu Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam"). 

Thanks, that is one reason I'm interested in getting a reliable install process down pat, and having a bootable clone just makes it easier for me to feel comfortable experimenting. Being able to experiment easily will make it easier to validate documentation.

> Regarding your original suggestion, I have been using 100% Linux systems for over six years and never found a need for a "bootable clone".  I just use [SBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to keep automatic daily backups.  In the unlikely event of a HDD crash, it is then simply a matter of a quick reinstall followed by restoration of my latest backup.Well, 'need' is a strong word I guess. As in we only really 'need' water, food and shelter ;)

I'm actually a little surprised at the reaction here, but I guess it is because until you become accustom to having a certain, very convenient, very powerful tool, you don't really know what you are missing? Windows does not have it (AFAIK), and a lot of users (mac & Win) never even bother to back up, so I guess it is a small minority who appreciate this.

There is at least two other like-minded people out there, from my earlier searches (with similar reactions):

[http://bbs.archlinux.org/viewtopic.php?pid=555986](http://bbs.archlinux.org/viewtopic.php?pid=555986)

Let me give an example to explain why I _want_ this capability:

I've been supporting 7 different OSX installations across my family. So let's say I stop by my Mom's house, and I have not backed her system up in a while. I bring an ext HD that I have partitioned, fire up the SuperDup! app, select target and source, and click a button to tell it to re-boot from the clone after completion. We go off to take care of whatever, come back and the system is now booted into the clone. I try out a few apps and open a few files and poke around a bit just to confirm that everything is as expected, and I'm done with almost 100% confidence in that backup. I reboot back to her install, and I am confident that everything is as it was. And I have the previous clone on another partition (or another disk), so if there are any other questions, I can even boot into that and see what's up. No modification of anything is required, I can do it all as we chat about the weather it is so simple.

When I get home, I can boot into that installation by just plugging in and holding th option key to choose from the list of bootable installs. So now, maybe I want to check some other things out or install some SW, or whatever - I can do it at my leisure, on my schedule, and boot back to my install whenever I want.  I have never had to do a single thing as far as configurations, no chance to slip up and hose her or my installation. Maybe later, I clone those changes back to her drive, or just copy the few added things, whatever.

Now, compare that to something like SBackUp (and correct me if my understanding is wrong here, as I am new to this side of things)-
So I run SBackUp, and I end up with a file on my external disk. OK, now what? Other than not seeing any error messages, how do I know that backup is what I think it is? I could recover it, but doesn't that mean writing over her drive? What if it doesn't work then - I just hosed her install! Or recovering to another drive, but then messing with the configuration while I'm over  there - not the ideal situation, and it all takes time. And if I take it home, I'd need to recover it somewhere, and then play with these boot settings? Which is an opportunity to mess things up. Yes, slight if you know what you are doing, but especially if you are dealing with a crash, all these little things add to the stress level.

Now - multiply that times 7 installs, plus wanting to experiment a bit, and it adds up. So no, you do not 'need' this capability, but I truly find it extremely useful, and I was disappointed to learn this wasn't the SOP for Linux. Hey, that's OK, I'll adapt, but I'd prefer to find a way to emulate this capability as best I can, if that is feasible with a procedure, standard tools and maybe some scripts.

-NTL2009

---

### Post by Zill on 2010-07-12
> **NTL2009 said:**
> ...I've been supporting 7 different OSX installations across my family. So let's say I stop by my Mom's house, and I have not backed her system up in a while. I bring an ext HD that I have partitioned, fire up the SuperDup! app, select target and source, and click a button to tell it to re-boot from the clone after completion. We go off to take care of whatever, come back and the system is now booted into the clone. I try out a few apps and open a few files and poke around a bit just to confirm that everything is as expected, and I'm done with almost 100% confidence in that backup. I reboot back to her install, and I am confident that everything is as it was. And I have the previous clone on another partition (or another disk), so if there are any other questions, I can even boot into that and see what's up. No modification of anything is required, I can do it all as we chat about the weather it is so simple...-NTL2009
It's getting late here so maybe I am missing the point but isn't this *exactly* what the Ubuntu (and other Linux OS's) live CD does?  You can take a live CD to *any* PC and boot into a "clean" version of Ubuntu without touching the installed OS at all.  You can still view and/or edit files on the HDD if you wish but essentially nothing changes unless you want it to.

---

### Post by NTL2009 on 2010-07-12
> **Zill said:**
> It's getting late here so maybe I am missing the point but isn't this *exactly* what the Ubuntu (and other Linux OS's) live CD does?  You can take a live CD to *any* PC and boot into a "clean" version of Ubuntu without touching the installed OS at all.  You can still view and/or edit files on the HDD if you wish but essentially nothing changes unless you want it to.

No, that is a good and useful feature, but it is not what I'm talking about. It is a portion of what I'm talking about, that is, you can boot into it separate from the installed local system, with no changes to either. (By local, I mean the system installed on the local internal HDD)

If I could optionally make that LiveCD pick up ALL the programs, settings, configurations and data from the installed local system, and then choose to boot that in my machine at home, yes - that is what I'm looking for.

It would need to be an HDD to be large enough to clone most people's systems & data, so that's one thing.  And I'd probably have multiple installs on partitions of that HDD. So I don't think that capability is part of any LiveCD I've heard of, but I could be wrong as I'm new at this stuff, and trying to learn what is available.

-NTL2009

---

### Post by marshmallow1304 on 2010-07-12
> **NTL2009 said:**
> If I could optionally make that LiveCD pick up ALL the programs, settings, configurations and data from the installed local system, and then choose to boot that in my machine at home, yes - that is what I'm looking for.

That's pretty much exactly what Remastersys does.

---

### Post by waynefoutz on 2010-07-12
Mondo Rescue will clone a physical drive, all it's partitions, and even GRUB. 
[http://www.mondorescue.org/]("http://www.mondorescue.org/") You should be able to install it with synaptic.

---

### Post by NTL2009 on 2010-07-12
> **marshmallow1304 said:**
> That's pretty much exactly what Remastersys does.

> **waynefoutz said:**
> Mondo Rescue will clone a physical drive, all it's partitions, and even GRUB. 
[http://www.mondorescue.org/](http://www.mondorescue.org/) You should be able to install it with synaptic.

Thanks, I will need to give these a closer look. I had earlier put Remastersys on back-burner, as the docs said:

> # It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.

I didn't see anything about Remastersys cloning to an HDD, and I would want to back up a larger data set than a DVD would hold - if it can do that, and boot from it (like it can from CD/DVD) it could be a good candidate.

Again, I guess I'll just have to give mondorescue a try too. It wasn't clear from what I read if it would boot the install itself, or whether it has to be restored first.

-NTL2009

---

### Post by waynefoutz on 2010-07-13
> **NTL2009 said:**
> Thanks, I will need to give these a closer look. I had earlier put Remastersys on back-burner, as the docs said:



I didn't see anything about Remastersys cloning to an HDD, and I would want to back up a larger data set than a DVD would hold - if it can do that, and boot from it (like it can from CD/DVD) it could be a good candidate.

Again, I guess I'll just have to give mondorescue a try too. It wasn't clear from what I read if it would boot the install itself, or whether it has to be restored first.

-NTL2009


I've used it with DVD's it backs everything up, and makes the first DVD bootable. Not sure if it can be done directly to a drive. But it will clone a drive.

---

### Post by marshmallow1304 on 2010-07-13
Remastersys makes an iso image.  You can write it to a CD or DVD if size permits, but you could also put it on a USB drive using usb-creator-gtk or unetbootin.

---

### Post by NTL2009 on 2010-09-12
I'm finally getting back to this task.

I tried Remastersys, but it seems to only want to handle images that can fit on a DVD. My install is larger than that, so that's seems to be a no-go for this process. And again, I'd like to be able to actually boot up the backup to be able to test that it is valid and I don't want to over-write my known-good installation on my internal HDD to test it - I'd be back to square one if anything in that process failed (or if I made a mistake). 

What I have been able to do so far, is to do a fresh install on an external, verify it boots, and then use Grsync to sync my internal "/home" to that new "/home". So now, that new install sees all my data and most of my configurations, but many of the programs and panels don't function, as there are missing pieces that need to be synced in "/". If I just new what needed to be synced and what needs to avoid being synced in "/", I'd be set I think. I've tried syncing some of the folders within "/", excluding "/boot" so I don't change the bootability of my external, but some programs and panels still did not function, and I must have over-written the pointers to "/home" as it started pointing back to the "/home" on my internal drive rather than "/home" on that external drive. I don't know where the pointers to "/home" (a separate partition) are stored. I'd think it would be a symbolic link, but I couldn't find it. But I seem to be a few steps closer.

-NTL2009

---

### Post by gwgerrity on 2012-03-15
> **bodhi.zazen said:**
> Where did you get the idea you would need to "invent" something ? You were given several options, some command line, some graphical.

Remastersys is graphical and about as straight forward as it gets.

You do not need to "invent" anything, you need to evaluate the available tools and learn a few things about how Linux works, mainly grub2 and fstab.

You have several options that were not listed previously :

1. Gparted.

2. Clonzilla.

[http://clonezilla.org/](http://clonezilla.org/)

[http://clonezilla-sysresccd.hellug.gr/](http://clonezilla-sysresccd.hellug.gr/)

You would do best to check your "attitude" and preconceived notions at the door, they will not help you much.

The problem is **not** attitude!

Clonezilla and dd simply won’t produce a bootable drive, at least for my configuration. I have a Dell Inspiron 1564 labptop with an internal 500GB HD and an identical USB HD. Both drives were formatted identically with gparted and have a partition for Windows 7, a spare fat32 partition, a separate grub partition, and an extended partition with separate swap and Linux sub-partitions. There is a bit of left over unformatted space in case I need it later. Both drives were checked with badblocks and passed. I did this because the original internal HD had too many bad blocks to hide and it caused both clonezilla and dd to fail (second-hand laptop!): the bad blocks were in the Windows partition.

The system was built on the internal HD and both Windows 7 and ubuntu Linux 11.10 work just fine. After cloning with Clonezilla (or dd — makes no difference), and attempting to boot from the External HD, grub has no menu for sdb, just the systems on sda, the internal drive.

Someone suggested that I use update-grub with both drives running and that would fix it. Well, it does add the windows 7 partition on sdb, but nothing else. Attempting to boot Windows 7 causes Windows to try and fix itself, but it fails. Rebooting on sda, Windows comes up just fine.

I mention this because if I attempt to boot up Linux from the USB HD, then what is booted (successfully) is the system on sda, as expected, since no alternative is given for sdb. I can check what is mounted where using Disk Utility, and sdb1 and sdb2, the Windows and FAT32 partitions are mounted as media, but **not** the corresponding ones on sda. The grub partition (sda3) and the Linux partition (sda6) on sda are both mounted, at “/boot” and “/”, respectively, once again, as expected if sda were being booted.

As near as I can tell, there are two problems, although there may only be one:

[LIST=1]
[*]grub is not setting up correct entries for booting sdb, and certainly not in its copy on sdb;
[*]The MBR on sdb is incorrect for sdb, or the MBR on sda is being used to try to boot sdb.
[/LIST]

Like the original poster, I want to use the USB drive for backup as well as a bootable option should the internal drive fail. On an Apple Macintosh, I use Carbon Copy Cloner.

Any “real” help would be appreciated.

George
------

---

### Post by gwgerrity on 2012-03-15
> **Zill said:**
> The FOSS community always welcomes users who can help write good documentation.  If you *do* want to get involved then I suggest you take a look at the [Ubuntu Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam").

Regarding your original suggestion, I have been using 100% Linux systems for over six years and never found a need for a "bootable clone".  I just use [SBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to keep automatic daily backups.  In the unlikely event of a HDD crash, it is then simply a matter of a quick reinstall followed by restoration of my latest backup.

I have replied in detail by amplifying why clonezilla and dd won’t work (at least for me), but didn’t state why the solution of just a quick reinstall isn’t a solution if it involves taking anything off the web. I am sending this computer to Africa, where even a good connection for email can be a problem. A backup and restore solution must be self-contained, and so a bootable external drive is a necessary solution.

George
------

---

### Post by howefield on 2012-03-15
Old thread closed.

Please start a new thread if you require suppport.

---

