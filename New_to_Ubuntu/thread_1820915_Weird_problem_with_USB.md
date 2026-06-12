---
title: "Weird problem with USB"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-08-08
Ok, a couple of days ago, after a long struggle, I finally managed to  install Ubuntu 10.04 LTS on both my laptop and desktop computers, from  the live CD I had previously downloaded.

Now, I find I'm having the same issue on both machines, when I use the  USB ports: whatever I plug in works perfectly, but the moment I unplug  it (whether I just unplug it or I use the "safely remove drive" option),  it completely crashes the OS, to the point that nothing works, not even  the mouse, and I have to power down the machine, and power it back up.

Can anybody tell me WTH is going on, and how to fix it?

Thanks in advance. :)

---

### Post by Inodoro Pereyra on 2011-08-08
Nobody? :(

---

### Post by anewguy on 2011-08-08
Just a point about forum rules (yes, you can get officially warned on this - I was a couple of years ago):

don't bump a thread until at least 24 hours have elapsed with no reply.  Everyone is volunteer, and not everyone who may be able to help is just available to help you.  You may not have known about this rule, so I just wanted to advise you ;)

Also, I'll be checking to see if I can find anything resembling your problem on the net.  Right now I don't know why it would do that especially on 2 different systems.

Is it the same USB device, or ANY USB device?  What devices are they?

Did you install Ubuntu as stand-alone, dual-boot or as a wubi installation?

Did you run the update-manager after the install?  It may be something that is fixed in a later kernel.

Post that back and we'll go from there.  Also, I think you'll find the people who can help the most won't be on here for an hour or 2.

Dave  ;)

EDIT: if it's a Aiptek graphics tablet you may want to see: [https://help.ubuntu.com/community/AiptekTablet]("https://help.ubuntu.com/community/AiptekTablet")

You might also see: [http://derekneely.com/tag/system/]("http://derekneely.com/tag/system/")

---

### Post by Inodoro Pereyra on 2011-08-08
Thank you Anewguy for the warning. I honestly didn't know.:oops:

Here's what I can tell you about it:

IN both computers, Ubuntu was installed as stand alone, from the 10.04 live CD. Both computers had previously run 10.04, upgraded from a live CD 9.10 install, and ran fine, without any problems.

In both, all of the USB ports produce the same problem. I can leave a thumb drive or external hard drive connected for hours, and the machine will run fine, but the moment I disconnect them, everything freezes up.

The laptop is an Acer Aspire 5002 WLCi, AMD64, with 1.25 GB of RAM. Both onboard USB ports have the same problem.

The desktop is a Pentium 4 clone (single core) with 2 GB DDR2, and an Asus P5GDC Deluxe MoBo. All 4 onboard ports, and 4 extra USB 2.0 ports on a Compaq card are having the same problem.

I ran the update manager on the desktop last night. Didn't run it on the laptop yet.

I'm pretty sure the problem is the live CD, as it's the only thing both computers have in common. What I want to know is if I can solve it, without having to go reinstall both computers from the 9.10 CD, and then upgrade to 10.04...:-?

EDIT: I just did the " sudo apt-get remove modemmanager" thing on my laptop. Didn't work. :(

---

### Post by amjjawad on 2011-08-08
> **Inodoro Pereyra said:**
> **I'm pretty sure the problem is the live CD**

LiveCD has NOTHING to do with this. You run the LiveCD to try Ubuntu without installation and then install Ubuntu OR when you have some issues and you want to do certain task(s). Otherwise, you are NOT running Ubuntu from a LiveCD, are you?

---

### Post by Inodoro Pereyra on 2011-08-08
> **amjjawad said:**
> LiveCD has NOTHING to do with this. You run the LiveCD to try Ubuntu without installation and then install Ubuntu OR when you have some issues and you want to do certain task(s). Otherwise, you are NOT running Ubuntu from a LiveCD, are you?

Well, I couldn't tell you. I'm far from an expert when it comes to Ubuntu. All I know is that 2 weeks ago I was running 10.04.3 on both my computers without a hitch. Then, I made the mistake of trying to upgrade to 11.04, and now, having switched back to 10.04, this time installed from the downloaded live Cd, I'm having plenty of problems I never had before.

---

### Post by amjjawad on 2011-08-08
> **Inodoro Pereyra said:**
> Well, I couldn't tell you. I'm far from an expert when it comes to Ubuntu. All I know is that 2 weeks ago I was running 10.04.3 on both my computers without a hitch. Then, I made the mistake of trying to upgrade to 11.04, and now, having switched back to 10.04, this time installed from the downloaded live Cd, I'm having plenty of problems I never had before.

So you suspect there is something wrong in your LiveCD?

What other issues do you have?

You can post these issues here and we'll try our best or you can wipe your HDD and start from scratch but make sure to backup your important files if any.

I personally love to try lots of steps before wiping the HDD and install again but that's me :)

---

### Post by westie457 on 2011-08-08
> **Inodoro Pereyra said:**
> Well, I couldn't tell you. I'm far from an expert when it comes to Ubuntu. All I know is that 2 weeks ago I was running 10.04.3 on both my computers without a hitch. Then, I made the mistake of trying to upgrade to 11.04, and now, having switched back to 10.04, this time installed from the downloaded live Cd, I'm having plenty of problems I never had before.

When you did the upgrade from 10.04 to 11.04 was it via the Update manager - that is from 10.04 to 10.10 to 11.04 - or did you install 11.04 straight over the top of 10.04 without formatting the partition. Or did you go for the clean install. Not that how you upgraded should make any difference.

In your Grub menu do have any earlier kernels or distros to boot into. If you do try one of the earlier ones to see if the problem still happens.

Now to what could be the cause of the problem. When you downgraded from 11.04 to 10.04 was it a clean install - that is formatting the partition - or did you just put 10.04 straight into the partition leaving your /home folder as is? 

If all this is as clear as mud to you hopefully it will become clear with the next statement.

A down grade to an older version should always be done as a clean install to remove any chance of conflicting drivers and differences between versions of installed packages.

---

### Post by anewguy on 2011-08-08
> **westie457 said:**
> When you did the upgrade from 10.04 to 11.04 was it via the Update manager - that is from 10.04 to 10.10 to 11.04 - or did you install 11.04 straight over the top of 10.04 without formatting the partition. Or did you go for the clean install. Not that how you upgraded should make any difference.

In your Grub menu do have any earlier kernels or distros to boot into. If you do try one of the earlier ones to see if the problem still happens.

Now to what could be the cause of the problem. When you downgraded from 11.04 to 10.04 was it a clean install - that is formatting the partition - or did you just put 10.04 straight into the partition leaving your /home folder as is? 

If all this is as clear as mud to you hopefully it will become clear with the next statement.

A down grade to an older version should always be done as a clean install to remove any chance of conflicting drivers and differences between versions of installed packages.

Just returned to get back online.  After reading the new posts, down to yours, this is exactly what I was thinking as well.  Any downgrade is best done as a clean install, however downgrading from 11.04 to 10.04 is definitely a time to do a clean install.  Too many libs, executables, etc., that can be left behind from 11.04.

So, +1 on your post!

Dave ;)

---

### Post by Inodoro Pereyra on 2011-08-09
> **amjjawad said:**
> So you suspect there is something wrong in your LiveCD?

What other issues do you have?

You can post these issues here and we'll try our best or you can wipe  your HDD and start from scratch but make sure to backup your important  files if any.

I personally love to try lots of steps before wiping the HDD and install again but that's me :smile:

Well, I'm not a programmer, and, like I said, all I know about Ubuntu is that I love it. 
My training is in electronics, and, in a case like this one, the normal  MO is to look for anything in common on the affected systems. All these 2  computers have in common (besides the problem itself) is that both are  runnung clean installs from the live CD, and that both were running  perfectly before, on the upgraded version (through the update manager)  from 9.10.

Other than that, a couple of days ago, right after installing it on my  laptop, I spent little more than 20 hours straight to be able to get the  BCM43 wireless driver working on it, but, as I learned, reading dozens  of threads and articles while I was trying to get it running, that's to  be expected with the Broadcom wireless drivers...

> **westie457 said:**
> When you did the upgrade from 10.04 to 11.04  was it via the Update manager - that is from 10.04 to 10.10 to 11.04 -  or did you install 11.04 straight over the top of 10.04 without  formatting the partition. Or did you go for the clean install. Not that  how you upgraded should make any difference.

In your Grub menu do have any earlier kernels or distros to boot into.  If you do try one of the earlier ones to see if the problem still  happens.

Now to what could be the cause of the problem. When you downgraded from  11.04 to 10.04 was it a clean install - that is formatting the partition  - or did you just put 10.04 straight into the partition leaving your  /home folder as is? 

If all this is as clear as mud to you hopefully it will become clear with the next statement.

A down grade to an older version should always be done as a clean  install to remove any chance of conflicting drivers and differences  between versions of installed packages.

I have probably been through all those scenarios (and actually a few more) in the last 2 weeks.
Here's what happened, as best I remember:

Up till 2 weeks ago, I was running 10.04.3 LTS (Wubi) on both machines,  upgraded from 9.10. In both cases I had been running Ubuntu without a  problem since I had installed it, almost 2 years ago. I was using  Windows XP on my laptop, and 7 on my desktop.
2 weeks ago (give or take) I found out, while installing an application (Emc2) that 11.04 had been released. Even when I was warned here not to upgrade Wubi, I decided to do it. The installer crashed in the middle of the install, and I lost everything.
Then, since I had no use for XP anymore, I decided to do a clean 10.04 install on the laptop. I did it from the 9.10 live CD, and everything worked perfectly. 
Meanwhile, I had an extra hard drive I wanted to install on the desktop, and, due to the debacle with Wubi on the laptop, I decided to install it, and do a dual boot, with Windows 7 on one HDD, and Ubuntu on the other one. I did (again from the 9.10 live CD) and, despite a few little complications (had to install W7 twice), everything worked perfectly in the end.
A few days later, I decided to give 11.04 a try on the laptop, given that it didn't have wubi anymore. I upgraded, and pretty much hated 11.04 from the get go: way too many bugs. Frustrated (and pretty much in love with Compiz on my desktop), I decided that at least I was gonna have 10.10 on the desktop.
I upgraded to 10.10, and, for some reason, my video went straight to hell: menues didn't close, animations worked horribly, etc. 
That's when I decided to get the 10.04 CD (to save the time it takes to install 9.10, and then upgrade), and do a clean install on both computers. Now, both computers have clean installs of 10.04, and both have the same USB problem.

Sorry guys for the long post. I hope it helps somehow...:(

---

### Post by westie457 on 2011-08-09
Trying to eliminate some things out of the problem.

Do you get the same issues while running the live desktop from the cd? The thinking here is if the pc locks up when a USB device (memory stick) is removed while running from the cd then the problem is with the device. If everything runs okay then the problem is mostly likely to be a bad install caused by a bad burn of a LiveCD.

No other suggestions at the moment.

---

### Post by jtarin on 2011-08-09
What is your definition of a clean install? Walk us through the procedure you use.

---

### Post by anewguy on 2011-08-09
+1.  We need to know if all the partitions were reformatted, etc..  If not, you are leaving parts behind from other versions and that causes nothing but problems.  At this point it would be best to have  clean system before trying to install again.

Also - even thought the update manager may tell you a new release is available and you can upgrade to it, most I know always back up what they need, then reformat the partitions and do an install instead of an upgrade.  Upgrades can leave things behind that don't cooperate - old libs, old settings, etc..  As far as 11.04 goes, an install, not an upgrade, is the only way to go.  I'll leave it to your judgement about 11.04 - personally I had some problems, so I did a clean install (reformatted the partitions) of 10.04, since it's the latest LTS release anyway

---

### Post by Inodoro Pereyra on 2011-08-09
> **westie457 said:**
> Trying to eliminate some things out of the problem.

Do you get the same issues while running the live desktop from the cd? 

Live desktop?:confused: Would that be running Ubuntu from the CD, without installing it?

> **jtarin said:**
> What is your definition of a clean install? Walk us through the procedure you use.

Hmmm...Selecting "Use the whole drive" in the partition manager? I didn't see any instruction that'd let me manually format the drive...

> **anewguy said:**
> 
Also - even thought the update manager may tell you a new release is available and you can upgrade to it, most I know always back up what they need, then reformat the partitions and do an install instead of an upgrade. 

Yeah, I'm an idiot. Got it.:lol::lol:
The reason I did the upgrade is because I'd done it before from 9.10 to 10.04, without any issues. Of course, it didn't take long for me to realize I had screwed up. Unfortunately, those realizations tend to come when it's already too late. 

Either way, I'm starting to think the best solution is gonna be doing a new install from the 9.10 CD, and upgrading to 10.04, like I did before...

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> Either way, I'm starting to think **the best solution** is gonna be doing a **new install from the 9.10 CD, and upgrading to 10.04**, like I did before...

That would be the WORSE solution ever.

Long story short (I can explain in many pages but that will make it long and complicated so I'll take the short version) ...

1- Ubuntu 10.04 is LTS ([https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)). Ubuntu 11.04 is not. Above all, Ubuntu 11.04 has Unity Desktop and definitely it's not like 10.04. You need to make your mind and decide which one you are going to use. If you want to try new things then 11.04. If you want stable OS then 10.04. End of Story.

2- Download the release of Ubuntu you want and make sure it matches your machine type (32bit or 64bit). 

3- After you download it, check **[MD5SUM ]("https://help.ubuntu.com/community/UbuntuHashes")**and create your **[LiveCD ]("https://help.ubuntu.com/community/LiveCD")**or **[LiveUSB ]("https://help.ubuntu.com/community/Installation/FromUSBStick")**- instructions of howto do that is here.

4- Boot your machine from your LiveCD or LiveUSB

5- Follow these steps: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

In case you want to install Ubuntu only (without Dual-Booting it with Windows) then just ignore step 3 in the above link which is talking about creating NTFS Partition for Windows.

6- Then you need to Click Install Ubuntu from your Desktop (yes, while you are on the Live Session while you are booting from the LiveCD or LiveUSB).

7- In case you want to Dual-Boot with Windows, then much better to install Windows first then Ubuntu. If you just want Ubuntu on your machine then install Ubuntu and follow this:

[http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

Whether you are Dual-Booting or not, just Double Check and make sure [**The Boot Loader (GRUB2)**]("http://en.wikipedia.org/wiki/GNU_GRUB") will be installed in /dev/sd**a** which is the **[MBR]("http://en.wikipedia.org/wiki/Master_boot_record")** of your HDD.

8- After installation is done, make sure to update your system.

9- Done.

In my signature, there is a guide of HOWTO Dual-Boot. If you didn't like it, you can search on google or [www.googlubuntu.com]("http://www.googlubuntu.com")


ABOVE ... will help you in case you decided to go that route and I recommend it because, in my humble opinion, you have followed the wrong approach to install Ubuntu on your machines.

Just for the record, Ubuntu 9.10 is NOT supported anymore so don't even bother yourself with it. On the top of that, I see no point to install a version and then upgrade it to the latest version?! you can do that simply by installing the desired version straightforward :) 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Inodoro Pereyra on 2011-08-09
Thank you Amjjawad for taking the time. That's an awesome walk through. :)

My reasoning behind using the 9.10 live CD is simple:

1. That CD has been shipped to me from Canonical, and I have installed it several times, so I KNOW it works perfectly.

2. Even when installing from the 10.04 CD may seem faster, it doesn't include the B43 driver, while the 9.10 CD does. Last time, I spent over 20 hours to make that driver work, and, to be honest, I don't really know how I did it, so I don't expect this install to be any faster.

3. My Internet connection is really bad. I rent a bedroom in a boarding house, and the router is in the bedroom farthest from mine. So, last time I downloaded the 10.04 live CD, it took almost 2 full days.

Other than that, in your tutorial you say you only created root and swap partitions. How many partitions should I create, and how big? I also have a 40 GB HDD (long story), so I need to have as much drive space available as possible. 

As per my version choice, it's simple: I'm sticking with 10.04, until the next LTS shows up. I'm not touching 11.04 with a 10 Ft. pole.

---

### Post by amjjawad on 2011-08-09
[http://ubuntuforums.org/showpost.php?p=11101432&postcount=126](http://ubuntuforums.org/showpost.php?p=11101432&postcount=126)

You most welcome :)


Sorry, can't post more coz i'm so busy ...

Edit:
The most recommended scheme is:

/ (root) - ext4
/home - ext4
SWAP - Swap-Linux

Size? depends.
Swap? If your RAM is 2GB and more, RAM=SWAP
If RAM is 1GB RAM or less, SWAP=RAM or SWAP = Double RAM (2GB in this case).

---

### Post by Inodoro Pereyra on 2011-08-09
Great. Thank you again for everything. Now I'm ready to take the plunge. :P

I will report back when I'm done.:D

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> Great. Thank you again for everything. Now I'm ready to take the plunge. :P

I will report back when I'm done.:D


Most welcome and I'll be waiting for your next post ;)

Good luck!

---

### Post by Inodoro Pereyra on 2011-08-09
Ok, first snag. 
I did everything as you explain in your link. Opened the live session, went to GParted, and created the new partitions. Since you only created 2 partitions (root and swap), and I needed 3, I made the third partition exactly like the first one. That is:

Create as: Primary partition
File system: ext 4

So I ended up with:

/dev/sda1.....Ext4..............15.63 GiB
/dev/sda2.....linux-swap.....2.00 GiB
/dev/sda3.....Ext4...............19.63 GiB

But, when I hit "apply", I got an error message. Here's what the "details" file says:

**Create Primary Partition #1 (ext4, 19.63 GiB) on /dev/sda** 00:00:03  (ERROR)
create empty partition  00:00:01  (SUCCESS)
          path: /dev/sda3
          start: 36965565
          end: 78140159
          size: 41174595 (19.63 GiB)

set partition type on /dev/sda3  00:00:02  (SUCCESS)
           new partition type: ext4

create new ext4 file system  00:00:00  (ERROR)

    [B]mkfs.ext4 -j -O extent -L "" /dev/sda3
           [/B]mke2fs 1.41.9 (22-Aug-2009}
           Could not stat /dev/sda3 --- No such file or directory

           The device apparently does not exist; did you specify it correctly?

libparted messages   (INFO)

Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting. 

The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.


So what does this mean? Should I just reboot, and everything will be ok, or should I have set up the partition differently?

Anyways, I am using the 9.10 CD, as I don't have the time to download a new copy of 10.04, and I don't trust the one I have...

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> Ok, first snag. 
I did everything as you explain in your link. Opened the live session, went to GParted, and created the new partitions. Since you only created 2 partitions (root and swap), and I needed 3, I made the third partition exactly like the first one. That is:

Create as: Primary partition
File system: ext 4

So I ended up with:

/dev/sda1.....Ext4..............15.63 GiB
/dev/sda2.....linux-swap.....2.00 GiB
/dev/sda3.....Ext4...............19.63 GiB

But, when I hit "apply", I got an error message. Here's what the "details" file says:

**Create Primary Partition #1 (ext4, 19.63 GiB) on /dev/sda** 00:00:03  (ERROR)
create empty partition  00:00:01  (SUCCESS)
          path: /dev/sda3
          start: 36965565
          end: 78140159
          size: 41174595 (19.63 GiB)

set partition type on /dev/sda3  00:00:02  (SUCCESS)
           new partition type: ext4

create new ext4 file system  00:00:00  (ERROR)

    [B]mkfs.ext4 -j -O extent -L "" /dev/sda3
           [/B]mke2fs 1.41.9 (22-Aug-2009}
           Could not stat /dev/sda3 --- No such file or directory

           The device apparently does not exist; did you specify it correctly?

libparted messages   (INFO)

Error informing the kernel about modifications to partition /dev/sda3 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda3 until you reboot -- so you shouldn't mount it or use it in any way before rebooting. 

The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.


So what does this mean? Should I just reboot, and everything will be ok, or should I have set up the partition differently?

Anyways, I am using the 9.10 CD, as I don't have the time to download a new copy of 10.04, and I don't trust the one I have...

I suggest to cancel the changes you made, reboot and start again.
If the same issue happened, your CD might be damaged. Keep in mind that GParted on Ubuntu 9.10 LiveCD is an old version and it might has some bugs or something.

Have you tried to create new partition table?

If you have a friend with a better internet speed, I think it's good idea to ask for his/her help :)

Edit:
Sometimes, it happens especially when running the Live Session from LiveCD instead of LiveUSB. CDs are slower than USB Drives. For better performance and less/free errors, LiveUSB is recommended but I understand you don't have a high speed internet and it's hard for you to download Ubuntu now.

---

### Post by Inodoro Pereyra on 2011-08-09
Will do. 

Quick question: what would happen if I use GParted to delete everything and create a new single partition, format it, and then reboot and install Ubuntu "the dumb way"?:confused:

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> Will do. 

Quick question: what would happen if I use GParted to delete everything and create a new single partition, format it, and then reboot and install Ubuntu "the dumb way"?:confused:

As I already posted previously, you need at least two partitions, root and swap. Recommend to have 3, root, swap and home.

One partition means you'll have to use swap file instead of swap partition and I'm not sure how to do that.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


Edit:
Again, make sure to create new partition table as in here: [http://ubuntuforums.org/showpost.php?p=11101707&postcount=129](http://ubuntuforums.org/showpost.php?p=11101707&postcount=129)

---

### Post by Inodoro Pereyra on 2011-08-09
What I meant is, once I start installing, if I choose "use the whole disk' in the partition manager, doesn't it create the partitions automatically?

Either way, I just rebooted. I'm gonna try creating the partitions again.

---

### Post by zero2xiii on 2011-08-09
> What I meant is, once I start installing, if I choose "use the whole disk' in the partition manager, doesn't it create the partitions automatically?

Not sure if it will make 3 partitions (highly doubt it..) But it WILL install ubuntu correctly, thats why its there... lolz.. good luck

---

### Post by Inodoro Pereyra on 2011-08-09
Ok, all good. Just formatted the partition to ext4, and everything seems to be perfect. Will keep you posted. :)

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> What I meant is, once I start installing, if I choose "use the whole disk' in the partition manager, doesn't it create the partitions automatically?

Either way, I just rebooted. I'm gonna try creating the partitions again.

Definitely will create the needed partitions automatically but not sure about /home.
I have never used that. I always create my partition and then install Ubuntu and choose "Manual" or "Advanced Options".

If you checked the links I posted, I already explained it should be done manually ;)
[http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

---

### Post by Inodoro Pereyra on 2011-08-09
Well, now it's installing, so let's see what happens.

> **amjjawad said:**
> 
If you checked the links I posted, I already explained it should be done manually ;)
[http://ubuntuforums.org/showpost.php?p=11101891&postcount=131](http://ubuntuforums.org/showpost.php?p=11101891&postcount=131)

Not only I did, but I actually have them all open right now. If you saw my browser, I have like 20 tabs open...:biggrin:

Anyways, I was just looking for an easier option, in case the manual install didn't work..

---

### Post by amjjawad on 2011-08-09
> **Inodoro Pereyra said:**
> Well, now it's installing, so let's see what happens.



Not only I did, but I actually have them all open right now. If you saw my browser, I have like 20 tabs open...:biggrin:

Anyways, I was just looking for an easier option, in case the manual install didn't work..

Never mind :)

You are installing 9.10, correct?

---

### Post by anewguy on 2011-08-09
amjjawad:  Thanks for helping the OP!  I've been in and out a lot lately so I haven't had much time to follow/help on threads.

Inodoro Pereyra:  I noticed you put smiley's by your reply to my last post, but just in case - I really wasn't implying you're an idiot or anything!  I sure hope I didn't come across that way!  Wishing you only the best!

Dave ;)

---

### Post by fslezak on 2011-08-09
> **Inodoro Pereyra said:**
> Well, now it's installing, so let's see what happens.



Not only I did, but I actually have them all open right now. If you saw my browser, I have like 20 tabs open...:biggrin:

Anyways, I was just looking for an easier option, in case the manual install didn't work..

Why not upload a screenshot?:D

---

### Post by Inodoro Pereyra on 2011-08-09
Sorry I didn't reply earlier. A friend had a car emergency.

> **amjjawad said:**
> Never mind :)

You are installing 9.10, correct?

So far, I installed 9.10, and was able to test the USB before I had to run. Everything works perfect!\\:D/\\:D/
Now I'm waiting for my roommate to get back from work, so I can hook up the ethernet cable and install the B43 driver. Then, it's upgrade time!:D

> **anewguy said:**
> amjjawad:  Thanks for helping the OP!  I've been in and out a lot lately so I haven't had much time to follow/help on threads.

Inodoro Pereyra:  I noticed you put smiley's by your reply to my last post, but just in case - I really wasn't implying you're an idiot or anything!  I sure hope I didn't come across that way!  Wishing you only the best!

Dave ;)

You both have helped a lot. and I really appreciate the time you have put into this thread.

Don't worry about that comment. That's what the smilies were for.
Reality is I do feel like an idiot. Over the last year and a half, give or take, I've been working from home, fixing computers, since I've been unable to find a job (life in Miami is getting very rough). Thing is, I've been working on computers (mostly hardware) since '93, being that I am an electronics technician.
 Ever since I started, I have been advising my customers to ALWAYS keep their hard drives backed up, should anything happen. ALWAYS.
Well, guess what: I upgraded my perfectly functional 10.04, EVEN WHEN I WAS ADVISED NOT TO, and I didn't even think to back up my stuff. As a result of that, I lost a whole lot of work, and stuff that will prove very difficult (if not impossible) to find again.
So, yeah, not my finest hour...

---

### Post by Inodoro Pereyra on 2011-08-09
> **fslezak said:**
> Why not upload a screenshot?:D

2 reasons:

1. I don't know how to (which seems to be somewhat important).:lolflag:

2. Firefox doesn't show all the tabs anyway. It shows about 10, and an arrow on either side.

---

### Post by anewguy on 2011-08-09
Can I laugh with you on the backups?  I think we've all been there!  I used to be a systems programmer and system administrator on big iron all the way down to micros.  The old big iron, with it's proprietary operating system, had it's own way of storing where files where located, if you used it, to isolate the programmers, etc., from needing to know where a file was physically located in a large disk pool.  So, backups in those days were to big mag tape, and that includes this master index to where files are, what physical tape reel is current in the backup rotation, etc..  So, one day the drive starts failing that the index is on - we're talking bump some switches inside the back cover of the drive and tell it to go again broken.  About 1 1/2 hours later I thought I had things backed up so I have the vendor replace the HDA for the drive.  So, now it's time to restore that volume - that's when I find out I have myself in a catch-22 -> the tapes I backed it up to are in the index, and I can't access them without the index, which is what I'm trying to restore so I CAN access the backups.  There was a big "ooooppppssss" come out of my mouth, then 52+ hours of around the clock work finally got things back to where they belonged.  Mind you, even in those days it was a company that ran 24/7 and I had to request time usually at least a month in advance to either install a new release of the OS or do some other system work.  And I have them down for 52+ hours because of a silly mistake.  My boss, the tech manager for our very large IS department and an ex-vendor support person, told me not to feel bad because he wouldn't have thought about that either.  So - some of us forget to backup our machines when we should (I've burned myself on that at home many times!), and then some of cause an entire large company not to be able to access their computers for 52+ hours!  ;)

Dave ;)

---

### Post by Inodoro Pereyra on 2011-08-10
Damn!!! And you were able to keep your job?:shock:
Your boss must have been one hell of a nice guy! Why can't I find a boss like that one?:biggrin:

Either way, little update: a couple of hours ago I went through my old threads, and found a way to install the b43 driver without an Internet connection. So I did, and since I've been doing the 10.04 upgrade. So far, it's chugging along nicely.8)

---

### Post by anewguy on 2011-08-10
> **Inodoro Pereyra said:**
> Damn!!! And you were able to keep your job?:shock:
Your boss must have been one hell of a nice guy! Why can't I find a boss like that one?:biggrin:

Either way, little update: a couple of hours ago I went through my old threads, and found a way to install the b43 driver without an Internet connection. So I did, and since I've been doing the 10.04 upgrade. So far, it's chugging along nicely.8)


I think the only thing that saved my butt was that in those days finding a replacement wasn't easy due to the proprietary nature of the OS and the knowledge of having set up tons of stuff.  That wouldn't mean squat today - all of those old units are either boat anchors or being used for ocean fish habitats :), and all that old knowledge is no longer needed.  Admittedly the experience and ways of thinking hold over to most anything - it's just a box and an OS (says the guy who worked a little with Unix 20 years ago and has been too lazy to learn squat about ubuntu! ;) )  If I was still working and if I did the same type of thing today I would be immediately out of work with little if any possibility of a new job.  As you know, and I feel for you, jobs are extremely scarce today and there is an extremely large pool of good talent to chose from.  Hang in there!

Dave ;)

---

### Post by Inodoro Pereyra on 2011-08-10
Tell me about it!
And I must add there's an extremely  large pool of good **YOUNG **talent to chose from, and, at the pace technology is moving forward today, there's no much need for the experience anyway. So why hire the old fart, just because he worked on computers long before they were born, if that knowledge today is as useful as knowing how to make a stone ax?
I used to program micro controllers in hex, back in the day. Then, in the late '90s, I went to see a job for an industrial electronics firm, and, when I mentioned that to the brat that gave me the interview, he said "I'm not familiar with that language":roll:. Never again mentioned it, ever.
YOU don't know squat about Ubuntu? What's left for me to say then? All I know about it, so far, is the most efficient ways to screw up everything!

---

### Post by anewguy on 2011-08-10
> **Inodoro Pereyra said:**
> Tell me about it!
And I must add there's an extremely  large pool of good **YOUNG **talent to chose from, and, at the pace technology is moving forward today, there's no much need for the experience anyway. So why hire the old fart, just because he worked on computers long before they were born, if that knowledge today is as useful as knowing how to make a stone ax?
I used to program micro controllers in hex, back in the day. Then, in the late '90s, I went to see a job for an industrial electronics firm, and, when I mentioned that to the brat that gave me the interview, he said "I'm not familiar with that language":roll:. Never again mentioned it, ever.
YOU don't know squat about Ubuntu? What's left for me to say then? All I know about it, so far, is the most efficient ways to screw up everything!

Man. I sure remember the hex programming days.  Pretty much everything I looked at was hex dumps, and I did hex programming even on that simple Sinclair ZX80/ZX81 - hand assembled the code, then poked it all in.  Could make some great word procssors, spreadsheets, etc., that way on a system with no cursor, etc..  Did a lot of that on micros (read "IBM PC Compatible") for a while as well - makes it fun trapping interrupts to do what you want for additional functionality.  Just always had to remember the timing and getting through code quickly.

I'm one of those old farts as well - and you're right, then young people in charge don't understand what the background does for understanding things quickly and being able to debug better.  This entire idea of these "kids" today not needing experience to get into jobs that would be much more productive with an experienced person in place just really grinds me.  We all remember the days of trying to get that first job, of learning both on the job and by continuing education, working your way up to the job you want - in other words, paying ones dues.  Everything seems to have gone from vertical to horizontal - no more really "moving up".  To me, it's a shame.

I wish you only the best!  I did see somthing the other day from Microsoft that is sort of a rad tool using their database engine.  Might not be a bad choice to learn anymore.  I remember back in the late 70's being approached by some people regarding developing a multi-platform case/rad tool - they wanted my help in all of the terminal drivers as well as the portion of the tool that would generate the platform/OS specific things for the OS I worked with.  Imagine how much money we could have made if we had finished - a case tool for developing on any platform to run on any platform - a real "trick" in those days.  I really don't know what happened with the project - I got about 85% complete of the generators needed for my stuff done and then never heard from them again.  At first I was worried they "took" my work, but nothing ever turned up on the market and I heard later the group was all made up of people like myself in those days - technical knowledge but no business management knowledge.  The result was nobody coordinated things together, even with the blue print there, so people go bored and dropped off the project until there was nothing left.


I know it's hard, but keep the chin up and we will all wish you only the best!

Dave ;)

---

### Post by Inodoro Pereyra on 2011-08-10
Thank you Anewguy, I really appreciate it.:D
I've really never been a programmer myself, just did the programming as part of my training as an electronics technician (actually, as part of my specialization in digital systems), so hex was as far as I went, and loved it. Later on, I tried my hand at basic (on a TI 99/4A), and found it horribly complicated. Noting beats just punching a bunch of numbers, and getting the job done.
Then again, I did manage to write a small program in basic, for calculating transformers. Nothing fancy, just about 400 lines of code. Then, when I was about to finish typing it in, on the TI99, without any data storage device, about 20 lines before finishing, there was a short power outage (just a couple of seconds) and I lost everything.:( Next day I sold the damn computer, and I haven't written a single line of code ever since, until I started with Ubuntu.

Anyway, back to the present...:)
Good news! I finished upgrading to 10.04, tried my USB external HDD (which was the one with the problem before) several times, and everything works perfectly. Actually, I'm typing this reply on my laptop, while I'm starting the install on the desktop. 

To you guys=D>=D> thank you for taking the time to help me out. You have turned what could've been a nightmare into a walk in the park.

Finally, to anybody who may have the same problem, 3 things:

1. Follow the instructions laid out in this thread. They definitely work.

2. If you need to use 9.10, just as I did, the same instructions will work for you. If you get the same error message I got, just reboot the computer (on the live session), and format the 3rd partition on ext4.

3. **Ubuntuforums ROCKS!!!:D**

---

### Post by amjjawad on 2011-08-10
4- You ROCK too :)

Glad you managed to fix it and you most welcome.

One of the best things about Ubuntu is this place, I spend hours here daily and I just can't get enough from it :)

---

### Post by amjjawad on 2011-08-10
> **anewguy said:**
> amjjawad:  Thanks for helping the OP!  I've been in and out a lot lately so I haven't had much time to follow/help on threads.


Glad to see you back ;)

---

### Post by Inodoro Pereyra on 2011-08-10
> **amjjawad said:**
> 
One of the best things about Ubuntu is this place, I spend hours here daily and I just can't get enough from it :)

I couldn't agree more. I'm (or have been) a member on more than 20 different forums, from mechanics and general science, to homebrewing and soapmaking, this is not only the biggest forum I've ever seen, but, by far, the friendliest. :D

---

### Post by amjjawad on 2011-08-10
> **Inodoro Pereyra said:**
> I couldn't agree more. I'm (or have been) a member on more than 20 different forums, from mechanics and general science, to homebrewing and soapmaking, this is not only the biggest forum I've ever seen, but, by far, the friendliest. :D

If truth to be told, I wasn't a fan of Forums at all but that is history now. I'm in LOVE with Forums but not every forum, just Ubuntu's one :)
I'm a member on other forums like LXDE, Fedora, Debian, Mint, SliTaz, antiX, OpenSUSE and can't remember what else?
Ubuntu and antiX forums are the best so far. However, I spend most of my time here.

Sometimes, I feel that I like this forum even more than I like Linux :P

---

### Post by Inodoro Pereyra on 2011-08-10
> **amjjawad said:**
> If truth to be told, I wasn't a fan of Forums at all but that is history now. I'm in LOVE with Forums but not every forum, just Ubuntu's one :)
I'm a member on other forums like LXDE, Fedora, Debian, Mint, SliTaz, antiX, OpenSUSE and can't remember what else?
Ubuntu and antiX forums are the best so far. However, I spend most of my time here.

Sometimes, I feel that I like this forum even more than I like Linux :P

I was, and still am. But there's all kinds of forums out there, from the extra nice, to the downright nasty. I usually avoid big forums, as I've had bad experiences in the past, ranging from moderators believing they have the right to bash members to forums where the friends of the staff were able to use racist remarks without punishment. This is the first big forum I see where everyone, from the staff down, is so nice, and, to boot, it's the biggest of them all!:D

---

### Post by amjjawad on 2011-08-10
> **Inodoro Pereyra said:**
> This is the first big forum I see where everyone, from the staff down, is so nice, and, to boot, it's the biggest of them all!:D

Ditto :D

---

### Post by jtarin on 2011-08-10
> **Inodoro Pereyra said:**
>  This is the first big forum I see where everyone, from the staff down, is so nice, and, to boot, it's the biggest of them all!:DWith the exception of guys that like to argue about socialized medicine.:lolflag:

---

### Post by Inodoro Pereyra on 2011-08-10
> **jtarin said:**
> With the exception of guys that like to argue about socialized medicine.:lolflag:

GRRRRRR!!!!! :lol::lol:

I don't mind arguing. It'd be kinda dumb to expect everybody on a forum to agree with you. I do admit that sometimes I can get heated (can't help it, I'm half Italian), but, in the end, everybody is entitled to have their own opinions.
But, for example, check this one out:
This happened to me on a biodiesel forum, and was ultimately the reason I stopped participating in it. I joined a thread in which they were discussing one of my all time favorite topics: ethanol as a fuel. Shortly after I joined the thread, another member (clearly against the use of ethanol as a fuel, although unable to provide any valid reason to back up his opinions) posted an article from some scientist, "professor of this and that University" and what not. As I always do when somebody posts the word of a "professional" like that, I googled the "professor", and it turned out the guy actually was a scientist, and he was part of the research staff of the university. But he was an ENTOMOLOGIST!!!#-o
Of course, the guy immediately left the thread. No surprise there.
But, from that moment on, he made it a point to barge in any thread I replied to, and turn my reply into a full fledged flame war. But I'm not saying he did that for a month. He did it **every day, for a year and a half**, until I finally left the forum. That's the kind of people I don't like.

---

### Post by jtarin on 2011-08-10
> **Inodoro Pereyra said:**
> GRRRRRR!!!!! :lol::lol:

I don't mind arguing. It'd be kinda dumb to expect everybody on a forum to agree with you. I do admit that sometimes I can get heated (can't help it, I'm half Italian), but, in the end, everybody is entitled to have their own opinions.
But, for example, check this one out:
This happened to me on a biodiesel forum, and was ultimately the reason I stopped participating in it. I joined a thread in which they were discussing one of my all time favorite topics: ethanol as a fuel. Shortly after I joined the thread, another member (clearly against the use of ethanol as a fuel, although unable to provide any valid reason to back up his opinions) posted an article from some scientist, "professor of this and that University" and what not. As I always do when somebody posts the word of a "professional" like that, I googled the "professor", and it turned out the guy actually was a scientist, and he was part of the research staff of the university. But he was an ENTOMOLOGIST!!!#-o
Of course, the guy immediately left the thread. No surprise there.
But, from that moment on, he made it a point to barge in any thread I replied to, and turn my reply into a full fledged flame war. But I'm not saying he did that for a month. He did it **every day, for a year and a half**, until I finally left the forum. That's the kind of people I don't like.I hate to say it but the guy might have been onto something as there is a connection between ethanol and insects.

> Drinking alcohol may increase your attractiveness to mosquitoes.

An interesting study suggested that the ingestion of alcohol may stimulate mosquito attraction. Mosquito landing on volunteers significantly increased after alcohol ingestion compared with before ingestion (Shiral et al. 2002). Bernier et al. (2007) also reported that a subject who consumed alcohol regularly was the most attractive of the six people participating in a study of mosquito preferences. This most attractive individual produced the highest levels of acetone, ethanol and methanol in sweat (volatile skin emanations) but it is unknown whether these compounds were responsible for the increase in attraction. :lolflag:

---

### Post by Inodoro Pereyra on 2011-08-10
OMFG you DEFINITELY need to go see a doctor...:lolflag:

---

### Post by anewguy on 2011-08-12
I've also for the most part liked this forum.  I've been on other forums where I've simply stated I did "x" to fix a problem, only to told strongly and repeatedly from other members AND the administrators that I was wrong and shouldn't post false information!  You know, when you have figured something out only to someone else tell you you couldn't have, you get a little ticked.  I've walked away from more than 1 forum for that.

The only "trouble" I've had on this forum has been people who don't understand some of the moral responsibilities that come with posting.  I've had people that have been posting a thread purely for help in hacking someone else's computer or network, or doing a denial of service attack at some server, and you tell them to discuss it away from the forum they want to argue until the sun burns out.  People find it hard to believe, but there really can be legal and monetary problems for the owners and administrators of the forum for things posted on the forum.  I used to belong to a non-ubuntu forum that ran into both of those problems due to the posts of a member.  On this Absolute Beginners Forum here. one of these seemed so insane to me that I actually quit for several months.  At least having watched the forum it seems that some of those members here have either been reprimanded or banned.  That gave faith in the forum again and why I asked recently for my id to be reinstated.  The forum here is great, the people on it always trying to help to the best of whatever their abilities are.  It's a great place for everyone to learn.

---

