---
title: "Need help partitioning and installing ubuntu netbook remix"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by da1337ninja on 2010-04-06
I was having major problems with my last installation so i decided to wipe and reinstall. I tried using the erase and install function in the install program but it failed to load GRUB. After doing some research, many people suggested to partition your HD. So, i came up with this partition scheme. I have a 8 Gig SSD.

4 Gigs for UNR Main system (mount point "/") type: ext4
2 Gigs for home directory (mount point "/home") type: ext4
2 Gigs for swap type:swap

When i started the installation, it said that it failed to load a partition of type ext4. Is there something I'm doing wrong? I kinda a newbie at installing linux. I'm very well versed in Mac. Usually when I install I do a nuke and boot. Is it necessary to do it for my netbook SSD? If so how would I? I really appreciate any help because I need this computer running asap.

---

### Post by da1337ninja on 2010-04-06
So i decided to scrap that partition table and go with a new one:

4 Gigs to main system (mount point "\") type: ext3
4 Gigs to home directory (mount point "\home") type: ext 3

I figure i don't really need a swap. Plus I don't want to kill my SSD. Anyways, i tried this and this is the exact error I got:

```
The attempt to mount a file system with the type ext3 in SCSI2(0,0,0), partition #1 (sda) at / failed.
```

What do I do? Please help!!!

---

### Post by audiomick on 2010-04-06
Hallo,
this is a guess, but what it looks like is that the computer is starting from your old grub, and not from whatever medium it is you are trying to install from.

Please post a bit more specifically what you are doing, i.e. trying to install from CD, from USB or whatever, and precisely what steps you have taken.

 I don't know if I will be able to help further, but with that info, someone else might.

---

### Post by farsight on 2010-04-06
Hi there,

I'm writing this from UNR on an asus eeepc 1000. I installed the operating system by first creating a bootable USB image of 9.10. (If you want to boot to a USB on this machine, press and hold escape whilst the system loads then choose USB).

Anyway, I think you are setting it up the same as I have chosen for mine. I mounted "/" to the smaller of the two hard drives, and the "/home" partition to the large, as this is where I will be adding the most data. I agree that there is no need for swap, mine works fine without it. My install was performed by choosing to manually allocate the partitions during install. Now, if I remember rightly, at this stage you can right click your hard drives and choose format, followed by selecting how and where you want to organise your mounts. As you say, "/" on one 4 GB HDD and "/home" on the other 4 GB HDD.

I am not exactly sure what your error is or means, however I suspect that the lack of a format during install is what is causing the system to hang. 

Again: *back up* prior to doing this.

Farsight

---

### Post by da1337ninja on 2010-04-06
I'm using a bootable USB drive. From that I boot into live mode and use gparted to create a new partition table (formate MSDOS), which erases the old data. Then, I run the install tool and use the built in partitioner to partition my drive. When it's installing, it stops and gives me that error. Am I formatting the partition to the wrong type?

---

### Post by farsight on 2010-04-06
Hey again. With the bootable USB I didn't bother actually running liveCD but proceeded straight to install option from the options menu. I then performed the partition as it seems you have, by manually selecting to mount each partition on an appropriate drive, though with the difference that at this stage I chose to format each hard drive immediately prior to mounting. Using this method, during install a message displays stating that formatting is being performed :)

The format that I chose to use for both "/" and "/home" was the new ext4. I have no reason to suspect that ext3 should cause your error. If this is what you have been using up until now, give ext4 a go. The reason I chose ext4 was a personal choice as opposed to an educated decision, with the only logic applied being that ext4 is newer than ext3 and so must present certain advantages.

Two more useful pieces of info you might be able to provide:
1) What netbook are you attempting to load UNR on to?
2) Does the MD5 sum for your downloaded image match that for the image, as provided here: [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

Farsight

---

### Post by da1337ninja on 2010-04-06
Farsight:
In the partition window I had the format box checked. I think that's what you mean. I chose ext3 because it's more stable than ext4. Plus i think ext4 does more journaling and writing to HD, which i don't want since I have an SSD. I'm pretty sure my MD5 hash is accurate as I downloaded it from the Ubuntu website. Plus, I used this same USB stick to install it before. I'm installing on an Acer Aspire One 110.

---

### Post by farsight on 2010-04-07
Hey again,

I've had a little bit of a look around. How did you install the UNR image on to the USB? This post seems to suggest that Unetbootin is the best method for loading the image:

[http://ubuntuforums.org/showthread.php?t=1315292]("http://ubuntuforums.org/showthread.php?t=1315292")

Other users seem to have experienced a similar problem: 

[http://www.linuxforums.org/forum/ubuntu-help/157690-unable-install-aspire-one-a110.html]("http://www.linuxforums.org/forum/ubuntu-help/157690-unable-install-aspire-one-a110.html")

Nevertheless, I guess you might try to install regular ubuntu and then convert to give the appearance of UNR. I didn't fully read this post, however it seems that it is a possibility:

[http://ubuntuforums.org/showthread.php?t=1133052]("http://ubuntuforums.org/showthread.php?t=1133052")

Sorry I can't help bypass the problem, but at least you have a life line in achieving pseudo-UNR installation. :D I don't understand it, the ubuntu support seems to suggest that SD cards might "act-up" after a suspend, but nothing more sinister than that with respect to your netbook.

Farsight

---

### Post by farsight on 2010-04-07
Heya,

Just stumbled along this post:

[https://help.ubuntu.com/community/AspireOne110L]("https://help.ubuntu.com/community/AspireOne110L")

It offers some information on installation on a (I presume) closely related netbook. Hopefully this can help you a little :)

Farsight

---

### Post by farsight on 2010-04-07
Here we go, here is a work around that apparently works. Note, many other people are having a problem with SSD's, suggesting this problem is due to your hardware as opposed to ubuntu:

> 

Ok, I write this for anyone else that experiences this issue. It's not a pretty workaround, requires time and patience, but having had the exact same problems you guys have had, right down to the exact same numbers where zeroing out the drive fails, I type this from a successfully installed UNR on that very same SSD.

I haven't fully finished playing around with this, the final attempts  will be to have myself a larger root partition, you'll read how in just a minute.
Initially obviously, this thing would also fail at gparted. After all kinds of retries I ended up choosing the option to try UNR without making any changes off of the usb stick from which I was trying to install UNR in the first place.
Under the system menu, you can scroll down and launch the gparted utility, where it will tell you that whatever is there is unrecognised.

I started by trying to make 500Mb partitions to see if I could get one in without an error, the object being to find my way past any bits that didn't want to be written to and find a big enough contiguous space in which to install UNR.
The first 500Mb partition (tried ext4 filesystem) didn't want to take at all giving an error whenever it attempted to write the filesystem. Gparted alllows you to specify how much space precedes the partition you are attempting to make, so the next attempt to make a partition (already chose to make msdos partition table on the unrecognised whole drive space, was first thing it made me do before I could attempt to put any partitions in) I specified 500Mb space prior to the 500Mb partition I wanted. No luck here either.
This made me start from the other side of the ssd first. Something like 7151Mb space at start then my 500Mb partition at the very end. Didn't like that either, again writing filesystem. Each time I did this, it did successfully create a partition, just not anything it could recognise filesystem wise. Just for fun, this final one, I selected again and this time chose to format it to fat32. Success, a recognisable partition. I made 3 more 500Mb partitions next to each other working back from the first end one, all fat32, all successfully. I then removed the first partition (one at the very end of the drive) and stuck a 1Gb next to the last one I'd created, then repeated taking off the oldest and making a new next to the newest (can only have 4 primaries).
When I was left with 1Gb at the start of the drive I started messing with 100Mb partitions, as obviously I'd been unable to write anything first go around at the start with 500Mb parts. Time after time success right until the very first 100Mb. Tried then leaving 8Mb space at the start and making a fat32 partition from there. Succeeded.

Having successfully written fat32 partitions all over the drive with the exception of the first 8Mb (no big whoop) I then removed all the partitions I had left, and tried writing ext4 ones. Success every time. First 8Mb obviously not a chance clearly something weird going on there. Eventually, making a 500Mb swap partition at the end (linux-swap filesystem) and the rest as an ext4, I was ready to install.
It failed at grub install (95% of the installation) but when I clicked the files/folders button, I certainly did have all the folders for unr, some 2+ Gb having been successfully written to the drive. I tried to do grub manually, but there was no stage1 to be found anywhere, so any attempt to use what I had just made was fruitless.

I tried install again using the partitions I'd made, and this time after entering the username etc when it brings up the install button, I clicked the advanced button. I had made a slightly different partition scheme (which involved me having to format as fat32 and ext4 several times before it'd let me do a new linux-swap partition) and made a 100Mb partition which during install on the partitioning part, I selected to be /boot. On the advanced tab, this is the partition I chose to install grub to. Installation completed 100% this time but still was not able to boot into it.

Finally today, I let it choose partitioning for me (not the use whole drive or user selected partitioning). I had previously used the "try unr without any changes" off the usb drive and ran GParted making a 6.9Gb ext3 partition leaving 100Mb free at beginning of drive and a 500Mb swap right after the ext3 partition. I'd also made a partition for the 100Mb at the start but chose to do it using "leave unformatted". Once again during the process it gave me some trouble making the linux-swap, allowing any other filesystem to be put on that partition, and eventually giving in and letting me format it to linux-swap. This killed Gparted during install, so I removed the partition on that first 100Mb, which cured the hang at 70% so apparently this first little area that the SSD refuses to accept a filesystem on (GParted at this stage will write an ext4 there without an error, but when it rescans the drive it comes up as unrecognised still) that section.
Install chose to keep 2Gb of the ext3 partition and make the rest of it a 4Gb ext4 and tiny swap partition in there too. Again after providing user information and being provided the install button, I clicked advanced and chose to install Grub to sda2 (which was originally the big ext3 partition I'd made). Install completed. Moreover, when it rebooted, it successfully booted from the ssd, and for the first time I had to actually enter my password. All kinds of gnome things like the quick user change applet refused to load, but I was able to connect to wireless, and run any of the programs (firefox, openoffice, games etc).

To cap things off, I booted from the usb again (GParted doesn't appear in the system tools on the actual installed UNR it seem) went into GParted, and shrunk the 2Gb ext3 to 200Mb, leaving me a bunch of unallocated room. I couldn't expand the partition UNR had installed to, because it'd set up an extended partition, SDA1, containing a 4Gb partition and a tiny linux swap partition). Oddly enough, on reboot, none of the gnome applets that failed previously failed this time, I've successfully installed things like flash and watched movies over the net, installed some codecs to watch mpegs, and absolutely everything seems to work exactly as it should.

I'm going to blitz it all again. This time, I'll leave an 8Mb space at the start for the bit that doesn't like being written to, make a 200Mb ext3 partition right after it, and then run install again. Hopefully this will give me almost all the drive space, along with the ability to boot into it.

This has been 4 days of messing around, but I hate being beaten. Knowing nothing about linux didn't help either, but whatever goes wrong with these Intel SSDs on the aspire ones, it appears to be a very aggravating hitch, but not the end of the machines usability. There's most likely a much simpler way to do this, it's just a case of avoiding that first 8Mb of the SSD (you can't make a partition smaller than 8Mb, and don't forget, you want that as just unallocated space, if you try as I did to have it as a partition, GParted will screw up at 70% during install of UNR) but for me, it was very reluctant to create partitions until I'd tried different file formats on different areas first. Making a new partition table to free up the whole thing makes me have to mess around all over again, as it's always unwilling to let me put things in new places at first.

Hopefully this is of some use to anyone else that finds themselves in the exact same position. At the very least, you can make use of almost all of the SSD still, even if you decide to run your OS off of a USB stick.

Not an issue then with GParted, nothing else I tried on the SSD was successful either, and in fact GParted with it's many options is how I got around the problem, and turned what appeared to be a junked SSD into a perfectly usable one still.

Last edited by InfuriatingSSD (2010-02-11 02:44:20)


Reference: [http://gparted-forum.surf4.info/viewtopic.php?id=13825](http://gparted-forum.surf4.info/viewtopic.php?id=13825)

I hope this cures the problem!

Farsight

---

### Post by da1337ninja on 2010-04-12
Farsight,

Thanks a lot for all your help. When i was doing research, I found that same article. The process that user went through was much too long for me to follow (I got lazy). Instead, I just downgraded and installed 9.04 and it's been working ok for about a week or so. I want to use the update manager to upgrade to 9.10 via download but i'm too scared to. I think i might just have to wait for 10.04 to come out... :(

---

