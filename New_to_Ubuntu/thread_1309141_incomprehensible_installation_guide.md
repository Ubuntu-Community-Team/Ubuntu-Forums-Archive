---
title: "incomprehensible installation guide"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by buntybu on 2009-11-01
I'm fairly tech savvy but new to Linux. Does anyone else think [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") is incomprehensible nonsense?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I'm about to give up with Ubuntu.

I don't have the 'Ubuntu USB desktop image creator', I can't find it in 'System-->Administration-->Create a USB startup disk' and typing 'sudo apt-get install usb-creator' into the Terminal returns the message 'Couldn't find package usb-creator'. So the first three things/instructions tried don't work, and I've hardly even started. Tried installing ImageWriter to create a USB boot disk, didn't work. Tried installing unetbootin-linux 377 which doesn't work either. 

[This page]("http://www.ubuntu.com/getubuntu/download-netbook"), makes it look simple and easy, but it sends you to another page for (incomprehensible) instructions, which in turn sends you to another [two]("https://help.ubuntu.com/community/Installation/FromImgFiles") pages for some [more incomprehensible instructions]("https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html") so I have 4 tabs open just to try and install Ubuntu 9.10 and still can't do it.

A long way from the one click wonder of an Android or Apple installation.

Painful and frustrating.

---

### Post by ikt on 2009-11-01
> **buntybu said:**
> A long way from the one click wonder of an Android or Apple installation.

Creating USB installs on other Operating Systems can be quite difficult, this is where ubuntu shines, it's so easy! You just go to USB start up disk creater > select the ISO > create! and I've done it tons of times!

Are you trying to install ubuntu via a usb stick?
Which OS are you using to do this?

---

### Post by buntybu on 2009-11-01
Thanks I'm trying to do it on a recently acquired Dell Mini 10v with Hardy Heron (8.04) installed. Trying to upgrade it to 9.10, but want to create a USB drive to boot from so I can go have a dual boot option (booting either into Dell version of 8.04 that it shipped with or 9.10).

Cheers.

---

### Post by ikisham on 2009-11-01
There may be some other way I'm unaware of.
What I know is that you should burn the ubuntu live-cd in a computer that has a disc drive and create the bootable usb in this same machine by booting into the live-cd, plugging in the usb stick, and going to System>Administration>Create a USB startup disk.
Then you can use it with the netbook.

---

### Post by ikt on 2009-11-01
> **buntybu said:**
> Thanks I'm trying to do it on a recently acquired Dell Mini 10v with Hardy Heron (8.04) installed. Trying to upgrade it to 9.10, but want to create a USB drive to boot from so I can go have a dual boot option (booting either into Dell version of 8.04 that it shipped with or 9.10).

Cheers.

If you head into terminal and do:

```
sudo apt-get install usb-creator
```

You should then have :

```
System-->Administration-->Create a USB startup disk
```

Available to you.

---

### Post by ugm6hr on 2009-11-01
I would strongly recommend just downloading the NBR (netbook remix) - it is easily written (using a single terminal command) to USB.

If you want the standard version, you can then just as easily remove the netbook-launcher / maximus and install the standard ubuntu-desktop.

You may find that some of the other solutions don't work, since the Dell Ubuntu 8.04 repository does not necessarily have the same applications available.

---

### Post by buntybu on 2009-11-01
-

---

### Post by buntybu on 2009-11-01
> **ikt said:**
> If you head into terminal and do:

```
sudo apt-get install usb-creator
```

You should then have :

```
System-->Administration-->Create a USB startup disk
```

Available to you.

Thanks. 

I tried that (see original post above) and got a 'Couldn't find package usb-creator' error message.

---

### Post by LewRockwell on 2009-11-01
netbooks are cool, except for small screens and no optical drive

here is one alternate method:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by LewRockwell on 2009-11-01
maybe you can get someone...a friend perhaps...to send you a USB drive already set-up and ready to go?

(depending on where you are of course)

.

---

### Post by buntybu on 2009-11-01
Thanks.

I downloaded the NBR, which is what I'm trying to put on a USB drive to boot from.

> **ugm6hr said:**
> I would strongly recommend just downloading the NBR (netbook remix) - it is easily written (using a single terminal command) to USB.

When you say 'easily' what do you mean (i.e. how?), given that I've tried all the methods in the original post.

My experience so far is that it's anything but easy. 'Frustrating' and 'annoying' would be more like it.

---

### Post by buntybu on 2009-11-01
> **LewRockwell said:**
> netbooks are cool, except for small screens and no optical drive

here is one alternate method:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

Thanks. Couldn't find a method there. Just more incomprehensible instructions. I'm trying to be patient (with Ubuntu, not with the kind advice given here) but am tempted to give up.

---

### Post by buntybu on 2009-11-01
> **LewRockwell said:**
> maybe you can get someone...a friend perhaps...to send you a USB drive already set-up and ready to go?

(depending on where you are of course)

.

Thanks. Sounds like a great idea. 

Alternatively, why isn't it possible just to do the same (effectively) and download it, put it straight onto a USB memory stick and boot from it??

---

### Post by LewRockwell on 2009-11-01
> **buntybu said:**
> Thanks. Sounds like a great idea. 

Alternatively, why isn't it possible just to do the same (effectively) and download it, put it straight onto a USB memory stick and boot from it??


There are indeed an untold number of sources/solutions/guides/tutorials/etc strewn across the world wide interwebs!


For those with time and patience:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

[http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive](http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive)


For others:

[https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers](https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers)

[http://ztechshop.net/usb/ubuntu/](http://ztechshop.net/usb/ubuntu/)

[http://brainstorm.ubuntu.com/idea/5737/](http://brainstorm.ubuntu.com/idea/5737/)

.

---

### Post by ugm6hr on 2009-11-01
WARNING: For future readers, the advice here does not apply to 9.10

OK. Lets get this sorted.

What is the name of the file you downloaded - you say it is the .img file above - can you confirm that, since you never stated that at the start.

Then, what size is the USB drive?  I have heard of people having difficulties if using a partition greater than 4GB, although I can't think why.

Did you format the drive in vfat?

Then, use your 8.04 Dell, with the USB plugged in (and no other usb sticks plugged in).  The downloaded .img file must be on an SD card or on the HD.

I have borrowed from the Terminal advice here: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

> 
Plug in USB stick (1-4GB preferably, with no data on it).
I assume the img file is at /home/username/ubuntu.img
**Please ensure the USB is /dev/sdb before proceeding** - if there are no other USB plugged in, it should be
To check:
```
sudo dmesg | tail -20
```

Check md5sum (if you haven't already) to ensure the file is not corrupted:
```
md5sum ~/ubuntu.img
```
Compare output to the listed md5sum: ed6e77587b87fe0d92a2f21855869f00

Then:
Format USB
```
sudo mkfs.vfat /dev/sdb1
```

Unplug, then replug the USB drive in, then unmount
```
sudo umount /dev/sdb1
```

Copy the file
```
sudo dd if=/home/username/ubuntu.img of=/dev/sdb bs=1M
```
Reboot from USB drive


PS: I have just realised that the 9.10NBR page does contain a link to [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) which is WRONG.  That is about installing the standard Desktop iso to USB; there is a small comment linking to the correct page, but it is confusing.  EDIT: My mistake - incorrect link is in Step 1, not step 2.


EDIT2: I have emailed the ubuntu.com webmaster re: error in link.

EDIT3: If you are at all uncertain, run the 1st and 2nd commands above to check the situation, copy and paste results here, and I will give you the exact commands for the rest.

EDIT4: Sorry - just realised I typed sda everywhere - it should be **sdb**

---

### Post by buntybu on 2009-11-01
> **LewRockwell said:**
> There are indeed an untold number of sources/solutions/guides/tutorials/etc strewn across the world wide interwebs!


For those with time and patience:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

[http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive](http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive)


For others:

[https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers](https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers)

[http://ztechshop.net/usb/ubuntu/](http://ztechshop.net/usb/ubuntu/)

[http://brainstorm.ubuntu.com/idea/5737/](http://brainstorm.ubuntu.com/idea/5737/)

.

Thanks 

Permission to weep?

> **LewRockwell said:**
> [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
Tried ImageWriter already. To no avail. See original post.

> **LewRockwell said:**
> [http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive](http://www.howtoforge.com/installing-ubuntu-8.10-on-your-usb-flash-drive)
I'm using 8.04 that ships with Dell mini 10v. It does not include USB creator.

> **LewRockwell said:**
> [https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers](https://help.ubuntu.com/community/GettingUbuntu#Obtaining%20from%20Other%20Suppliers)
This is one of those circular instruction pages, which refers you to endless other pages to download bit and pieces. You have to follow the [image file writing instructions]("https://help.ubuntu.com/community/Installation/FromImgFiles") to which I referred in my original post. Incomprehensible.

> **LewRockwell said:**
> [http://ztechshop.net/usb/ubuntu/](http://ztechshop.net/usb/ubuntu/)
I'm not paying $70 dollars for it.

> **LewRockwell said:**
> [http://brainstorm.ubuntu.com/idea/5737/](http://brainstorm.ubuntu.com/idea/5737/)
ditto.
> **LewRockwell said:**
> time and patience
!!
I've already spent days on it which is more than most standard Win/Mac/Android etc. users would.

---

### Post by ugm6hr on 2009-11-01
> **buntybu said:**
> Alternatively, why isn't it possible just to do the same (effectively) and download it, put it straight onto a USB memory stick and boot from it??

Because the boot files need to be written using a low level writing device (e.g. dd); just copying the file on to the USB is akin to just copying an iso file on to a CD.

---

### Post by buntybu on 2009-11-01
> **ugm6hr said:**
> OK. Lets get this sorted.

What is the name of the file you downloaded - you say it is the .img file above - can you confirm that, since you never stated that at the start.

Thanks.
It's the file you get from the [UNR download page]("http://www.ubuntu.com/GetUbuntu/download-netbook"), an ISO file.

> **ugm6hr said:**
> Then, what size is the USB drive?  I have heard of people having difficulties if using a partition greater than 4GB, although I can't think why.
1GB

> **ugm6hr said:**
> Did you format the drive in vfat?
Er...dunno. Whassat? This is for newbies remember.

I haven't formatted the USB stick (and can't see how to on this machine - Dell Mini 10v 8.04).

> **ugm6hr said:**
> Then, use your 8.04 Dell, with the USB plugged in (and no other usb sticks plugged in).  The downloaded .img file must be on an SD card or on the HD.

I have borrowed from the Terminal advice here: [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)



Following the terminal advice I get as far as the 'Check md5sum'when I get a 'no such file or directory' presumably because I don't have the .img file, and if I did, I wouldn't know the right place to put it on the HD for it to be checked by this command.

Regarding your comment about the incorrect URL for the NBR; can you tell me the correct url to get the NBR .img file?

Many thanks.

---

### Post by ugm6hr on 2009-11-01
Apologies, we'll start from the beginning again.

I made the mistake of assuming the system used would have remained the same since I got 9.04 NBR, but it has in fact changed completely; hence the confusion with all the various instructions.

It appears that, while the NBR is designed for Netbooks (which have no CD drives), 9.10NBR is now only distributed as an iso file (no longer as an img for USB images).  Why?  No idea.  I found the img format a lot more sensible.

Anyway, given you now have the iso file, the easiest way to put this on to USB is with Unetbootin, and, surprisingly, to do it on a Windows machine.  Unfortunately, usb creator is not available for the Dell Ubuntu (as far as I know).

So, the important questions are:

Do you have access to a Windows machine?
Do you have any machines with a "standard" Ubuntu installation (i.e. not your dell version)?

EDIT: Wow. This is a real failure on Canonical's part not to maintain the img NBR.  You are not alone in your confusion: [http://ubuntuforums.org/showthread.php?t=1304609](http://ubuntuforums.org/showthread.php?t=1304609)
[http://ubuntuforums.org/showthread.php?t=1309200](http://ubuntuforums.org/showthread.php?t=1309200)

It is shameful that the easiest way to install it is: either use a different device to burn a CD and then create a USB, or use Windows.

---

### Post by buntybu on 2009-11-01
> **ugm6hr said:**
> Apologies, we'll start from the beginning again.

I made the mistake of assuming the system used would have remained the same since I got 9.04 NBR, but it has in fact changed completely; hence the confusion with all the various instructions.

It appears that, while the NBR is designed for Netbooks (which have no CD drives), 9.10NBR is now only distributed as an iso file (no longer as an img for USB images).  Why?  No idea.  I found the img format a lot more sensible.

Anyway, given you now have the iso file, the easiest way to put this on to USB is with Unetbootin, and, surprisingly, to do it on a Windows machine.  Unfortunately, usb creator is not available for the Dell Ubuntu (as far as I know).

So, the important questions are:

Do you have access to a Windows machine?
Do you have any machines with a "standard" Ubuntu installation (i.e. not your dell version)?

EDIT: Wow. This is a real failure on Canonical's part not to maintain the img NBR.  You are not alone in your confusion: [http://ubuntuforums.org/showthread.php?t=1304609](http://ubuntuforums.org/showthread.php?t=1304609)
[http://ubuntuforums.org/showthread.php?t=1309200](http://ubuntuforums.org/showthread.php?t=1309200)

It is shameful that the easiest way to install it is: either use a different device to burn a CD and then create a USB, or use Windows.

Thanks. I least I know my floundering is founded and not just newbie naivety. 

It does seem amazing you can't install/upgrade from one of the few mass market machines that ships with Ubuntu. 

I do have access to windows pcs and will use one to set up a USB stick to boot from, you're correct though, it doesn't seem quite right that it should be necessary. Hopefully it will be rectified.

Thanks for your help and for looking into it.

---

### Post by ugm6hr on 2009-11-01
I would recommend trying Unetbootin to install to a USB from your Windows machine.

Let us know when you get it sorted.

---

### Post by alexcckll on 2009-11-01
You could always buy one from Linux Emporium or similar...

[http://www.linuxemporium.co.uk/products/ubuntu_9.04/#pidR26956](http://www.linuxemporium.co.uk/products/ubuntu_9.04/#pidR26956)

Just enable "boot from USB" in the BIOS, shut down, plug the stick in, and go..

It's what I'll probably do.. unless I decide to just buy an IdeaPad from LE with Ubuntu preloaded - as I did with my current Thinkpad..

---

### Post by entropic_existence on 2009-11-01
I have found USB-Creator to the be the most straightforward option, at least they have updated the official installation link to point to the right instructions now. So the real problem is that you don't have access to it. 

The third post in this thread ([http://ubuntuforums.org/showthread.php?t=1167133](http://ubuntuforums.org/showthread.php?t=1167133)) seems to indicate that you can install the usb-creator package from 8.10 under 8.04 using gdebi manually.

If that works it is a simple matter of using USB-Creator to load your downloaded iso onto the USB stick.

And in Ubuntu's defence, while I understand this is frustrating, making bootable install USB drives for any OS is painful right now. I don't know about android of course, but the process to make a bootable usb for installation for windows or OS X for instance is even more complicated and difficult. Its just that most end users will never ever have to do that. Linux end users on the other hand, do have to deal with installation, which is not always a straightforward process.

---

### Post by cariboo on 2009-11-01
+1, the usb boot disk creator utility isn't available from the hardy repositories. To get it go [here]("http://packages.ubuntu.com/").

---

### Post by t0p on 2009-11-01
> **alexcckll said:**
> You could always buy one from Linux Emporium or similar...

[http://www.linuxemporium.co.uk/products/ubuntu_9.04/#pidR26956](http://www.linuxemporium.co.uk/products/ubuntu_9.04/#pidR26956)


Dude, why are you advising people to go buy a copy of Ubuntu?  If the OP wanted to fork cash over, he wouldn't have posted here.  Would here?

The OP wants it for free.  Help him do that, or don't help him to do that.  Advising him to do crap he doesn't want to do... well what's the point?  really?

---

### Post by mgmiller on 2009-11-01
You can download a unetbootin.deb from here:
[http://packages.debian.org/sid/i386/unetbootin/download](http://packages.debian.org/sid/i386/unetbootin/download)

That will install unetbootin on your 8.04 machine.  Then use it to created the USB installer from the ubuntu 9.10.iso you have already downloaded.

---

### Post by ikisham on 2009-11-01
Just asking: the USB disk creator creates a persistent installation to the USB stick but doesn't UNetbootin create only a simple live system (no persistence)?

---

### Post by mgmiller on 2009-11-01
> Just asking: the USB disk creator creates a persistent installation to the USB stick but doesn't UNetbootin create only a simple live system (no persistence)?

That is true.  However, I have never gotten persistence to work.  

It works quite well as a simple live environment, but simply will not save anything for me when I try to turn persistence on.  I have been using a 4 gig USB thumb drive and allocating all of it to persistence, but no go.

---

### Post by ugm6hr on 2009-11-02
> **ikisham said:**
> Just asking: the USB disk creator creates a persistent installation to the USB stick but doesn't UNetbootin create only a simple live system (no persistence)?

The OP wants a LiveUSB to install with.

Hence either should work.

---

### Post by TironN on 2009-11-02
if you have a second computer you could set it up through that:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

or if you have a windows one (this is the way I made mine for my Dell Mini 9):
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by buntybu on 2009-11-02
> **entropic_existence said:**
> you can install the usb-creator package from 8.10 under 8.04 using gdebi manually.

If that works it is a simple matter of using USB-Creator to load your downloaded iso onto the USB stick..

Thanks.

You lost me at 'using gdebi manually'. This is a newbie forum remember.

I wish people would stop saying 'then you simply need to...'. Nothing has been simple so far (I don't mean to sound ungrateful for advice though! Just frustrating).

---

### Post by nothingspecial on 2009-11-02
Did you try [[COLOR="Red"]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")?

I even use it to install on computers that do have cd drives.

I have found that sometimes it doesn`t work unless you format the stick first.

---

### Post by buntybu on 2009-11-02
> **mgmiller said:**
> You can download a unetbootin.deb from here:
[http://packages.debian.org/sid/i386/unetbootin/download](http://packages.debian.org/sid/i386/unetbootin/download)

That will install unetbootin on your 8.04 machine.  Then use it to created the USB installer from the ubuntu 9.10.iso you have already downloaded.

Thanks. Tried this. Couldn't add it to Synaptic Package Manager. Get following error message:

'GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FEGPG error: [http://ftp.uk.debian.org](http://ftp.uk.debian.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302BFailed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ftp.uk.debian.org/debian/dists/sid/main/binary-lpia/Packages.gz](http://ftp.uk.debian.org/debian/dists/sid/main/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.'

---

### Post by nothingspecial on 2009-11-02
Unetbootin is available in the ubuntu repositories

---

### Post by buntybu on 2009-11-02
> **nothingspecial said:**
> Did you try [[COLOR=Red]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")?

I even use it to install on computers that do have cd drives.

I have found that sometimes it doesn`t work unless you format the stick first.

Yes. See original post. Download page gives an executable file. Not a linux file.

---

### Post by buntybu on 2009-11-02
> **nothingspecial said:**
> Unetbootin is available in the ubuntu repositories

Not mine it isn't. I searched for it.

---

### Post by nothingspecial on 2009-11-02
what happens if you type ```
sudo apt-get inatall unetbootin
```

What version of ubuntu are you running?

---

### Post by nothingspecial on 2009-11-02
You can get it [[COLOR="Magenta"]here[/COLOR]]("http://packages.ubuntu.com/jaunty/i386/unetbootin/download")

---

### Post by ugm6hr on 2009-11-02
Been out of the loop for a few hours.

My suggestion:

Before doing anything, format the USB as FAT32 (this can be done on Windows too)

1. Download unetbootin for Windows from the unetbootin site: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

2. Install unetbootin on Windows (as per advice on unetbootin site - double click).

3. Run unetbootin on Windows.

4. Point unetbootin to .iso (Disk image) file and usb stick as relevant.

5. Press OK (or whatever the button says).

I haven't used unetbootin for about 6 months, so I hope it hasn't changed the way it works since then too!

The try booting from USB stick - remember you need to change the boot order on the Mini to do that.

Apologies for providing a Windows-related solution, but I think that this will be easiest for you.  The other option is to use a 9.04 img file, install that, and then use that to install usb-creator to create a 9.10 USB stick (which would be stupid).  AS mentioned, the problem stems from using the Dell lpia Ubuntu, which has different repositories (and hence different applications available).  I suspect that you probably could install unetbootin (or maybe even usb creator) on the lpia Ubuntu, but would not guarantee it - hence the advice to use Windows.  Additionally, I always found the Linux unetbootin to be less reliable than on Windows (although this has been improved with recent releases).

Let us know how it goes.

---

### Post by buntybu on 2009-11-03
> **nothingspecial said:**
> what happens if you type ```
sudo apt-get inatall unetbootin
```

What version of ubuntu are you running?

1. I get the following 'E: Invalid operation inatall'

2. Version 8.04.

Cheers.

---

### Post by buntybu on 2009-11-03
> **nothingspecial said:**
> You can get it [[COLOR=Magenta]here[/COLOR]]("http://packages.ubuntu.com/jaunty/i386/unetbootin/download")

Tried this. I get:

'Error: Dependency is not satisfiable: libqt4-network'

---

### Post by entropic_existence on 2009-11-03
> **buntybu said:**
> Thanks.

You lost me at 'using gdebi manually'. This is a newbie forum remember.

I wish people would stop saying 'then you simply need to...'. Nothing has been simple so far (I don't mean to sound ungrateful for advice though! Just frustrating).

Sorry, the using gdebi manually was a reference to the instructions in the thread that I linked to. The recommendations to download a .deb and install manually bypass the need to use synaptic package manager. There is at least one other post in this thread pointing directly to a .deb file for usb-creator. Follow the link and download the .deb file. When it asks you what to do with it (download, etc) there should be an "open with> option, it should default to a program called gdebi. This is a manual package installer. You may get some warnings (lpia versus 386 architecture) but you will want to force it to install. 

If you need further help at this stage there are many excellent threads on these forums I believe for using gdebi to force an install on a different architecture. If I can I will come back later and post some links.

---

### Post by techstop on 2009-11-03
> **buntybu said:**
> Tried this. I get:

'Error: Dependency is not satisfiable: libqt4-network'

The link you quoted is for jaunty (9.04), not hardy (8.04) which you are using.

Here is a direct link to the file you need;

[http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-creator/usb-creator_0.1.10~hardy1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-creator/usb-creator_0.1.10~hardy1_all.deb)

Save it to your hard drive. Then double-click on the file and run it if asked. You will then have usb-creator in your menu, which is extremely easy to use.

---

### Post by buntybu on 2009-11-03
> **entropic_existence said:**
> Sorry, the using gdebi manually was a reference to the instructions in the thread that I linked to. The recommendations to download a .deb and install manually bypass the need to use synaptic package manager. There is at least one other post in this thread pointing directly to a .deb file for usb-creator. Follow the link and download the .deb file. When it asks you what to do with it (download, etc) there should be an "open with> option, it should default to a program called gdebi. This is a manual package installer. You may get some warnings (lpia versus 386 architecture) but you will want to force it to install. 

If you need further help at this stage there are many excellent threads on these forums I believe for using gdebi to force an install on a different architecture. If I can I will come back later and post some links.

Finally!! Some success!! Followed links elsewhere in this thread and have managed to install USB Creator! Thank you. 

Now just need to figure out how to format a USB memory stick on Dell mini 10v 8.04 and then hopefully will be able to create a boot disk. Perhaps the pain is nearly over.

Thanks.

---

### Post by mgmiller on 2009-11-03
> Thanks. Tried this. Couldn't add it to Synaptic Package Manager. Get following error message:

I should have been more explicit.  Once you go to that page, just click on one of the mirror links that are listed.  It will offer to download a .deb that you can then just double click to install.

---

### Post by mgmiller on 2009-11-03
> Now just need to figure out how to format a USB memory stick on Dell mini 10v 8.04 and then hopefully will be able to create a boot disk. Perhaps the pain is nearly over.I am sure people will give you commands that can do this from terminal, but if you want a gui application.  You need to install gparted.

You can install it from synaptic if you want to use the gui approach, or you can install it from command line, by copying and pasting into terminal:
```
sudo apt-get install gparted
```Once, it's installed, you need to plug in the memory stick first and wait for it to mount, then run gparted.  
System > Administration > Gparted.

Once it loads, there is a drop down in the upper right corner that will say /dev/sda (size of your drive).

Click the down arrow and you will see your thumb drive in the list.  Just select it.

It will appear as a horizontal graphic.
Below it, you will see what the drive is formatted as, it's mount point, size, used, etc.

Make sure you are looking at the thumb drive!!!
Right click inside that graphic and select "Unmount".
Once it's unmounted, again right click inside the graphic and select "Format To" and select what you want.

This will erase all data on the drive, so again be certain you are looking at your thumb drive!

Next, you will click the "Apply" button in the top of the window and it will format the drive.

Once it's done, you can exit gparted.

You will probably need to remove and reinstert the drive for it to be recognized again.

I have a 1 gig thumb drive that I use for installs and it is formatted as fat16.

---

### Post by nothingspecial on 2009-11-03
> **buntybu said:**
> 1. I get the following 'E: Invalid operation inatall'

2. Version 8.04.

Cheers.

That`s because I typed it wrong 

```
install
```

not

```
inatall
```

anyway, glad to see you got it sorted :D

---

### Post by SaintDanBert on 2009-11-03
> **buntybu said:**
> 
I'm fairly tech savvy but new to Linux. Does anyone else think [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") is incomprehensible nonsense?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I'm about to give up with Ubuntu.
...


I could not agree more!!!

I've been a computer guy since the late sixties and while new to Ubuntu, I'm not a Ludite or other techno-phobe. Between the problems caused by the need for enormous head space for back story and the other enormous head space for options of lists of options... I need
duct (duck) tape to keep my head from exploding. Add to this manuals and HOWTO etc that provides answers only for those who don't need to ask the question.

I'm glad that so many folks stepped up trying to answer your technical question. I wrote to speak about your complaint subject line.

Kindred reader,
~~~ 0;-Dan

---

### Post by buntybu on 2009-11-04
> **mgmiller said:**
> I should have been more explicit.  Once you go to that page, just click on one of the mirror links that are listed.  It will offer to download a .deb that you can then just double click to install.

Thanks.

Yes, I did see that, but the page you linked to also recommended that you install it via the Synaptic Manager, so I was playing safe. Have now managed a direct install using gdebi. Cheers.

---

### Post by buntybu on 2009-11-04
> **SaintDanBert said:**
> I could not agree more!!!

I've been a computer guy since the late sixties and while new to Ubuntu, I'm not a Ludite or other techno-phobe. Between the problems caused by the need for enormous head space for back story and the other enormous head space for options of lists of options... I need
duct (duck) tape to keep my head from exploding. Add to this manuals and HOWTO etc that provides answers only for those who don't need to ask the question.

I'm glad that so many folks stepped up trying to answer your technical question. I wrote to speak about your complaint subject line.

Kindred reader,
~~~ 0;-Dan

Thank you! I'm not going mad!

I think a quick browse through this (and other) threads shows the difficulties. Thankfully, the clouds are now parting a bit and I'm beginning to see a way through, but what a struggle!

I second that thanks for all the patient help 'round here.

---

### Post by buntybu on 2009-11-04
> **mgmiller said:**
> I am sure people will give you commands that can do this from terminal, but if you want a gui application.  You need to install gparted.

You can install it from synaptic if you want to use the gui approach, or you can install it from command line, by copying and pasting into terminal:
```
sudo apt-get install gparted
```Once, it's installed, you need to plug in the memory stick first and wait for it to mount, then run gparted.  
System > Administration > Gparted.

Once it loads, there is a drop down in the upper right corner that will say /dev/sda (size of your drive).

Click the down arrow and you will see your thumb drive in the list.  Just select it.

It will appear as a horizontal graphic.
Below it, you will see what the drive is formatted as, it's mount point, size, used, etc.

Make sure you are looking at the thumb drive!!!
Right click inside that graphic and select "Unmount".
Once it's unmounted, again right click inside the graphic and select "Format To" and select what you want.

This will erase all data on the drive, so again be certain you are looking at your thumb drive!

Next, you will click the "Apply" button in the top of the window and it will format the drive.

Once it's done, you can exit gparted.

You will probably need to remove and reinstert the drive for it to be recognized again.

I have a 1 gig thumb drive that I use for installs and it is formatted as fat16.

More success!! Thank you for the very clear, step-by-step instructions.

Gparted installed (except it called itself Partition Manager so I didn't see it at first). Had some difficulties with the memory stick formatting, but it's writing to the USB stick as I type!! Might finally be getting there.

---

### Post by buntybu on 2009-11-04
> **techstop said:**
> The link you quoted is for jaunty (9.04), not hardy (8.04) which you are using.

I was just  a newbie following instructions... :(

---

### Post by buntybu on 2009-11-04
> **mgmiller said:**
> I should have been more explicit.  Once you go to that page, just click on one of the mirror links that are listed.  It will offer to download a .deb that you can then just double click to install.

Thank you. That worked!

---

### Post by buntybu on 2009-11-04
Ooooh. So close.

Have created USB drive to boot from. When I hit F12 on startup to go into boot options, and select removable drive I get the following error message:

'con-system disk or disk error'

then

'MBR system disk or disk error'

Any ideas what that's about?

---

### Post by buntybu on 2009-11-04
Oh. It's all gone quiet. And I was getting so close.

---

### Post by disorientedminds on 2009-11-04
> **buntybu said:**
> I'm fairly tech savvy but new to Linux. Does anyone else think [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") is incomprehensible nonsense?
 
If you have ever made a bootable usb disk of any kind then this is cake. Have you tried booting to the disk from another computer, if that is available? If not try starting over with a different usb disk, that one could have corrupt sectors on it.

---

### Post by R_U_Q_R_U on 2009-11-04
I am sorry to say this, but money will solve your problem. I have a Samsung NC10 netbook that came with XP. I bought an LG USB external DVD drive and on another machine burned the ISO of 9.10 UNR to a CD. Plugged my external DVD drive into my netbook and booted from the aforementioned CD. Installed Ubuntu on netbook without any issues and it runs great.

---

### Post by disorientedminds on 2009-11-04
Yes that will definatley work but not everyone has an external disk drive, which aren't needed anymore since everything can be downloaded and made into an image if it's not already one when downloaded.

---

### Post by mgmiller on 2009-11-04
> 
'con-system disk or disk error'

then

'MBR system disk or disk error'

Any ideas what that's about?If the drive is formatted as fat16, try changing it to fat32 and vice-versa.

Also the boot flag has to be set.  unetbootin should have done that for you, but you never know.

Put the drive back in and when it mounts, startup gparted again.

Right click the graphic of the drive and click "Manage Flags".
Make sure that "Boot" and "Lba" are checked and nothing else.
When you close the manage flags window, the changes should apply.


Also sometimes booting from a thumb drive can be finicky about the brand of drive.

What size drive are you using?  I have had best luck using 1 gig thumb drives for this.

I have attached a picture of my 1 gig thumb drive that I have used to boot into a live session.  Notice the curser is pointing at the boot listing in the Flags section.

---

### Post by R_U_Q_R_U on 2009-11-04
> **disorientedminds said:**
> Yes that will definatley work but not everyone has an external disk drive, which aren't needed anymore since everything can be downloaded and made into an image if it's not already one when downloaded.

Apparently not. The OP has been having a very hard time getting a bootable USB image of UNR. I merely pointed out that for some people, money can solve the problem. It is the buyer's choice. Struggle and be frustrated, or spend a small amount of cash to purchase a proven and easy solution.

Based on the number of suggestions posted to this tread giving the OP all sorts of tips and hints on how to get 9.10 on his netbook, I am thinking he would be very happy to have an external DVD drive ;-)

---

### Post by nothingspecial on 2009-11-04
unetbootin works.

I have used it today to install crunchbang on my samsung nc10.

Last week I used it to install karmic on our households 5 computers.

In your menus go system > preferences > software sources

Click on add and copy and paste these 2 lines (1 at a time) into it
```

deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu hardy main 
```

Then type ```
 gedit key.txt
```

In the window that opens, copy and paste this into it
```

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXZ0aQEEAJuOMpfa92ZgqoLkBTKjN1D3zplRbxCkfCJ7vo5O+lEx5lM8x3K1QU3AY1Vs
LGPMpTVbl9kdFnOIKc0MD166l3yPPjuEmb7a+odpBJHhfcKPhpHc5kVBSrD+7/LnVRFISQZI
IbrN+v3CNU0ZqIJ1FbJpkaqPRKKYhGGaFXTWoKl3ABEBAAG0HUxhdW5jaHBhZCBQUEEgZm9y
IEdlemEgS292YWNziLYEEwECACAFAkl2dGkCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAK
CRDUXfLo/JGufqS+A/9+5ZIaV3QuW/gEecvZafnYchgF3ZgG82UDflyvptl5KjVEprYcn3Ey
UAiYCHIu7tiJL2e8Wq3uEp5sGbqdIOqAeAANlvAKJbv1P6tePGPhTRRvWwULnU+xfGzk3HeL
SVKYjJboojJ/ntFqP0vrr4FIKgzXbKNSVjoOMsHRvpeoaA==
=c5Rb
-----END PGP PUBLIC KEY BLOCK-----
```

Go back to software sources and click authentication, then import key file. (Find your home folder if it doesn`t display it) and highlight key.txt. Then click ok.

Then type (or copy and paste)```
 sudo apt-get update && sudo apt-get install unetbootin
```


Then type ```
sudo unetbootin
```

---

### Post by buntybu on 2009-11-05
Success!! 

Finally have 9.10 running from a USB memory stick, and how lovely it is (and only took me 3 days to do)!!

Will try and recreate the steps here when I have the energy, in case it's useful for anyone.

Thanks to all for advice.

Only couple of slight problems, wireless connection is not kicking in, not sure drivers have installed, and unable to install the NBR onto HD as I get an insufficient free space message, despite having way more free space on HD than on memory stick.

Anyways, 9.10 NBR is running, and a very nice it is too.

---

### Post by ikisham on 2009-11-05
In the USB stick you have Ubuntu compressed, which is the size of the iso. It's decompressed at boot time.
To install it it would have to be decompressed. It's recommended, I think, at least 6GB of disk space. It can be installed in less but I don't know which amount of disk space the installer is set to consider the minimum.

My Karmic install has only 2.9 GB but Ubuntu considers 4.2 GB since it reserves some space for functioning properly. My data is in a separate partition.
```
sergio@puppypc:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              11G  2.9G  6.8G  30% /
udev                  502M  256K  501M   1% /dev
none                  502M  1.2M  501M   1% /dev/shm
none                  502M   80K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda6             7.3G  4.9G  2.1G  71% /data

```

Also it's better that you sort out this wireless thing before installing and ending without Internet.

---

### Post by R_U_Q_R_U on 2009-11-05
> **buntybu said:**
> Success!! 

Finally have 9.10 running from a USB memory stick, and how lovely it is (and only took me 3 days to do)!!

Very Nice. Glad you were able to accomplish your goal. And yes. UNR 9.10 is very nice. I really think the appearance is far better than 9.04.

Enjoy!

---

