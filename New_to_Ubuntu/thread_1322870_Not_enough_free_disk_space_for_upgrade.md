---
title: "Not enough free disk space for upgrade"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Tony.B on 2009-11-11
Hello.  I've tried several times to upgrade from 9.04 to 9.10, but I always get the following message:

[INDENT]**Not enough free disk space**

The upgrade is now aborted. The upgrade needs a total of 1496M free space on disk '/'. Please free at least an additional 356M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'[/INDENT]

There is nothing in trash and I don't understand the instruction about removing temporary packages.

Can anybody help out please?

Thank & regards,
Tony

---

### Post by kansasnoob on 2009-11-11
Please post the full ouput from terminal of:

```
df -H
```

---

### Post by brujoand on 2009-11-11
if you go to Applications -> Assesories -> Terminal

And type in ```
 df -h 
``` what results do you get?

(like kansasnoob said :P )

---

### Post by Tony.B on 2009-11-11
Hello kansasnoob

I'm sorry I haven't the faintest idea what your message means.

---

### Post by brujoand on 2009-11-11
Tony, if you read my post, i tell you exactly how to do it :)

---

### Post by kansasnoob on 2009-11-11
Just curious how 9.04 is working for you?

---

### Post by Tony.B on 2009-11-11
Yes, GrimmVarg, you DID tell me EXACTLY how to do it. Thank You
And, kansasnoob, I find 9.04 really good. It's my first encounter with Ubuntu, and I certainly wouldn't ever again pay extra for a Windows-loaded computer.

OK here is what happened when in typed in "df -h":-

filesystem   size   used    avail    use%        mounted on
/host/ubuntu/disks/root-disk
             4.6G   3.3G     1.1G     76%
tmpfs        497M     0      497M      0%   /lib/inst/rw
varrun       497M   116K     497M      1%   /var/run
varlock      497M     0      497M      0%   /var/lock
udev         497M   152K     497M      1%   /dev
tmpfs        497M    84K     497M      1%   /dev/shm
/dev/sda2     32G    25G     6.8G     79%   /host
lrm          497M   2.2M     495M      1%   /lib/modules/2.6.28-16-generic/volatile
tony@ubuntu:~$

I typed all this in pretty columns, but I see when I previewed my work that the system doesn't follow my layout.  I hope it's not too confusing.

Does any of this help?
Cheers,
Tony

---

### Post by konqueror7 on 2009-11-11
try clearing up your apt-cache, open a terminal (Applications > Accessories > Terminal) and input the following,

```
sudo apt-get autoclean && sudo apt-get clean
```

you may also try the alternate disc, at least it won't download that much anymore space...

---

### Post by Tony.B on 2009-11-11
Hello konqueror7.

I typed in "sudo apt-get autoclean && sudo apt-get clean"
- and I got a message reading as follows:
[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Del google-chrome-unstable 4.0.222.5-r28804 [11.9MB]
Del google-chrome-unstable 4.0.223.11-r29900 [11.9MB]
tony@ubuntu:~$[/INDENT]

But I didn't understand the second part of your advice. What's an alternate disc?

Thanks,
Tony

---

### Post by konqueror7 on 2009-11-11
> **Tony.B said:**
> Hello konqueror7.

I typed in "sudo apt-get autoclean && sudo apt-get clean"
- and I got a message reading as follows:
[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Del google-chrome-unstable 4.0.222.5-r28804 [11.9MB]
Del google-chrome-unstable 4.0.223.11-r29900 [11.9MB]
tony@ubuntu:~$[/INDENT]

But I didn't understand the second part of your advice. What's an alternate disc?

Thanks,
Tony

seems only a few MB were in your cache. upgrading using the alternate disk is much easier since it is intended for computers without an internet connection. however, in your case, it can be used instead as a source (if your write the disk). this will save you more space as compared to downloading all update files on your harddisk, because all the data are in the CDROM.

---

### Post by pi.boy.travis on 2009-11-11
You can get the alternate disk image [here]("http://ubuntu.media.mit.edu/ubuntu-releases/karmic/ubuntu-9.10-alternate-i386.iso").  If you burn the disk, take it out, and then reinsert it, you should get a window asking you if you would like to perform an upgrade from the CD.  However, you must be aware that you have very little disk space left, and you still may not have enough room for the upgrade.  If that is the case, and you still insist on upgrading, I would back up all your data to an external hard disk and perform a clean install.

Good Luck!

---

### Post by kansasnoob on 2009-11-11
> **Tony.B said:**
> Yes, GrimmVarg, you DID tell me EXACTLY how to do it. Thank You
And, kansasnoob, I find 9.04 really good. It's my first encounter with Ubuntu, and I certainly wouldn't ever again pay extra for a Windows-loaded computer.

OK here is what happened when in typed in "df -h":-

filesystem   size   used    avail    use%        mounted on
/host/ubuntu/disks/root-disk
             4.6G   3.3G     1.1G     76%
tmpfs        497M     0      497M      0%   /lib/inst/rw
varrun       497M   116K     497M      1%   /var/run
varlock      497M     0      497M      0%   /var/lock
udev         497M   152K     497M      1%   /dev
tmpfs        497M    84K     497M      1%   /dev/shm
/dev/sda2     32G    25G     6.8G     79%   /host
lrm          497M   2.2M     495M      1%   /lib/modules/2.6.28-16-generic/volatile
tony@ubuntu:~$

I typed all this in pretty columns, but I see when I previewed my work that the system doesn't follow my layout.  I hope it's not too confusing.

Does any of this help?
Cheers,
Tony

You typed all of that?

In the future use copy-n-paste:

[http://www.ascentive.com/support/new/trouble_copypaste.phtml](http://www.ascentive.com/support/new/trouble_copypaste.phtml)

BTW see the slight differences between using a lower case vs. upper case H (a couple examples in bold):

> lance@lance-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             **8.2G**  3.3G  4.6G  42% /
udev                  **975M**  280K  975M   1% /dev
none                  975M  104K  975M   1% /dev/shm
none                  975M   88K  975M   1% /var/run
none                  975M     0  975M   0% /var/lock
none                  975M     0  975M   0% /lib/init/rw
/dev/sda10             16G  2.2G   13G  15% /home
lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda3              **8.8G**   3.5G   4.9G  42% /
udev                   **1.1G**   287k   1.1G   1% /dev
none                   1.1G   107k   1.1G   1% /dev/shm
none                   1.1G    91k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              17G   2.4G    14G  15% /home


Anyway, if 9.04 is working well for you I'd wait to upgrade. The problems for some have been pretty darn profound this time around.

---

### Post by hakeem09 on 2009-11-11
I have the same problem. I was wandering if I accidentally had  installed the HP restore Partion.

fatimah@fatimah-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              23G   21G  1.1G  96% /
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  204K  244M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  148K  244M   1% /dev
tmpfs                 245M  112K  244M   1% /dev/shm
lrm                   245M  2.2M  242M   1% /lib/modules/2.6.28-16-generic/volatile

---

### Post by Tony.B on 2009-11-12
> **kansasnoob said:**
> You typed all of that?

In the future use copy-n-paste

Yes. In fact I wrote it all out in longhand first so that I'd have something to refer to when I typed it.

Thanks for telling me about *Copy-n-Paste*.  There seem to be some big black holes in my computer knowledge: a product of being born a few decades too early.

Please accept my apologies for my ignorance.

Cheers,
Tony

---

### Post by s3a on 2009-11-12
Do:

```

sudo apt-get clean

```

then try upgrading again and see what happens.

---

### Post by Tony.B on 2009-11-12
Hi konqueror7 & pi.boy.travis

Sorry, I don't understand. What alternate disk?

---

### Post by Tony.B on 2009-11-12
> **kansasnoob said:**
> Anyway, if 9.04 is working well for you I'd wait to upgrade. The problems for some have been pretty darn profound this time around.

Now I'm really confused. I thought I had to have the latest version to get the best results. Is this a fallacy?

I'm sorry if I'm being a nuisance.

Cheers,
Tony

---

### Post by pi.boy.travis on 2009-11-12
OK, firstly, the alternate disk provides the packages that make up Ubuntu as a Debian repository on CD.  It contains all the package files you would download if you were upgrading.  The standard CD, or live CD you probably used has a working environment that is simply copied to the hard disk, while the alternate installer works by installing hundreds of packages that make up Ubuntu.  Just follow my earlier instructions and it should work.

Secondly, all versions of Ubuntu are supported for 18 months.  You could certainly continue to use 9.04 until 10.04 comes out.

---

### Post by Tony.B on 2009-11-12
Thank you very much, pi.boy.travis.

I *think* I understand.

Regards, Tony.

---

### Post by Tony.B on 2009-11-12
> **pi.boy.travis said:**
> ...However, you must be aware that you have very little disk space left, and you still may not have enough room for the upgrade...

Why have I very little disk space left?

Is this:
[INDENT](a) because my laptop was only fitted with a small disk?  - or
(b) because the disk was "partitioned" in the wrong place when I loaded Ubuntu 9.04?[/INDENT]

Is there anything I can do about either of these?

---

### Post by pi.boy.travis on 2009-11-12
> **Tony.B said:**
> Why have I very little disk space left?

Is this:
[INDENT](a) because my laptop was only fitted with a small disk?  - or
(b) because the disk was "partitioned" in the wrong place when I loaded Ubuntu 9.04?[/INDENT]

Is there anything I can do about either of these?

It is not likely that the installer made an error when partitioning your disk.  It usually does a fair job at ascertaining the optimal configuration. . . 

How big is your hard disk?  Is Ubuntu the only operating system, or are you dual-booting with windows?  Do you have any external hard drives, or other external media available to you?  Do you have a lot of extra applications, or even Firefox extensions for that matter?  How much of you person data is on the disk?  All of the factors contribute to disk usage.  We have all been in your situation at one point, scraping the bottom of the barrel for every last kilobyte.

How old is your laptop?  Do you have the means to purchase a new hard disk, install it, and move your data over to it?  If you do, we can help you get it partitioned and working with Ubuntu correctly.

Hope this helps!

---

### Post by Tony.B on 2009-11-13
Hello again pi.boy.travis.
Thank you for your help. I'll try to answer your questions in the order you asked them.

I'm not sure which of these numbers gives the size of my hard disk:
[LIST][*]Intel Celeron processor 550 (2.0 GHz, 533 MHz FSB, 1MB L2 cache)[*]Up to 252MB Mobile Intel Graphic Media Accelerator X3100[*]1GB DDR2[*]15.4" WXGA Acer CrystalBrite LCD (8ms/220-nit)[*]80GB HDD[*]DVD-Super Multi DL[*]802.11b/g WLAN[/LIST]

Windows Vista Basic is also loaded on this laptop. I installed Ubuntu 9.04 all by myself (and I'm very proud of this achievement).
I do not have any external hard drives, but I sometimes use a memory stick to copy documents.
I don't have any extensions that I'm aware of, and certainly not Firefox ones, except that I have downloaded and use Opera 10 browser.
I don't store any personal data anywhere on my laptop.
The laptop is about 18 months old, purchased in UK.
If I have to buy a new hard disk, I suppose I can afford it, but I prefer to use my pension for other necessities, like food. 
I would definitely need to get the supplier to install the hard disk for me!!!!
There's very little on the computer that I can't easily re-create, so I don't need to worry about moving data.

I hope all this makes sense.

---

### Post by 3rdalbum on 2009-11-13
> **Tony.B said:**
> Why have I very little disk space left?

Is this:
[INDENT](a) because my laptop was only fitted with a small disk?  - or
(b) because the disk was "partitioned" in the wrong place when I loaded Ubuntu 9.04?[/INDENT]

Is there anything I can do about either of these?

You installed Ubuntu by using the Windows-based installer, didn't you? (the program that you double-click in Windows, that lets you install Ubuntu without actually booting your computer up from the CD).

In that installer program, there is a popup menu that lets you choose how much disk space to allocate to Ubuntu. It looks like you might have left it at its default setting (4gb), which isn't really enough for Ubuntu.

The Windows-based installer does not actually do any partitioning - it merely creates a file on your Windows hard disk, installs Ubuntu into that, and then tells the Ubuntu bootloader where the file is. As a result, you can't actually resize the file that contains Ubuntu...

Your best bet is probably to use the Add/Remove Software program in Windows to 'remove' Ubuntu, and then boot up from the Ubuntu CD and install it that way, which will involve a spot of partitioning. Make sure all your data is backed up first, as a precaution. Also pay attention to the **two bar graphs** on the screen of the installer - when you elect to resize your existing Windows partition, you need to move the handle on the bottom bar graph to the left to allocate 10 gigabytes or more to Ubuntu.

---

### Post by egalvan on 2009-11-13
> **pi.boy.travis said:**
> 
Secondly, **all versions of Ubuntu are supported for 18 months**.  You could certainly continue to use 9.04 until 10.04 comes out.

Except for the Long Term Support versions of Ubuntu/Kubuntu/Xubuntu.

They are supported for 3 years on the Desktop
and 5 years on the Server.

8.04LTS Hardy Heron is a Long Term Support version,
and is used by many folks who prefer, or need, stability over "new" features.

Although some "new" features can mean support for your hardware.

You don't NEED the latest and greatest to have the "best" results.
The "best" result is a stable, properly working computer,
with all hardware working correctly,
and with the software that YOU need/want,
and that YOU are happy with.

It's all about choice, and the *nix world is filled with choices.

Ernest

P.S.
and yes, I use Hardy 8.04.3LTS on my main work machine.
It runs well, so I am happy.

I have a few other machines that I use to "play around" with different OS's.

---

### Post by pi.boy.travis on 2009-11-13
> **3rdalbum said:**
> You installed Ubuntu by using the Windows-based installer, didn't you? (the program that you double-click in Windows, that lets you install Ubuntu without actually booting your computer up from the CD).

In that installer program, there is a popup menu that lets you choose how much disk space to allocate to Ubuntu. It looks like you might have left it at its default setting (4gb), which isn't really enough for Ubuntu.

The Windows-based installer does not actually do any partitioning - it merely creates a file on your Windows hard disk, installs Ubuntu into that, and then tells the Ubuntu bootloader where the file is. As a result, you can't actually resize the file that contains Ubuntu...

Your best bet is probably to use the Add/Remove Software program in Windows to 'remove' Ubuntu, and then boot up from the Ubuntu CD and install it that way, which will involve a spot of partitioning. Make sure all your data is backed up first, as a precaution. Also pay attention to the **two bar graphs** on the screen of the installer - when you elect to resize your existing Windows partition, you need to move the handle on the bottom bar graph to the left to allocate 10 gigabytes or more to Ubuntu.

Good call, this is probably the case.  I would highly recommend you do a normal install, using the Ubuntu live CD.  [This guide]("https://help.ubuntu.com/community/Installation") may be of assistance. 

Good Luck

---

### Post by Tony.B on 2009-11-13
First of all, let me say how impressed I am with all this advice. Thank You.

Secondly, I can barely remember what I had for breakfast, let alone something I did on my computer a couple of months ago.  But, as I recall, to obtain Ubuntu, I googled Ubuntu in Windows Vista and found the website. There I was instructed to insert a blank CD in my laptop and download (I think you might call that *burning a CD* but I'm not absolutely sure of the terminology).

This CD was used to install Ubuntu on my laptop. At some point it may have asked if I wished to use default settings, to which my reply would certainly have been YES, since I realise I'm not capable of tinkering around with anything.

When I start up my laptop, I have the option of starting either Windows Vista OR Ubuntu. Is this relevant?

---

### Post by pi.boy.travis on 2009-11-13
> **Tony.B said:**
> First of all, let me say how impressed I am with all this advice. Thank You.

Secondly, I can barely remember what I had for breakfast, let alone something I did on my computer a couple of months ago.  But, as I recall, to obtain Ubuntu, I googled Ubuntu in Windows Vista and found the website. There I was instructed to insert a blank CD in my laptop and download (I think you might call that *burning a CD* but I'm not absolutely sure of the terminology).

This CD was used to install Ubuntu on my laptop. At some point it may have asked if I wished to use default settings, to which my reply would certainly have been YES, since I realise I'm not capable of tinkering around with anything.

When I start up my laptop, I have the option of starting either Windows Vista OR Ubuntu. Is this relevant?

Yes, this is good information.  Your hard disk is plenty big enough for the upgrade, your Ubuntu partition is just too small.  We can figure out the nature of your install, if you could provide us with a screen shot of your boot screen.  Any picture of the menu you see will suffice.

Good Luck

---

### Post by Tony.B on 2009-11-13
I know this is going to sound really dumb, but I have to ask these questions:
[INDENT]- What's a *boot screen?*
- How do I take a screen shot of it?[/INDENT]

Please accept my apologies for my ignorance.

---

### Post by pi.boy.travis on 2009-11-13
> **Tony.B said:**
> I know this is going to sound really dumb, but I have to ask these questions:
[INDENT]- What's a *boot screen?*
- How do I take a screen shot of it?[/INDENT]

Please accept my apologies for my ignorance.


The boot screen is the menu you use to select Windows or Ubuntu.  You could use boot chart, but, honestly, I usually just use my digital camera.

You could also use a program called bootchart, but it may be easier to just take a picture.

---

### Post by Tony.B on 2009-11-13
> **pi.boy.travis said:**
> The boot screen is the menu you use to select Windows or Ubuntu.  You could use boot chart, but, honestly, I usually just use my digital camera.

You could also use a program called bootchart, but it may be easier to just take a picture.

Mmm. The only digital camera I have is on my mobile phone. I took a photo of the page you suggested, but then I came across a problem:
I have no idea how to get that picture to you.

The photo consists entirely of words but my phone's screen is a bit small to read all of them, so I got a strong magnifying glass and can now type them here:

[B][INDENT][INDENT]Windows Boot Manager[/INDENT][/INDENT]

Choose an operating system to start, or press TAB to select a tool.
(Use the arrow keys to highlight your choice, then press ENTER.)

[INDENT]Microsoft Windows Vista
Ubuntu[/INDENT]

To specify an advance option for this choice, press F8
Seconds until the highlighted choice will be started automatically: 6


Tools[INDENT]Windows Memory Diagnostic[/INDENT]
ENTER=Choose.................TAB=Menu.................ESC=Cancel[/B]

I hope this gives you the correct information.
Regards,
Tony

---

### Post by pi.boy.travis on 2009-11-14
> **Tony.B said:**
> Mmm. The only digital camera I have is on my mobile phone. I took a photo of the page you suggested, but then I came across a problem:
I have no idea how to get that picture to you.

The photo consists entirely of words but my phone's screen is a bit small to read all of them, so I got a strong magnifying glass and can now type them here:

[B][INDENT][INDENT]Windows Boot Manager[/INDENT][/INDENT]

Choose an operating system to start, or press TAB to select a tool.
(Use the arrow keys to highlight your choice, then press ENTER.)

[INDENT]Microsoft Windows Vista
Ubuntu[/INDENT]

To specify an advance option for this choice, press F8
Seconds until the highlighted choice will be started automatically: 6


Tools[INDENT]Windows Memory Diagnostic[/INDENT]
ENTER=Choose.................TAB=Menu.................ESC=Cancel[/B]

I hope this gives you the correct information.
Regards,
Tony

Excellent, this is the info we needed.  Here is what I would recommend:

-Back up anything you aren't prepared to lose that is on the Ubuntu partition.  We are going to have to delete it, and you *will* lose *everything* that isn't backed up.  It might also be a good idea to back up any important data on your Windows partition as well, as we will be shrinking it.  IF any errors occur during that process, human or otherwise, you could potentially lose that data as well.  Do not panic, as the partitioning tools we will be using are tried and true, and very reliable.  However, an ounce of prevention is worth  pound of cure. . .  It may also be a good idea to defragment your Windows partition.  The less fragmented it is, the smaller the possibility of error.

-OK, after you have backed up all of your important data, boot into Windows and use the add/uninstall tool in the control panel to remove Ubuntu.  The uninstaller will ask you if you want to remove any cached data.  Answer yes.  After it is finished, remove the \ubuntu folder that may remain in your C: drive.

-Download the .iso for Ubntu 9.10, and burn it to a CD as you did before.

-Reboot with the disk in the drive.  You should see the Ubuntu LiveCD menu, at which you should choose the "Try Ubuntu" option, the first one on the list, and allow Ubuntu to boot until you reach the desktop

-At this point, check to make sure that all your hardware is working properly.  Your printer, WiFi ,webcam, or any other hardware you have, test it to make sure it is compatible with Ubuntu 9.10.  Normally hardware support improves with every release, however, regressions may occur.

-After confirming that all of your hardware is functioning properly, go ahead and start the installer.  The launcher should be on the desktop.  Proceed and answer all of the installer's questions.  When you get to the page regarding partitions, move the slider until the amount of space you want to allocate to Ubuntu is shown.  Make sure to leave enough room for Windows!  If it were me, I would probably give Ubuntu 20 GB of space, and leave 60GB for Windows.  Remember that when you install Ubuntu alongside Windows, you will be able to access all of the data on your Windows partition from Ubuntu.

-Confirm the calculated partitioning scheme, and enter your user data.  At the final page, confirm everything, and go make yourself a cup of coffee.  The LiveCD install usually takes about 30-45 minutes.

-When it is finished, reboot, and remove the CD when prompted.  After your computer boots up, you should see a menu similar to the one you saw earlier, asking if you want to boot into Ubuntu or Windows.  Boot into Ubuntu to ensure that everything is functioning properly.

-Next, boot into Windows.  Windows will want to check it's filesystem, as it's partition seems to have shrunk without it knowing!  After the check, confirm that everything is well in Windows world.

-Congratulations, you have successfully setup a dual-boot between Ubuntu and Windows.  If you have any other questions, do not hesitate to post. There are thousands of knowledgeable people on these forums, more than willing to answer any questions and help you through any problems you may have.

Sorry for my long-winded answer.  I hope it helps.

Good Luck.

---

### Post by Tony.B on 2009-11-15
> **pi.boy.travis said:**
> ... Sorry for my long-winded answer... 
This is amazing. I'm so impressed at the amount of time & trouble you've taken to help me. There's CERTAINLY no need to apologise.

I've written all your instructions out carefully & I'll be sure to follow them.

Just one quick question to satisfy my thirst for knowledge:
> **pi.boy.travis said:**
> ...When you get to the page regarding partitions, move the slider until the amount of space you want to allocate to Ubuntu is shown.  Make sure to leave enough room for Windows!  If it were me, I would probably give Ubuntu 20 GB of space, and leave 60GB for Windows...
What is the reason for the 20/60 split? Why not 40/40, or some other allocation?

But thank you so much once again for all the help.
**Now I know why it's called Ubuntu.**

Best regards,
Tony

---

### Post by KeithE4 on 2009-11-15
I have the same problem - my root partition is only 10 Gb, with 70 Gb in the /home partition.

I was able to free up almost 1 Gb by doing the following (as root):
1.  Move the /usr/src and /usr/local to /home/src and /home/local, respectively.
2.  Create symbolic links from /home/src to /usr/src and /home/local to /usr/local, respectively, by doing the following:
ln -s /home/src /usr/src
ln -s /home/local /usr/local

I learned this trick years ago, when I was using Slackware.  Of course, having a root partition that's big enough is a better solution. :biggrin:

---

### Post by Tony.B on 2009-11-15
Thanks for your input, KeithE4, although that all sounds a bit too technical for the likes of an old wrinkly like me.
I'm part way through now, following the instructions religiously. I've deleted the old Ubuntu 9.04 and am slowly, very slowly, downloading 9.10.
I had forgotten how slowly my laptop boots [if that's the right word] Windows Vista compared with the high-speed Ubuntu.
This forum post is via my mobile phone using Opera Mini.
Thanks for your contribution.
Regards, 
Tony

---

### Post by ????123856 on 2009-11-15
Boot into CD and select 'Try Ubuntu without making any changes to your computer.' Then launch a terminal from accersoirs and use the command ```
 'sudo apt-get clean'
```

---

### Post by Tony.B on 2009-11-15
> **????123856 said:**
> Boot into CD and select 'Try Ubuntu without making any changes to your computer.' Then launch a terminal from accersoirs and use the command ```
 'sudo apt-get clean'
```

Thanks for your input, ????123856, but I think that may have been covered earlier by post #8 of this thread.

---

### Post by pi.boy.travis on 2009-11-15
> **Tony.B said:**
> This is amazing. I'm so impressed at the amount of time & trouble you've taken to help me. There's CERTAINLY no need to apologise.

I've written all your instructions out carefully & I'll be sure to follow them.

Just one quick question to satisfy my thirst for knowledge:

What is the reason for the 20/60 split? Why not 40/40, or some other allocation?

But thank you so much once again for all the help.
**Now I know why it's called Ubuntu.**

Best regards,
TonyT

The 20/60 split is just a guess, as coming up with a partitioning scheme is more art then science.  In a dual boot configuration, it is usually judicious to give Windows more space than Ubuntu.  This is because Ubuntu can easily access the files on your Windows partition, while it is significantly more difficult to get Windows to read the data on the Ubuntu partition.  I dual-booted for my first year with Linux, during which I kept all my personal files on the Windows partition, and accessed them with Ubuntu.  As I became more accustomed to Ubuntu, I used Windows less and less, until I got to the point when I felt that I could go on without it.  I've been Microsoft free for three years now, and I've never looked back.

I'm glad that I was able to help, as providing support is my favorite way to give back to the Ubuntu community.

Thanks, and good luck!

---

### Post by Tony.B on 2009-11-16
It didn't work.
I'm posting this from Windows (my apologies if that's blasphemy).

I inserted the new CD in my disc drive and re-started my computer in Windows (because Ubuntu had already been deleted), but I didn't get get any message saying *Ubuntu Live CD Menu*, or anything similar.

So I tried to sort it out myself - always a dangerous option where I'm concerned!

I went to *Computer* and opened up the CD drive, which gave me 3 options:
[INDENT]**Demo and full installation**  Try Ubuntu without installing...
**Install inside Windows**  Install and uninstall like any other app...
**Learn more**...[/INDENT]

The first option seemed to be the only one which would be any use, so I selected it and got another 3 choices which basically said:
[INDENT](a) leave the CD in the drive, reboot & it'll automatically start
(b) sort it out later
(c) use the CD boot helper[/INDENT]

I tried the first alternative, but it didn't work, nothing happened. So I used the CD boot helper and everything seemed to be going OK except that there was no option to move the partition as I was expecting.

When I re-booted, I found that I now had a choice between Windows & Ubuntu, so I selected Ubuntu *(of course):*
[INDENT]I got a message saying *Completing the Ubuntu installation* which looked promising.
Then I got the Ubuntu logo in monochrome for about 90 secs.
Then I got the following message, repeated 43 times:
[INDENT]/init: line1: can't open /dev/sr0: No medium found[/INDENT]
- followed by these next words
[INDENT]BusyBox v1.13.13 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initranfs) Unable to find a medium containing a live file system[/INDENT][/INDENT]

Then I found I couldn't switch off my computer except by Control+Alt+Delete.

Should I try to sort it out from this point, or would it be better to start again?

---

### Post by pi.boy.travis on 2009-11-16
> **Tony.B said:**
> It didn't work.
I'm posting this from Windows (my apologies if that's blasphemy).

I inserted the new CD in my disc drive and re-started my computer in Windows (because Ubuntu had already been deleted), but I didn't get get any message saying *Ubuntu Live CD Menu*, or anything similar.

So I tried to sort it out myself - always a dangerous option where I'm concerned!

I went to *Computer* and opened up the CD drive, which gave me 3 options:
[INDENT]**Demo and full installation**  Try Ubuntu without installing...
**Install inside Windows**  Install and uninstall like any other app...
**Learn more**...[/INDENT]

The first option seemed to be the only one which would be any use, so I selected it and got another 3 choices which basically said:
[INDENT](a) leave the CD in the drive, reboot & it'll automatically start
(b) sort it out later
(c) use the CD boot helper[/INDENT]

I tried the first alternative, but it didn't work, nothing happened. So I used the CD boot helper and everything seemed to be going OK except that there was no option to move the partition as I was expecting.

When I re-booted, I found that I now had a choice between Windows & Ubuntu, so I selected Ubuntu *(of course):*
[INDENT]I got a message saying *Completing the Ubuntu installation* which looked promising.
Then I got the Ubuntu logo in monochrome for about 90 secs.
Then I got the following message, repeated 43 times:
[INDENT]/init: line1: can't open /dev/sr0: No medium found[/INDENT]
- followed by these next words
[INDENT]BusyBox v1.13.13 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initranfs) Unable to find a medium containing a live file system[/INDENT][/INDENT]

Then I found I couldn't switch off my computer except by Control+Alt+Delete.

Should I try to sort it out from this point, or would it be better to start again?

OK, here is what happened.  Your BIOS is not configured to boot from the CD.  That is why you did not see the Ubuntu LiveCD menu.  Then the CD boot manager tried to reinstate the wubi boot manager we deleted earlier.  *That* boot manager then tried to boot from the Ubuntu partition we deleted, explaining your BusyBox shell.  Wubi is the Windows-based Ubuntu installer.

The BIOS (Basic Input Output System) is a small chip on your motherboard that is the first thing to "come alive" when you start up your computer.  The BIOS is responsible for loading the operating system into the system memory, after which it hands control over to the OS.

When you first start up your computer, you should see a BIOS splash screen displaying either your motherboard's manufacturer, or your computer vendor's (ie, Dell) Logo.  You should also see some text that will say something like: "press F12 to enter setup."  Unfortunately, I can't provide you with specific instructions, as the BIOS differs from computer to computer.  You should be able to find out what key you have to press, and then hit it right as your computer is starting up.  You will then get a scary looking text based menu system that will let you set the BIOS options.  You will need to find something along the lines of "Boot device priority, Boot device order, Boot order configuration, etc.  You BIOS setup screen should provide you with a key somewhere that will tell you what key does what.  Make sure to be careful and take your time.  The ultimate goal is to setup the BIOS such that it boots from the CD *first*, and then your internal hard disk.

After that, boot into Windows again, and run the Windows Ubuntu uninstaller again, just to make sure that the wubi boot loader is gone.  Make sure to delete the \ubuntu folder on your C: drive if it remains.

If all goes well, you should be able to boot from the CD, and pick up where you left off.  If not, let us know what the situation is and we should be able to help you through any adversity.

Sorry it didn't work right off the bat.  Most people encounter a problem like this and then give up on linux. . . 

Good Luck!

---

### Post by Tony.B on 2009-11-17
Thank you yet again for your patience.

I've again deleted the Ubuntu file, but I couldn't find anything in C drive about any \ubuntu folder, so I continued with rest of your instructions.

In my case it is *Press F2 to enter set-up* which took me to a screen titled *InsydeH20 Setup Utility*, which has 5 page headings, *Information, Main, Security, Boot, Exit*.

I selected *Boot* which gave me the following screen:
[INDENT]**Boot Priority Order**
1. IDE0:  TOSHIBA MK8046GSX
2. IDE1:  PIONEER DVD-RW DVRKD08RS
3. USB FDD:
4. Network Boot:  MBAv10.0.9 Slot 0500
5. USB HDD:
6. USB CDROM:[/INDENT]

There are also instructions to change the order of these.

I tried swapping 5 & 6 around, as this seemed the most logical to me, and re-booted with the CD in the disk drive. But it didn't make any difference, so I've changed 5 & 6 back again.

What did I do wrong?

Regards, Tony
PS: Thank you so much for the assistance I'm getting. One day I hope to be in a position to offer help to others (provided they are totally hopeless, of course).

---

### Post by pi.boy.travis on 2009-11-17
> **Tony.B said:**
> Thank you yet again for your patience.

I've again deleted the Ubuntu file, but I couldn't find anything in C drive about any \ubuntu folder, so I continued with rest of your instructions.

In my case it is *Press F2 to enter set-up* which took me to a screen titled *InsydeH20 Setup Utility*, which has 5 page headings, *Information, Main, Security, Boot, Exit*.

I selected *Boot* which gave me the following screen:
[INDENT]**Boot Priority Order**
1. IDE0:  TOSHIBA MK8046GSX
2. IDE1:  PIONEER DVD-RW DVRKD08RS
3. USB FDD:
4. Network Boot:  MBAv10.0.9 Slot 0500
5. USB HDD:
6. USB CDROM:[/INDENT]

There are also instructions to change the order of these.

I tried swapping 5 & 6 around, as this seemed the most logical to me, and re-booted with the CD in the disk drive. But it didn't make any difference, so I've changed 5 & 6 back again.

What did I do wrong?

Regards, Tony
PS: Thank you so much for the assistance I'm getting. One day I hope to be in a position to offer help to others (provided they are totally hopeless, of course).

I think the thing to do would be to swap 1 & 2, as long as the CD is in your computer's built-in CD drive, and not an external drive.  That should do the trick!

---

### Post by Tony.B on 2009-11-17
It all looks good so far, but I've got a query. I'm at Prepare Disk Space (Step 4 on Install). Screen options are:
- install side by side (Default option)
- erase and use entire disk (Which I DON'T want - not brave enough)
- specify partitions manually.
I looked at that option, but the next screen terrified me, so I've come back to the options. 
What should I do now, please. 
This is being laboriously typed on my cellphone, as I don't wish to muck up what I've already started, so please excuse poor typing.

---

### Post by Tony.B on 2009-11-17
Maybe I should add that the Prepare Disk Space page starts by saying 
** This computer has several operating systems on it:**
- Windows Vista (loader) (/dev/sdal1) 11.7 GB
- Windows Vista (loader) (/dev/sda2) 31.5 GB
- /dev/sda3 31.3 GB

---

### Post by 23dornot23d on 2009-11-17
Its been an hour since anybody was last here ...... so .......

  3 ............. choices ...... 

______________________________________________

1... back out now ...... 

or 

2 ... continue ...... when the original person returns

3 .... have a go ..... and take the consequences if they arise .........

___________________________________________

1.

If you back out now ....... no real harm done and you can check this video out

How to install linux in 5 mins and it explains the part you are coming up to


[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)



because this may be the hardest bit .....

____________________________________________________________


2....... wait till the original person comes back ............ pi.boy.travis


____________________________________________________________

Then there is a 3rd option ......... 


  There are a few steps to this but its easier once you watch the video and see
what happens here ...... you can skip the first half as its about burning the disk
and you have already done this part ..........

Then you can continue ....... 

I would set it up like this ....... 

I personally would back out watch the video  ....... 

and read about what you need to do on the web and some of the problems encountered .......  

You have the boot CD and by setting the BIOS to boot from CD Which I believe you
have already setup  ......... this ensures that you can always bring ..............
UBUNTU 9.10 back up using the CD ............. 


and your System has 1 Gig mem

I'm not sure which of these numbers gives the size of my hard disk:
[LIST]
[*]Intel Celeron processor 550 (2.0 GHz, 533 MHz FSB, 1MB L2 cache) ..... CPU
[*]Up to 252MB Mobile Intel Graphic Media Accelerator X3100
[*]1GB DDR2 .............................................................. This is your Memory
[*]15.4" WXGA Acer CrystalBrite LCD (8ms/220-nit)
[*]80GB HDD ............................................................... This is your Hard Drive
[*]DVD-Super Multi DL
[*]802.11b/g WLAN ....................................................... This is Your WIFI ...
[/LIST]


__________________________________________________________________

The option that keeps your data safer for future upgrades is to do it something like this.

( with a /home ........partition )

Which means splitting the  .... sda3 ....... partition into 3 parts .....

/       .......... root partition as ext4 ............... 10 Gig

/swap .........                    as swap ..............        1 Gig (this could be larger but reading above it should be ok)
..............     [ More info on swap space required here .... ] [http://ubuntuforums.org/showthread.php?t=446813](http://ubuntuforums.org/showthread.php?t=446813)

/home ..........                   as ext4 ..............   19 Gig      basically this last part is whats left

_____________________________________________________________

I did a upgrade on my own system and kept the partitions as ext3 .....
and I do not have the new boot loader installed ...... GRUB2

I have no problems ....... on my system ...... 

But I am reading about quite a few problems with the new grub2 and 
some problems with ext4 .......   

This could turn out to be a longer journey than you expect .......

But I am letting you know all the facts first ,,,,,,,,,,

It could run smoothly ,,,,,,,,, we would hope ..... as was said earlier .... 

Backup all valuable DATA ...... before doing this ,,,,,,,,,,,

---

### Post by pi.boy.travis on 2009-11-17
> **Tony.B said:**
> Maybe I should add that the Prepare Disk Space page starts by saying 
** This computer has several operating systems on it:**
- Windows Vista (loader) (/dev/sdal1) 11.7 GB
- Windows Vista (loader) (/dev/sda2) 31.5 GB
- /dev/sda3 31.3 GB

Hmm. . .  I'm curious as to what is on the partition /dev/sda3. . .  I haven't used Windows in a while, does that partition belong to Windows?

If you aren't sure, I would boot back into Windows, and go into My Computer, or whatever it is called now.  How many drives do you see?  What are their labels?  What letters are they assigned?

If you are sure that partition had nothing to do with Windows, the I would reboot the Ubuntu LiveCD, and choose the first option again, to try without installing.  Then, go to System > Administration > Partition manager.  This should open up gParted, the manual partitioning tool used by Ubuntu.  Using gParted, delete that third /dev/sda3 partition, and click apply.  Make sure to be careful, you wouldn't want to accidentally delete your Windows partition!  When you are ready, click "Apply."  Then, reboot the Ubuntu LiveCD and start the installer as you did before.  Then, when you get to the partitioning stage, select the option entitled "Install Ubuntu in largest continuous free space."  That should do the trick!

Good Luck!

---

### Post by Tony.B on 2009-11-17
Thank you very much, 23dornot23d.

I tried watching the video as you suggested, but unfortunately neither the visuals nor the sound were clear enough for me to follow the instructions.  I know how to increase the volume & the screen size, but that didn't help, so it could be due to an age thing on my part.

There is a 4th Option, of course.  I could always follow the default choice and install Ubuntu with their recommended partition, which I *think* is 15.5GB (if my memory serves me well, but bear in mind the possibility that I may be going senile). 

Thanks, too, for clarifying the meaning of all those confusing specifications about memory, hard drives, wi-fi, etc.

Cheers,
Tony

---

### Post by pi.boy.travis on 2009-11-17
> **23dornot23d said:**
> Its been an hour since anybody was last here ...... so .......

  3 ............. choices ...... 

______________________________________________

1... back out now ...... 

or 

2 ... continue ...... when the original person returns

3 .... have a go ..... and take the consequences if they arise .........

___________________________________________

1.

If you back out now ....... no real harm done and you can check this video out

How to install linux in 5 mins and it explains the part you are coming up to


[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)



because this may be the hardest bit .....

____________________________________________________________


2....... wait till the original person comes back ............ pi.boy.travis


____________________________________________________________

Then there is a 3rd option ......... 


  There are a few steps to this but its easier once you watch the video and see
what happens here ...... you can skip the first half as its about burning the disk
and you have already done this part ..........

Then you can continue ....... 

I would set it up like this ....... 

I personally would back out watch the video  ....... 

and read about what you need to do on the web and some of the problems encountered .......  

You have the boot CD and by setting the BIOS to boot from CD Which I believe you
have already setup  ......... this ensures that you can always bring ..............
UBUNTU 9.10 back up using the CD ............. 


and your System has 1 Gig mem

I'm not sure which of these numbers gives the size of my hard disk:
[LIST]
[*]Intel Celeron processor 550 (2.0 GHz, 533 MHz FSB, 1MB L2 cache) ..... CPU
[*]Up to 252MB Mobile Intel Graphic Media Accelerator X3100
[*]1GB DDR2 .............................................................. This is your Memory
[*]15.4" WXGA Acer CrystalBrite LCD (8ms/220-nit)
[*]80GB HDD ............................................................... This is your Hard Drive
[*]DVD-Super Multi DL
[*]802.11b/g WLAN ....................................................... This is Your WIFI ...
[/LIST]


__________________________________________________________________

The option that keeps your data safer for future upgrades is to do it something like this.

( with a /home ........partition )

Which means splitting the  .... sda3 ....... partition into 3 parts .....

/       .......... root partition as ext4 ............... 10 Gig

/swap .........                    as swap ..............        1 Gig (this could be larger but reading above it should be ok)
..............     [ More info on swap space required here .... ] [http://ubuntuforums.org/showthread.php?t=446813](http://ubuntuforums.org/showthread.php?t=446813)

/home ..........                   as ext4 ..............   19 Gig      basically this last part is whats left

_____________________________________________________________

I did a upgrade on my own system and kept the partitions as ext3 .....
and I do not have the new boot loader installed ...... GRUB2

I have no problems ....... on my system ...... 

But I am reading about quite a few problems with the new grub2 and 
some problems with ext4 .......   

This could turn out to be a longer journey than you expect .......

But I am letting you know all the facts first ,,,,,,,,,,

It could run smoothly ,,,,,,,,, we would hope ..... as was said earlier .... 

Backup all valuable DATA ...... before doing this ,,,,,,,,,,,

We should not advise a new user to manually calculate and setup a separate /home partition on their first time.  We can cross that bridge when we get there.  That said, it would be nice if a separate /home partition was the default. . . 

Secondly, The OP has no free space with which to work with, because of /dev/sda3.  It very well may be a data partition for Windows.

Some people will always have problems with new bootloaders and filesystems, and it is the negative experiences that receive the most attention.  I run 2 web servers, a squid reverse proxy, a samba server, a router running Ubuntu, a mysql database server, and an FTP server, and none have had any problems, even after a power failure.  Neither did any of my other computers or my client's computers.  While I would be hesitant to use ext4 in a production environment, I have experienced no issues so far.

---

### Post by Tony.B on 2009-11-17
> **pi.boy.travis said:**
> ...go into My Computer, or whatever it is called now.  How many drives do you see?  What are their labels?  What letters are they assigned?...
I found the following details:
[INDENT]ACER (C:) Local Disk  Total Size: 31.5GB, Free Space: 7.10GB
DATA (D:) Local Disk  Total Size: 31.3GB, Free Space: 31.2GB
DVD RW Drive (E:) CD Drive *no further details - no disc inserted*[/INDENT]


> If you are sure that partition had nothing to do with Windows...
Given my ineptitude where computers are concerned, this would be a dangerous assumption, and I don't think I can rely on it.

Thanks,
Tony

PS When I previewed this post, I got some smiley faces. If they are still there, please note that I typed **:** followed by **)**. I hope you can understand this.

---

### Post by 23dornot23d on 2009-11-17
> **Tony.B said:**
> Thank you very much, 23dornot23d.

I tried watching the video as you suggested, but unfortunately neither the visuals nor the sound were clear enough for me to follow the instructions.  I know how to increase the volume & the screen size, but that didn't help, so it could be due to an age thing on my part.

There is a 4th Option, of course.  I could always follow the default choice and install Ubuntu with their recommended partition, which I *think* is 15.5GB (if my memory serves me well, but bear in mind the possibility that I may be going senile). 

Thanks, too, for clarifying the meaning of all those confusing specifications about memory, hard drives, wi-fi, etc.

Cheers,
Tony


Cheers Tony ......

I try to help when I can ...... but you appear to be right about option 4 ......

and PI BOY was right .... in getting you to check it ....

Looks like sda3  is your D: drive .......... and although it has hardly been used ,,,,,

It is a necessary to have some of it .....

It can possibly be resized to 10 gig or less ..... leaving you 20 gig or more ....... for UBUNTU

( That is why it probably recommended 15 Gig ,,,, its split the space in half and left 15 Gig for windows )

________________________________________________

I only jumped in earlier because .....  

I thought you had been left hanging ....

I won't hijack the thread now he has returned ,,,,,,

________________________________________________

He has more equipment than me ..... so he probably knows more too .....

It sounds like it all runs very well ..... but I am glad he has some concerns over ext4

I too am getting on in years ,,,,, so its nice to learn ..... a bit .... ;)

Best of luck with whatever you should choose to do .......

Oh I also agree with the /home drive ..... Mandriva auto assigns these 3 partitions

,,,,,,,,,,,,,,,,  root   ( / ) ......( swap ) and  ( /home )

It could be a thought for UBUNTU to incorporate this too .......... 

saves on the manual calcs .... although I can still do that occasionally for others .....

---

### Post by Tony.B on 2009-11-17
Hi 23dornot23d,

Gosh! I didn't know it is possible to "hijack" a thread. I thought a forum was an opportunity for open discussion, but maybe that's something *else* I've got to learn.

I'm overwhelmed with the help and goodwill shown on this forum. So thank you for your input too.

I agree, though, that pi.boy.travis has really gone the extra mile. Out of courtesy to him, maybe I should await his advice.

Cheers,
Tony

---

### Post by pi.boy.travis on 2009-11-17
> **Tony.B said:**
> I found the following details:
[INDENT]ACER (C:) Local Disk  Total Size: 31.5GB, Free Space: 7.10GB
DATA (D:) Local Disk  Total Size: 31.3GB, Free Space: 31.2GB
DVD RW Drive (E:) CD Drive *no further details - no disc inserted*[/INDENT]



Given my ineptitude where computers are concerned, this would be a dangerous assumption, and I don't think I can rely on it.

Thanks,
Tony

PS When I previewed this post, I got some smiley faces. If they are still there, please note that I typed **:** followed by **)**. I hope you can understand this.

Hmm. . . that is interesting.  It would not be wise to delete any of these three partitions. . . Here is what I would do:

Boot into the Ubuntu LiveCD, and go to System > Administration > GParted.  It might also be called partition manager, it's just that it's called GParted in the netbook interface I am using. . . 

This should bring up a graphical diagram of the three partitions, showing their size, position, and space used.  The GParted UI is pretty simple, just click on the partition you want to edit and strech/slide it around.  The ultimate goal is to get 10-20 GB of free, non-partitioned free space at the end (right hand side) of the diagram.  *Don't* create a new partition there just yet, just leave the space unpartitioned.  Again, be very careful.  When you are finished, click apply.  (I'll do some googling and see if I can't find a screenshot or short video to help explain this procedure better. . . )

After GParted finishes, reboot yet again, and start the installer.  Once you get to the partitioning stage, choose to install Ubuntu "in the largest continuous free space."

Hope this helps, and god luck!

---

### Post by Tony.B on 2009-11-18
Yes. It's called GParted.
That gives me 7 columns headed Partition - File System - Label - Size - Used - Unused - Flags.
There are 3 rows of info. Only the second partition, /dev/sda2, has an entry under flags and it says "boot". I think we're more interested in the 3rd partition which reads /dev/sda3 - ntfs - data - 31.30 GiB - 3 GiB - 28.30 GiB.
Quite honestly, I'm very scared of fiddling with this - I'm way out of my comfort zone.

---

### Post by Tony.B on 2009-11-18
Hello again.

I'm sorry to present another query - it's just that I'm very scared of making an irreversible mistake:

> **pi.boy.travis said:**
> ...The ultimate goal is to get 10-20 GB of free, non-partitioned free space at the end (right hand side) of the diagram.  *Don't* create a new partition there just yet, just leave the space unpartitioned.  Again, be very careful...

I followed the instructions very carefully and tried to adjust /dev/sda3. But the partition didn't give me non-partitioned free space* at the end (right-hand side) of the diagram.* The new area I created occurred *before* /dev/sda3. 

Also, a note came up which read:
**Move /dev/sda3 to the right & shrink it from 31.30 GiB to 11.77 GiB**

Also the list showed the new area in between /dev/sda2 & /dev/sda3 and had the following details:
Partition *unallocated*
File System *unallocated*
Label (field left blank0
Size *19.54 GiB*
Used -
Unused -
Flags (field left blank)

I was not at all confident that I'd done the right thing, so, mindful of the warning to take care, I** undid** this action and shut down GParted.

Can someone please tell me what I did wrong?

Thanks,
Tony

---

### Post by pi.boy.travis on 2009-11-18
> **Tony.B said:**
> Hello again.

I'm sorry to present another query - it's just that I'm very scared of making an irreversible mistake:



I followed the instructions very carefully and tried to adjust /dev/sda3. But the partition didn't give me non-partitioned free space* at the end (right-hand side) of the diagram.* The new area I created occurred *before* /dev/sda3. 

Also, a note came up which read:
**Move /dev/sda3 to the right & shrink it from 31.30 GiB to 11.77 GiB**

Also the list showed the new area in between /dev/sda2 & /dev/sda3 and had the following details:
Partition *unallocated*
File System *unallocated*
Label (field left blank0
Size *19.54 GiB*
Used -
Unused -
Flags (field left blank)

I was not at all confident that I'd done the right thing, so, mindful of the warning to take care, I** undid** this action and shut down GParted.

Can someone please tell me what I did wrong?

Thanks,
Tony

It would seem from your description that you are almost there.  You  would have successfully shrunk the partitions, now you just have to drag them all to the left, so the 19 GB of free space you created is all at the right.  If you grab the box that represents a partition in the middle, you should be able to drag it around.  Keep the partitions in the same order, just make sure there isn't any unpartitioned space between them.

There is little to worry about, you are doing fine.  Just take your time, and ask any questions you have.  There is no stupid question, and we were all in the same situation at one time.

I hope this helps, and good luck!

---

### Post by 23dornot23d on 2009-11-18
**[quote]**

 I** undid** this action and shut down GParted.

**[quote]**

_____________________________________________________________

Seeing that you have not done this step yet ............

When you **DO RESIZE** this partition using GPARTED ,,,,,,,

**You can resize the partition from either .... side** ...... but I advise to do it from the **right** ...... 

If when you do this again ........ you use the mouse ..... and slide it from


Right to Left  ( when  doing the resize operation ,,,,,, )

it will leave the space that you require for UBUNTU at the right hand side

______________________________________________________________

I will post a screen shot here ..... to help .........

It should look similar to this .... obviously your sizes are different ..... 

but the Black Arrows at each end slide using the mouse ....... 

and the device in this top brown bar will read   **  /dev/sda3 **

[IMG]http://www.dedoimedo.com/images/computers/2009/gparted-resize.png[/IMG]


Free Space Preceding ...... will be ............ 0 .......... the same as shown above ....

New Size in MB ............... will be somewhere near to ........... 11,770 ..... 
[B]
I used this figure as this was what you had written earlier 11,77 Gig ...... * ( This will be the size of the Windows D drive )[/B]

The Free space it will calculate to whatever is left ..............




Once you have completed these operations ....... and applied it ...... it will take a short time to resize and set it up
as you have very little DATA on there ...........
_________________________
Check first with Pi.Boy.Travis

Hopefully ...... he too agrees with this ...........  method ..... 

As its the same as how he explained it earlier 

**[ Quote ]**

This should bring up a graphical diagram of the three partitions, showing their size, position, and space used. The GParted UI is pretty simple, just click on the partition you want to edit and strech/slide it around. The ultimate goal is to get 10-20 GB of free, non-partitioned free space at the end (**right hand side**) of the diagram. *Don't* create a new partition there just yet, just leave the space unpartitioned. Again, be very careful. When you are finished, click apply. 
(I'll do some googling and see if I can't find a screenshot or short video to help explain this procedure better. . . )

**[ Quote ]**

So I have added here a part of the information ...... that you were looking for .... I hope it helps ........
__________________________________________________


I thought it best to join in again - just to clarify this ........

and thinking that this information might come in helpful ............ and hopefully remove some worries

______________________________________________________________________________________

All's well that ends well ..... and there is nothing at all wrong with what you did do / have done ...... 

or ( are about to do .... in this operation ..... as long as the disk has no errors on it everything should go well  )


_______________________________________________________________________________________

* This message is fine too ................................. and it will come up with a message like this again ...........
as you said ...........Also, a note came up which read:
**Move /dev/sda3 to the right & shrink it from 31.30 GiB to 11.77 GiB**

---

### Post by Tony.B on 2009-11-19
I have done it.
I HAVE DONE IT.
**I HAVE  DONE IT.**

Thanks to everybody for their patience, especially pi.boy.travis.

I feel like a contestant on *"Who Wants To Be A Millionaire?"*.[INDENT]- I've asked the audience
- I've phoned a friend (well almost!)
- And I've done 50/50 (actually 20/60).[/INDENT]As I'm almost an expert now, anybody got any questions? !!!

Thanks so much once again.
Cheers,
Tony

---

### Post by 23dornot23d on 2009-11-19
Excellent Result .......... well done ........ and welcome to UBUNTU 9.10

Tony .....

---

