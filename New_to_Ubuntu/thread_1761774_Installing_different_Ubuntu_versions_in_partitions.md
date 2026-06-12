---
title: "Installing different Ubuntu versions in partitions"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by greenewbie on 2011-05-18
I want to install 11.04 Nutty Narwhal in a separate partition on my HDD (for testing purposes) so that it doesn't affect my 10.10 Maverick partition. I've read up on the basics of making partions in EG [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition), I now understand the real basic stuff, like the differences between primary, extended and logical partitions.

 But what I'm totally confused about is on which partition (I currently have 4 primary partitions) [COLOR=#ff0000]a novice[/COLOR] like me should put 11.04 Nutty and how exactly do I do it?  The help documentation and forum postings I've looked at so far haven't given me clear answers to those questions, so I'm hoping you guys can help!  The solution which is easiest for a novice would probably be best at the moment (as long as it doesn't risk affecting my 10.10 Maverick stuff (ref booting up etc).  

 Please note that I'm the sole user on my PC and that other than setting up partitions on my HDD (which I did during the standard installation process when I reinstalled Maverick), the ONLY partition I've used is the one it boots to.   

 You'll no doubt think this is a totally daft question but is my home folder (ie [COLOR=Blue]john1-desktop[/COLOR]) actually located in **/dev/sda3 **which is [COLOR=#0000ff]&#8220;mounted at /home&#8221;[/COLOR] ?

 One thing I'm confused about is, if this is so, then is it logical for **/dev/sda****2 **to be the [COLOR=#ff0000]bootable[/COLOR] partition?  Does one partition boot into another? Please find attached screenshots of my partitions using the Disk Usage Analyzer tool and sudo fdisk -l command.  
 I've set up another desktop account [COLOR=#0000ff](john2-desktop)[/COLOR]. If I upgraded to Nutty using this **secondary** account, would it leave my **primary** account (as above) unaffected, still on 10.10 Maverick?

 When I set up the partitions, I wanted to do them all in[COLOR=Blue] /home [/COLOR]but the system said I had to select a different folder each time.  So I shrugged my shoulders, closed my eyes (more or less!) :P and clicked on[COLOR=#0000ff] /[/COLOR] and [COLOR=#0000ff]/boot[/COLOR] and [COLOR=#0000ff]/home[/COLOR] for my partitions.  Was this choice unwise for a novice?!  

I'd just like to mention that some time in the future (when I'm happy that I've worked out the technicalities of it all) I'd like to install Win XP on this HDD (just to use Skype which is the one and only thing I've had such persistent problems with for several years on Ubuntu), leaving several other partitions for different versions of Ubuntu (and possibly a different Linux distribution if I happen to find out that it's better for Skype than Ubuntu).  But I know that Windows is more complicated to set up, so if need be I'll do a totally fresh partitioning, that wouldn't be a problem.

 So thanks in advance for any help.

---

### Post by Elfy on 2011-05-18
mmm - first thing I would say is that your / and /boot partition are absolutely enormous :) 

Probably not any need to have /boot anyway unless you have very specific requirements for it.

What I would do assuming that those are all of your partitions - is shrink sda2 then install the 11.04 in that, if you choose manual partitioning you will be able to choose where to install it's bootloader - install that to the same partition as you install to (probably going to be sda4)

Then boot your normal install run sudo update-grub and it should see the new install.

On a slightly different note - your post is very hard to read, please use more whitespace.

If you update with a new user then the old user will have the updated system as well afaik.

---

### Post by Quackers on 2011-05-18
Firstly, if you now have 4 primary partitions on your hard drive, and you are not using GUID Partitioning you should NOT attempt to create any more partitions! 4 primary partitions is the maximum permitted on any single disc using the MBR partitioning system.
A /boot partition is not normally required on most domestic systems and just serves to complicate repair procedures.
Your home folder will indeed be in sda3 (if that's the partition you mounted as /home during installation).

---

### Post by Lateralis on 2011-05-18
Just to add to what forestpiskie as said, the /boot partition, if you really must have a separate partition for /boot, needs only be about 200 MBs at most.  Presently, only ~200 MBs of space is being used anyway!  If you want to be totally paranoid then you make that partition three, four or maybe five hundred, but really no more than that.  The remaining 109 GBs can be used, as forestpiskie says, for your new Ubuntu install.

Edit: Just looked at some other people's partitioning schemes and they use less than 100 MBs - some as little as 32 MBs for their /boot partition.  And my current /boot directory contains 80 MBs of data.

---

### Post by Elfy on 2011-05-18
> **Quackers said:**
> Firstly, if you now have 4 primary partitions on your hard drive, and you are not using GUID Partitioning you should NOT attempt to create any more partitions! 4 primary partitions is the maximum permitted on any single disc using the MBR partitioning system.
A /boot partition is not normally required on most domestic systems and just serves to complicate repair procedures.
Your home folder will indeed be in sda3 (if that's the partition you mounted as /home during installation).

Didn't catch the second screenshot ... 

In light of that I'd change my mind.

Given what you have I would boot the livecd - remove the swap - resize both sda1 and sda2 - move the partitions about so the unallocated space is one.

Create an extended in there - then first create a new swap, then you can use some space there to create a partition to install to.

You will also need to change the fstab line of the current install if you do that to deal with the new swap.

---

### Post by Dngrsone on 2011-05-18
Okay, we have a problem or two here.

You have four partitions on your drive and that's fine for what you are using it for now.  Unfortunately, you have no extra space for more partitions, and you need a partition or two of empty drive in order to install 11.04 without affecting your existing 10.10 installation.

This is one of those "you can't get there from here" scenarios:  in order to accomplish your stated goal, you would have to somehow shrink an existing partition (or two), and break at least one of the primary partitions down into a group of secondary partitions.

Your /boot partition doesn't need to be very big, only about 300MB.  Your swap also shouldn't be more than 2x the amount of RAM on your machine.

I am running 11.04 on a 20GB partition with /home on a 30GB partition, and a third, /Data part for music and such.  I'd say plenty of room on my 320GB drive to install a few more operating systems, but Vista owns some 111GB.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/argh.gif[/IMG]

Still I have enough room for a couple more versions of Ubuntu as they come available.

---

### Post by greenewbie on 2011-05-18
> **forestpiskie said:**
> mmm - first thing I would say is that your / and /boot partition are absolutely enormous :) 

Probably not any need to have /boot anyway unless you have very specific requirements for it.

What I would do assuming that those are all of your partitions - is shrink sda2 then install the 11.04 in that, if you choose manual partitioning you will be able to choose where to install it's bootloader - install that to the same partition as you install to (probably going to be sda4)

Then boot your normal install run sudo update-grub and it should see the new install.

On a slightly different note - your post is very hard to read, please use more whitespace.

If you update with a new user then the old user will have the updated system as well afaik.

Many thanks forestpiskie!

You're talking to a real Tech dummy.....the only bit I really understand so far is that my posting needed more white space (so I've done that now....I think I've mastered it!) :)

I'm going to see if eating some dinner now will awaken some brain cells in me.  In the meantime, surely I don't want to install to sda4: that's the swap partition?

---

### Post by greenewbie on 2011-05-18
Thanks very much guys.....I really hadn't counted on all these replies so fast! Back in 90 mins

---

### Post by Quackers on 2011-05-18
Feed the grey cells :-) Usually a good idea!
The way I would go about it is the way forestpiskie describes in post #5.

---

### Post by Elfy on 2011-05-18
> **greenewbie said:**
> Many thanks forestpiskie!

You're talking to a real Tech dummy.....the only bit I really understand so far is that my posting needed more white space (so I've done that now....I think I've mastered it!) :)

I'm going to see if eating some dinner now will awaken some brain cells in me.  In the meantime, surely I don't want to install to sda4: that's the swap partition?We've mostly all been there at some point - if it gets to much and you really have no idea what someone said - tell them so and ask for a simplification ;)

Try and make some sort of decision and people will be more than happy to help you along.

---

### Post by srs5694 on 2011-05-18
Another option that might help is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program to convert one or more primary partitions into logical partitions. This may require resizing partitions, though, since every logical partition requires at least one unallocated sector immediately preceding it, and it's not clear if you've got such space. (By default, fdisk displays partition start and end points in cylinders, which are imprecise; you'd need a sector-precise fdisk listing to know if you've got gaps between your partitions.) Shrinking one or two partitions by 1 MiB or so should be relatively simple and quick, though.

Although temporarily deleting your swap space can be a good way to enable you to create an extended partition, since Windows requires a primary partition, just deleting the swap space would leave you in the situation of having to delete one of your existing Linux partitions to make room for Windows. With FixParts, you can convert one or more of your Linux partitions into logical partitions, thus freeing up one or more primary slots for Windows. Since you've got to resize partitions to make room for Windows anyhow, using FixParts to do a primary-to-logical conversion makes sense to me.

Be aware, though, that resizing partitions is inherently dangerous. You should back up your data before you begin with such a task.

One more warning: The Windows XP installer is known to convert logical partitions into logical partitions under some circumstances, but it doesn't always resize the extended partition. Since the extended partition *must* contain the logical partitions, but *must not* contain primary partitions, the result is an illegal partition table. Linux and Windows can both boot on such a disk, but some partitioning tools will flake out and claim the disk is empty. I just want you to be aware of this issue so that you can check for it and fix it if it occurs. (FixParts will correct this problem.) You can minimize the risk of running into this problem by creating your partitions using Linux tools before installing XP, and by ensuring that all four of your primary partitions exist (presumably one for XP, two for Linux, and one as your extended partition).

---

### Post by greenewbie on 2011-05-19
Many thanks [srs5694]("http://ubuntuforums.org/member.php?u=1032238") for your detailed reply.  I liked the fact that it catered for the option of installing XP on one of my partitions.  
 

 I've now installed Gdisk 0.7.1-1.  I'm confused already though! I clicked on the download link in [http://sourceforge.net/projects/gptfdisk/files/](http://sourceforge.net/projects/gptfdisk/files/)  which sent me the download; I clicked on open which sent me automatically through to Ubuntu Software Centre and I then installed it from that page.  Synaptic properties tells me the program is installed and the size is 463kB.  Is that how it should be?  And there's no sign of it in my Applications or System menus, no user-friendly button to click on: is this how it should be? I did scan through some of the explanatory notes (all Chinese to me!) and I gather it's a Command Line Interface program, so do I have to use Terminal to make the changes to my partitions?  If so, I strongly suspect that I'm venturing way beyond my depth here!
 

 And I'm still totally confused about the size my partitions should be, in what folder etc (EG should I have a partition in /boot or not?).  I've looked at all the advice given (very kindly, thanks to everybody once again) several times and I can't even quite work out if this advice is conflicting or not!  Basically it looks to me as if I couldn't have made more of a hash up of making partitions if I'd tried!  So I'm beginning to suspect that with my technical know-how as (extremely) limited as it is, I'd be better off doing a fresh reinstallation and redoing my partitions (but if so, I'd still like some advice on how big my partitions should be and in which folder etc I should put them)
 

 Thanks in advance for any further advice!

---

### Post by srs5694 on 2011-05-19
It's a text-mode program that doesn't appear in your GUI menus; as you suspected, you must launch it from a Terminal. Also, you installed the wrong package; you don't want gdisk, you want either fixparts, from [here](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/), or gptfdisk, from [here](http://www.rodsbooks.com/gdisk/download.html) (check the "Downloading GPT fdisk from OBS" section for links for three specific Ubuntu versions). I'm afraid the package options are a bit too complicated because of the fact that there are three closely related programs (gdisk, sgdisk, and fixparts) with different purposes and support library requirements.

The simplest partitioning setup is what Ubuntu does by default: Devote a small amount of space (1-2 times your RAM size is recommended, but I don't know what rule the Ubuntu installer uses) for swap and the rest for root (/). Many people, myself included, recommend devoting 5-20 GiB to root (/) and the rest to /home. In most cases, a separate /boot partition is *not* required, but it can be helpful or even necessary in some rare cases (older motherboards with drive-size limits, for instance).

---

