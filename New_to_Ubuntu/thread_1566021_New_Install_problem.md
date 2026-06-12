---
title: "New Install problem"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-09-01
Two days ago I purchased a new E-Machine (et1331g-07w) that has an AMD Athlon ll duel processor with a 640G HD.  I installed another 180G HD in order to install Ubuntu on so that I could leave the 640G hd with Windows 7 alone.  My thoughts went along the lines that I could then boot off of which ever drive I wanted to and load either Ubuntu or Windows.

This seemed to work well until today.  Today when I went to boot off of the 160G drive, nothing happens.  A blank black screen with a blinking prompt, with no boot what so ever.

When I then went to boot from the 640G drive, I get the loader prompt asking if I want to boot with Ubuntu or Windows.  Both boot fine and work as expected.

If I disconnect the 160G HD, I get the following error message when trying to boot

[COLOR=Red]Error: fd1 cannot get C/H/S values
grub rescue>_[/COLOR]

When I first installed Ubuntu on the 160G this drive showed up under Places -Computer.  I saw both the 160G and the 640G.  Now 160 is not showing up.

When I run Disk Utilities under the Control Panel it sees 160G and shows the entire disk as dedicated to ubuntu.  When I look at the 640G it looks like there are 3 partitions on it with the following labels:

[COLOR=Red]PQService                     /dev/sda1
System Reserved          /dev/sda2
Emachines                      /dev/sda3[/COLOR]

I think I may have caused this problem myself, but am so new to Linux and Ubuntu that I'm not sure, here is what I did that I think may be part of the issue.

After installing Ubuntu I was looking around in Places and saw both 160G and 640G HDs under Places -> Computer.  When I clicked on them an icon of the drives showed up on the desktop.  There was an up arrow with a underscore to the right of each of these drives in the Places menu and when I clicked on this arrow the desktop icon went away.  

When I repeated the same action today I got a message saying it was now safe to disconnect the hard drive (I did not see this message the first time I did this).

Does anyone have any idea what I have done to my drives and how to correct this issue?

---

### Post by jtarin on 2010-09-01
Some information. When you boot what is the first screen you see after the bios screen? What does it say? Is this the same screen you had before installing Linux? I think you installed Grub to the MBR of the larger drive with Windows and when you remove the smaller one you screw Grubs mapping up and it panics. I would advise you to repair your Windows install and then we can walk-through installing Grub in another location where it will be safe to disconnect your other drive without any problems. RDisconnect the Linux drive while repairing Windows. We will treat them as two seperate drives from here on out. Grub sees them as one large drive. When you have repaired your Window MBR to use the Windows loader and it work let me know.

---

### Post by Sleven7 on 2010-09-01
I now get a "Loader Screen"  It has multiple choices as to what I want to boot right after the bios screen (del for bios, f12 for booting options)

The loader has these options

Ubuntu 
Ubuntu Recovery
A memory test
Another memory test
Vista Loader
Windows 7 loader

When I first install Ubuntu on the 160G drive it would boot directly from that drive without any kind of "loader" loading.

---

### Post by Sleven7 on 2010-09-01
Thanks jtarin, it will be a few days (at least Friday) before I can make the recovery disks for Windows, I have to go buy some blank DVDs first.  Will get back to you as soon as I can, thanks again.

---

### Post by jtarin on 2010-09-01
> **Sleven7 said:**
> Thanks jtarin, it will be a few days (at least Friday) before I can make the recovery disks for Windows, I have to go buy some blank DVDs first.  Will get back to you as soon as I can, thanks again.
No problem. I've dual booted for years and finally found a fool-proof way to do it. While your at it you might want to look at the link in my signature about EasyBCD and download it. The forums on that site are a wealth of information about dual boot. We will use the Windows loader to boot Windows and then chainload Grub which we will place on the Linux drive.

---

### Post by Sleven7 on 2010-09-04
jtarin, I have downloaded EasyBCD and have a new hard drive.  The new system is not compatible with my extra old hard drives so I have no choice but to put the new OS on the main HD.  I downloaded Pinguy OS and burned the ISO to a dvd.  Booted from the dvd live and it seems to work fine.  I like the looks of Pinguy, it is like Ubuntu on steroids lol.

---

### Post by jtarin on 2010-09-04
Got a link to their website?

---

### Post by blazemore on 2010-09-04
The problem is, that menu is on the other hard drive.
When you remove it, your computer can't load that menu and so can't continue booting.

---

### Post by Sleven7 on 2010-09-04
Here is the link to Pinguy

[http://www.ubuntugeek.com/pinguy-osa-ubuntu-fork.html](http://www.ubuntugeek.com/pinguy-osa-ubuntu-fork.html)

---

### Post by jtarin on 2010-09-04
Thanks! Good Luck!

---

### Post by Sleven7 on 2010-09-04
A 4G flash drive does not have enough room to install Pinguy OS.  It ran out of room at 76% of install.

You mentioned that you had a fool-proof way of dual booting using EasyBCD, I'm all ears, :)  I opened the EasyBCD and looked around a bit, didn't do anything but look.  Have no idea how to use the program.  I'm going back to the site to read, but any suggestions will be greatly appreciated.

---

### Post by jtarin on 2010-09-04
When you install the Operating System Pinguy or Ubuntu 10.04 you want to make sure that you install Grub2 to the partiton that your Linux is on. In Ubuntu during the Grub2 setup you will need to look for a button that says "advanced" when you click on it it will show you the different partitions that exist on your computer. Choose the one that has Linux **_NOT THE MBR_**because you will overwrite the Windows loader if you do. As an example: My Windows is on my /dev/sda1 and it places its loader at /dev/sda (which is the name of the entire drive)where the MBR is located.My Linux installation is in an extended partiton named /dev/sda4 within that partiton I have /dev/sda5 and /dev/sda6. /dev/sda5 is my Linux partiton (ext4 filesystem) and /dev/sda6 is my swap file of 1GB. I will choose /dev/sda5 to install Grub2.[[COLOR="Red"]Here's a link to the installation and where you should see the "advanced" tab[/COLOR]]("http://www.unixmen.com/linux-tutorials/973-ubuntu-1004-lucid-lynx-step-by-step-installation-for-newbies-howto"). It's the 10th screen down. You must tell Grub2 where to install using this tab. Make sure you know where your Linux is installed.
[[COLOR="Red"]Here is a link to the illustrated guide for EasyBCD.[/COLOR]]("http://neosmart.net/forums/showthread.php?t=6350") Make sure you use EasyBCD ver 2.xx

---

### Post by Sleven7 on 2010-09-04
Sorry, seems I cann't follow a simple thread to the second page.  Thought my post had got lost, thats why I PMed you.  Thanks again for the guide.

---

### Post by Sleven7 on 2010-09-04
How do I know which partition Ubuntu will be on?

Also in the instructions there is this warning:

**Step Five**
Continue with the wizard, fill out the forms, and select the defaults  where applicable. When you reach page 7 of the installation wizard **do not press the advanced button and make changes. There is a bug in Ubuntu 10.04 that does** ***not***[B] allow you to manually install GRUB to another partition.

Should I be concerned?
[/B]

---

### Post by jtarin on 2010-09-04
No problem.....I just noticed you live in Central Fla. I used to live in Tallahassee from about 1989-1996.

---

### Post by Sleven7 on 2010-09-04
Do you really live in Vladivostok now?

---

### Post by jtarin on 2010-09-04
Yea for about 6 yrs now...married a Russian and have my own English school. It's a tough life here but I can survive as long as I have Linux to play with. :)

---

### Post by Sleven7 on 2010-09-04
I ran into a snag.  At the screen where it say install OSes side by side, it came back with the following error message:

The resize operation did not create enough free space for the installation.  Resizing may have failed.  You will have to set up partitions manually.

On that screen it showed the Linux OS having 132G 

I'm not sure how to resize manually.

Suggestions?

---

### Post by jtarin on 2010-09-04
Did you watch the video on that page I gave you the link too?

---

### Post by jtarin on 2010-09-04
Just leave the Windows partition alone and set you Ubuntu partition to be as big or as small as you want.It should be:Windows-------Ubuntu------Swap.Make the swap space about 1GB then adjust the Partition for Ubuntu the size you want.[Go here]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html")

---

### Post by jtarin on 2010-09-04
Now when you finish the install Ubuntu will not be bootable until you have configured EasyBCD

---

### Post by Sleven7 on 2010-09-04
I went back and watched the video on how to manually setup the partition several times and thought that I had it.  The video was on a drive that had nothing on it.  My drive already had 5 partitions and I wasn't sure how to proceed, so I went back and installed Ubuntu instead of Pinguy and the automatic install worked perfect.  EasyBCD was very easy to use  and now I have a very slick looking loader that works great.

I thought about it and the reason I wanted Pinguy was because it was Ubuntu with many bells and whistles already installed, but that kind of defeats the purpose of me learning about Linux and Ubuntu.  So I'm going to find the upgrades that Pinguy has and do it myself.  

Thanks again for all the help.

---

### Post by jtarin on 2010-09-04
Great you got something running. Once you  get your head wrapped around the dual boot concept and partitions it will be much easier. It's a difficult thing to visualize in the beginning. Now you can use the native loader of Windows and don't have to worry about both systems being down at once due to one loader. Now the next thing you should think about is a rescue plan and a backup plan for both OS's.

---

### Post by Sleven7 on 2010-09-05
Do you have a suggestion for a good back up program?

---

### Post by jtarin on 2010-09-05
I use Paragon Backup and Recovery Free Edition 10 Portable. I have it on a USB stick and boots from my computer. The only place I know of that you can get it now would be a torrent. [Here's a link to Google page with it listed]("http://www.google.com/webhp?hl=en#hl=en&q=Paragon+Backup+and+Recovery+10+Free+Edition+Portable.exe&aq=f&aqi=&aql=&oq=paragon+express+free&gs_rfai=&pbx=1&fp=5673716d440c1f33"). I don't do backups in the usual sense. I do a clean install then I make an image to use to restore. As I add software and make changes I will make another image to use to backup in the event of disaster.I normally keep about 4-5 images and rotate them out but always keeping the 1st clean install one. It takes about 20 minutes to restore my install.

---

### Post by Sleven7 on 2010-09-06
Is the software that Paragon is offering here,

[http://www.paragon-software.com/home/db-express/](http://www.paragon-software.com/home/db-express/)

different than the software you are using?

I looked at the link you gave me to Google and wanted to know more about the software, I found Paragon's website offering a backup and recovery program and was wondering what the difference was between the two.

Also another question, you said you use images to do your backup, do you use ISO images for the backup?

---

### Post by jtarin on 2010-09-06
Yea that should be good.Download it. That's got some new features!!!! I'm downloading it now. :)
> Also another question, you said you use images to do your backup, do you use ISO images for the backup?No images as in Norton Ghost, Windows Backup....etc....the Paragon Restore created backup image.

---

### Post by Sleven7 on 2011-01-24
Hey jtarin,

How have you been? Its been a while and I have often thought of you.  You were the first person to help me ease into Linux.  I've been meaning to come back and say thanks for all the help.

I migrated over to Mint for a while.  Since last speaking with you have over wrote my MBR 3 times, crippled it once, installed and played with dozens of distro, filled an entire album with live ISOs and a few days ago ended up re-installing Ubuntu 10.04 64bit.

The learning curve for Linux is steep and for a while I was wondering if I wasn't in over my head.  A few months ago it just started to click and everything seemed to make alot of sense. It was at that time that I realized that I had been trapped in a frontend gui called Windows since MS DOS 1.0 (yes, that long ago #-o ) Thanks for helping me see the light.

You were right, once I got the hang of using grub2 the installs became fun.  I now have 8 different OSs across 3 HDDs, Windows XP, 5 Linux OSs, and 2 BSD OSs,  fun fun.

I had to re-install Ubuntu because I want to help develop the Chromium OS and it uses 10.04 64B as a base. I found the live ISO for Chrome OS and as a browser OS its like driving a supped up Porsche with unlimited nitro. On youtube the videos instantly download and start playing.  It is amazing what happen when you dedicate an entire OS to the sole purpose of surfing the net.

Hope everything is going okay for you, how's the weather in Vladivostok this time of the year?

---

### Post by jtarin on 2011-01-25
> **Sleven7 said:**
> Hey jtarin,

How have you been? Its been a while and I have often thought of you.  You were the first person to help me ease into Linux.  I've been meaning to come back and say thanks for all the help.

I migrated over to Mint for a while.  Since last speaking with you have over wrote my MBR 3 times, crippled it once, installed and played with dozens of distro, filled an entire album with live ISOs and a few days ago ended up re-installing Ubuntu 10.04 64bit.

The learning curve for Linux is steep and for a while I was wondering if I wasn't in over my head.  A few months ago it just started to click and everything seemed to make alot of sense. It was at that time that I realized that I had been trapped in a frontend gui called Windows since MS DOS 1.0 (yes, that long ago #-o ) Thanks for helping me see the light.

You were right, once I got the hang of using grub2 the installs became fun.  I now have 8 different OSs across 3 HDDs, Windows XP, 5 Linux OSs, and 2 BSD OSs,  fun fun.

I had to re-install Ubuntu because I want to help develop the Chromium OS and it uses 10.04 64B as a base. I found the live ISO for Chrome OS and as a browser OS its like driving a supped up Porsche with unlimited nitro. On youtube the videos instantly download and start playing.  It is amazing what happen when you dedicate an entire OS to the sole purpose of surfing the net.

Hope everything is going okay for you, how's the weather in Vladivostok this time of the year?

Thank you for the kind words. :D
It's always a pleasure to see someone get their hands dirty and learn Linux. That's the only way to learn it...have no fear.:P Practice does lead us closer to perfecting our experience.
Interesting about the Chrome OS...where did you get the .iso? Link?

---

### Post by Sleven7 on 2011-01-25
I have had a lot of fun over the past few months, I'm not sure when it started to click but sure glad it did, the first two months were rough and scary.  You know what I think the hardest part was, picking up the new lingo.  It's so foreign to some one with only Windows experience and no nix system experience. Glad I persevered.

The addy for the Chrome OS is 

[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

Be prepared, that link leads to a server that gives you two options, paid high speed transfer, or a free 50KB/s transfer.
Took me 3 hours to get the ISO.  

It is also not the official Google Chrome OS, which is built with the Chromium OS on top of an Ubuntu 10.04 base, its the Chromium OS built on top of SUSE.  It is still very impressive to say the least.  

Another one you might want to try is Flow, a fork of the Chromium OS developed by a 17 year old Brit(goes by the name Hexxeh).  From what I've read he was able to implement Java support and release a distro before Google even started on Java support. Here the link to Flow.

[http://chromeos.hexxeh.net/](http://chromeos.hexxeh.net/)

After a few hours of working with Flow from a usb flash, I had it up and almost running right. For some reason it has some issues with anything Google related.  As opposed to the Chrome OS that just worked perfect out of the box.

It's good to hear from you again, let me know what you think of the Chrome OS.

---

