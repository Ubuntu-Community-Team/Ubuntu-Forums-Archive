---
title: "Screen resolution - at wits end!"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by cooperman411 on 2008-12-18
Hey all!

I'm new to Linux in general and Ubuntu specifically.  Used RedHat briefly several years ago and only for internet access.

I installed Ubuntu on my Averatec 3715-ED1 laptop.  The video card is VIA S3G UniChrome Pro IGP with 1024x768 XGA resolution.  

When I tried installing Ubuntu it would freeze.  I switched to Safe Graphics Mode and it installed.  The problem is I have a max resolution of 800x600.  I have read a zillion forums and tried to go into Terminal.  I've followed a step-by-step howto on YouTube even.  I typed what the pro typed and when he hit enter he got a screen full of editable text and I got a blank white terminal screen.

I then tried other distributions: Simplis, Xubuntu, Kubuntu, and am going to try Mint next.  I didn't install them -- I just tried launching from the CD/DVD.

I did get a bit further on Kubuntu.  It at least got to a screen showing 1024x768 however it froze.

Any help appreciated.  Keep in mind I'm very much a newbie.

---

### Post by cooperman411 on 2008-12-18
So I found this: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

and ran this command in the Terminal:
 sudo apt-get install xserver-xorg-video-openchrome 

It installed successfully BUT I still just have 800x600 resolution.

Now what?  I rebooted.  I checked the System>Administration>Hardware Drivers and didn't see anything.  

Thanks again in advance!

---

### Post by mapes12 on 2008-12-19
If you're running 8.10 that could be your problem. I followed many threads and the general feedback is that 8.10 has many screen res issues. Previously, editing the xorg.conf file would fix things (/etc/X11/xorg.conf) but in 8.10 this makes little difference. This is because there appears to be a newer version of the X server deployed in 8.10 that tries to do things automatically.

In the end I solved the problem by installing 8.04LTS where manual configuration is still possible. 

If you do install 8.04 and you need to change your screen res settings then right click **Applications** select **Edit Menu**. When the GUI pops up select **Other** in the L/H column then select **Screen and Graphics** in the R/H column. **Close**. You should then be able to go **Applications>Other>Screen and Graphics** to manually set what you want. Your machine may require a restart first though.

That fixed it for me.

8.04 is supported up to April 2011 whereas 8.10 is only supported to April 2010.

---

### Post by cooperman411 on 2008-12-19
Thanks so much!  I think I understood all that.

Next quick question -- can I install 8.04 from the web/download directly or do I have to create a new install CD?  Also, can I install it without writing over the documents/music/photos I've put on here since installing 8.10?

Thanks again!

---

### Post by SunnyRabbiera on 2008-12-19
> **cooperman411 said:**
> Thanks so much!  I think I understood all that.

Next quick question -- can I install 8.04 from the web/download directly or do I have to create a new install CD?  Also, can I install it without writing over the documents/music/photos I've put on here since installing 8.10?

Thanks again!

I suggest backing everything up, its not possible to downgrade unless you burn another CD.

---

### Post by mapes12 on 2008-12-20
> **cooperman411 said:**
> Thanks so much!  I think I understood all that.

Next quick question -- can I install 8.04 from the web/download directly or do I have to create a new install CD?  Also, can I install it without writing over the documents/music/photos I've put on here since installing 8.10?

Thanks again!
You will need to burn yourself another CD of the 8.04 iso. Personally, I use the [alternate CD's]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") but if the Live CD's work for you then all well and good.

Now, to keep all the stuff you have saved to your machine you will need to keep a copy of everything in your /home folder. You will see it in your Filesystem. You can use a backup application or just copy the entire folder to external media. When you have the new installation installed then just copy the entire folder back again. Your /home folder contains all your files, settings, firefox bookmarks and generally the entire look and feel to how you like your system.

Another way to preserve /home is to move it to a separate partition ahead of the new installation. This involves some more work but in the future will save a lot of time if your system crashes and you need to install it again. This [HowTo]("http://ubuntuforums.org/showthread.php?t=46866") worked faultlessly for me.

If you move /home to another partition you will need to be careful when installing Ubuntu. You will get to a section called Partitioning. The Default is **Guided - Use Entire Disk**. You don't want this. Select the last option called **Manual**. Then for each partition on your system select it, then select the variables from the options to tell the installer where to place "/", /home and Swap. This might sound a bit complex at first but once you have done it a few times it really is quite easy.

As you start to tweak around with your system (most people do) then occasionally things go wrong and the OS gets screwed up. Unlike windoze getting your system up and running again is quick and easy provided you have a clear configuration strategy. The first part of this is to have /home on a separate partition. You then have numerous options. I like to keep a [tar file of all my system files]("http://ubuntuforums.org/showthread.php?t=35087&page=76") (look for post no. seven five eight) plus a full backup of all my installed packages in an iso file backed up by an application called aptoncd (search for it in Synaptic).

In a windoze world users become paranoid about their system crashing. And quite rightly so. Windoze filesystem is all over the place which makes any crash, virus attack etc.a nightmare. Linux has a much more orderly and secure file system making recovery very easy. Always keep /home safe and you should be fine.

---

### Post by cooperman411 on 2008-12-27
Hey there!  I've been travelling for the holidays and haven't been online much at all. Thanks for all the advice.  I now have a new question:

In the mean time, I've burned a new CD with 8.04.  I was going to install it but during the setup I got something I couldn't understand.  I got a copy of windows and installed it.  During installation I accidentally partitioned the disk and have  "D" drive and a "C" drive.  Windows is on D.  I want to put 8.04 on the C drive.  When I attempt to install it only shows one partition to install on and I'm not sure if it's C or D.  I don't want to wipe out Windows by accident. Don't worry -- everything is backed up if I do but it'd be a royal pain to install windows again.

---

### Post by HavocXphere on 2008-12-27
I fixed my resolution + refresh rate issues like [this]("http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401") [offsite]. Do note that it was on Kubuntu though...should be the same on ubuntu though.

The "C" "D" designation is user only by windows...it means little outside of windows. Windows always designates the partition on which it is installed as "C"...and you can't change the OS drive letter. The others you can change via the logical disk manager in MS.

I usually look at the partition sizes to figure out what is what. Thats not the "correct" way...but it works for me.

Your description is slightly confusing. What is currently installed...What installer is showing 1 partition only? Is the 1 partition using all of the space available on the disk?

---

### Post by cooperman411 on 2008-12-29
Funny story -- I went to install 8.04 and the partition thing was making me crazy.  I successfully figured out which partition and when I did, it wiped out windows. Oops.  Damage already done, I started over and just did a clean install.  I now have an exclusive Linux machine and I'm going to leave it that way.

I have an old Creative Nomad MP3 player.  WHen I plug it in, the system doesn't see it at all.  I have a USB drive which works just fine and so I'm not sure why it can't find the MP3 player as it's basically just a USB drive.  

Also, I have a Magicjack (USB VoIP phone).  I plugged it in and under windows it recognized it as 2 USB drives but Ubuntu ignores it.  I ran the MagicJack program on Wine and was shocked that it actually loaded but then I got an error message telling me to connect my MagicJack.  Again, ignores the USB device.  But I don't understand why it has no problem with my USB 10-key, mouse, or my 16gb USB drive.

Any advice?

---

### Post by cooperman411 on 2008-12-29
Forgot to mention -- can't play a DVD either.  Totem Movie Player launches when I insert a DVD and then a few seconds later I get a little window with "could not read from the resource".

I can put in a DVD bootable disk no problem, and I can see the files on the DVD in the file browser but it won't play.

Ideas?

---

