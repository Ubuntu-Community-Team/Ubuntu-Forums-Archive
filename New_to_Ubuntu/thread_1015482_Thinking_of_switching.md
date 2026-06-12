---
title: "Thinking of switching"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Wovaki on 2008-12-18
Hello everyone!

This is my first post here, and I'm thinking about switching from Windows (Vista) to Ubuntu. Right now its a little scary, since I have never done this before, and I will have no clue what I am doing.

I'm hoping I can get some questions answered to help me along.

Since I am using Vista, I plan to install Ubuntu using the Wubi installer, so I have a few questions about that:

[B]1. If I were to install Ubuntu using Wubi, and keep windows (dual boot?) would this be the same as just using the live cd to partition my hard drive?

2. If I downloaded a file on the Ubuntu boot that had a windows virus in it, and then switched to the Windows boot, would that virus then be able to work and do whatever it is supposed to do? (Security is the main reason I want to switch).

3. Using Wubi, is any of my Windows files or anything going to be deleted when I install/uninstall, or whatever else using Wubi?[/B]


My next question doesn't really have anything to do with Wubi specifically, but [B]using the Live CD, can I check to see if all my hardware is compatible, and can I do almost anything (browse the internet, test out apps, etc.) from the Live CD without installing Ubuntu?

Also will using the Live CD change anything, like delete stuff on my hard drive or anything like that?[/B]


Thanks, any help is greatly appreciated!
Wovaki

---

### Post by pmains on 2008-12-18
Man up and blow away your Vista partition.

In all seriousness, why do you think you might lose Windows files? I doubt that you will, but it never hurts to back up your system when making a change like this.

On point 2, it is possible to transfer files from Linux to Windows, so I suppose that it's hypothetically possible for a virus to go from your Linux partition to your Windows partition. However, it needs a way to get there. If it's a Windows executable, it won't execute under Linux, right? So, this virus would have to be specifically written in order to infect dual-boot computers, or some nonsense like that. I think you're safe.

That's just me spit-balling. Maybe someone more knowledgeable should chime in.

---

### Post by Hospadar on 2008-12-18
1)
No, wubi doesn't actually make a partition.  I'm not sure exactly how it works, but it's different from a regular install.

2)
Maybe, if you have the windows ext3 filesystem drivers, and you went and opened that file.  But the likeliehood of that happening is very tiny.

3)
No, although it's always good to back up any super important stuff before you monkey with your drives.

---

### Post by bumanie on 2008-12-18
1) I prefer an installation to a separate partition rather than wubi, however you can install with wubi and later transfer ubuntu to it's own partition using [this procedure]("http://lubi.sourceforge.net/lvpm.html"). Wubi works differently to other installations - it's beyond my understsnding, but involves all sorts of hooks and I assume windows-like api's that makes windows believe it is a regular windows program.
2) Not sure how a windows virus obtained on ubuntu would affect windows - on a 'normal' dula boot it won't have any effect unless the file is transferred to windows.
3) As long as everything goes correctly, wubi will not delete anything presently on your windows drive.
4) The live cd works off the cd and loads into ram - it does not touch your any of your other hardware at all - ie hard drives.

---

### Post by albinootje on 2008-12-18
> **Wovaki said:**
> 
[1. If I were to install Ubuntu using Wubi, and keep windows (dual boot?) would this be the same as just using the live cd to partition my hard drive?

No, the live cd does not by default not write to your hard disk.
With Wubi you will get a new directory (folder) on your Windows-partition
containing all files needed to run Wubi.
> 
2. If I downloaded a file on the Ubuntu boot that had a windows virus in it, and then switched to the Windows boot, would that virus then be able to work and do whatever it is supposed to do? (Security is the main reason I want to switch).

If you would click/run that file in Windows it would be the same effect.
But if you decide later to give Ubuntu a real partition on your disk, then you will get "a kind of new security layer" from Ubuntu.
> 
3. Using Wubi, is any of my Windows files or anything going to be deleted when I install/uninstall, or whatever else using Wubi?[/B]

Unlikely.
> 

My next question doesn't really have anything to do with Wubi specifically, but [B]using the Live CD, can I check to see if all my hardware is compatible, and can I do almost anything (browse the internet, test out apps, etc.) from the Live CD without installing Ubuntu?

Yes.
You can even install software while using the live cd (pretty cool, no ? :), but after a reboot it (the newly installed software) will all be gone.

---

### Post by Shwefty on 2008-12-18
Well, I wouldn't up and "Man up and blow away your Vista partition" quite yet :)

I haven't opened up Windows in a very long time, so security for me is not really a problem...and...frankly I just wouldn't worry about it.

Putting the LiveCD in won't change your computer from the get-go.  You have to hit Install on there before it does anything.  So, feel free to boot from it and select the option to boot from the cd without affecting your computer for a trial!  (Keep in mind that you should expect speed increases whenever you boot from disk over booting from the cd).

About the hardware question, I've never heard anything about that, so...I doubt that the Live CD can do that.  Check out this link for that: [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

Yes, you can delete your partitions if you mess up when installing from the LiveCD.  So, ask around here if your nervous about it or want to know a good way for you to do it.

---

### Post by donkyhotay on 2008-12-18
> **pmains said:**
> Man up and blow away your Vista partition.

In all seriousness, why do you think you might lose Windows files? I doubt that you will, but it never hurts to back up your system when making a change like this.

On point 2, it is possible to transfer files from Linux to Windows, so I suppose that it's hypothetically possible for a virus to go from your Linux partition to your Windows partition. However, it needs a way to get there. If it's a Windows executable, it won't execute under Linux, right? So, this virus would have to be specifically written in order to infect dual-boot computers, or some nonsense like that. I think you're safe.

That's just me spit-balling. Maybe someone more knowledgeable should chime in.

Please don't suggest reformatting to someone that just wants to try it out, some people don't know enough about computers to know they can lose everything if they do that. Linux is great, it's wonderful, but... it's different and it can take some time to get used to. Don't be too scared about trying it. It's a learning process. Start with wubi, it will give you a chance to test ubuntu about as safely as is practically possible. Also remember, So long as your careful about what you do in root you're protected from destroying the linux install, and even if you somehow *do* manage to destroy your linux installation you can just go ahead and reinstall again. Once you've spent a few months or so and have gotten comfortable and familiar with how ubuntu works *then* you may want to think about backing up your data, reformmating, and wiping out your windows. (c;

---

### Post by Wovaki on 2008-12-18
Wow, lots of replies in so short of time!

The main reason I want to start with Wubi is because I have never partitioned a computer or anything like that before, and I have only ever used Windows. So I don't want to go ahead and get rid of windows or even partition it with a dual boot, and with Wubi I can just uninstall Ubuntu if I don't like it.

Another question, if I use the Live CD to partition my drive and keep windows, will my files on windows be deleted, or should the important files only be backed up as a precaution?

Thanks!
Wovaki

---

### Post by albinootje on 2008-12-18
> **Wovaki said:**
> 
Another question, if I use the Live CD to partition my drive and keep windows, will my files on windows be deleted, or should the important files only be backed up as a precaution?

The Ubuntu installation cd (Which is both a live cd and an installation cd) can do the non-destructive resizing of your Windows-partition.
But you should make backups. Imagine having a power-failure during the resizing process, and you'll end up with broken pieces.

(One other option to try Ubuntu is to run it inside a Virtual Machine, like for example VirtualBox. See : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) Expect some performance loss though.)

---

### Post by Aardobard on 2008-12-18
Hey guys, I'm new too! 

Another idea is to grab a second harddrive and go to town.  The thing I like about this approach is that you can use any old harddrive you have lying around or you can pick one up cheap at a thrift store that sells old computers.  Just about anything you find will work.  It's getting pretty hard to find old HDD's smaller than about 40GB.  PLUS they are a breeze to install, even if you've never opened a PC case before!

---

### Post by albinootje on 2008-12-18
> **Aardobard said:**
> Hey guys, I'm new too! 


Welcome! :)
> 
Another idea is to grab a second harddrive and go to town.  The thing I like about this approach is that you can use any old harddrive you have lying around or you can pick one up cheap at a thrift store that sells old computers.  Just about anything you find will work.  It's getting pretty hard to find old HDD's smaller than about 40GB.  PLUS they are a breeze to install, even if you've never opened a PC case before!
Yes, true.

(And running Linux completely of a usb-stick is also an idea.)

---

### Post by balaknair on 2008-12-18
Hello Wovaki

If you use the Live Cd to partition your drive and keep Windows(as a dual boot), it *will not delete any files from Windows*, but will make space for the new partition by shrinking your existing Windows partition(ie, shrinking the free space on the Windows partition). But before you do this, make sure that you **defragment the hard drive under Windows** to eliminate the risk of corrupting fragmented files.

Making backups is a bit like taking out an insurance policy. In most cases(nearly all cases), there will not be any problems, but it adds to your peace of mind to make backups of all the data you've been working on and stuff that you want to save(family photos, videos etc).

If you just want to try out Ubuntu, I suggest using Wubi, so that if you don't like Ubuntu, you can just uninstall it later easily. Wubi creates a virtual hard disk on the existing Windows partition which is mounted when you boot into Ubuntu using a loopback mechanism, and it modifies the Windows bootloader so that an option to boot into Ubuntu is also displayed when you start up the PC. This means that the rest of the Windows partition is untouched.A Wubi installed Ubuntu will however be **slower** than a genuine Ubuntu install with its own partition(not by much if you have a fairly new system with enough RAM), and certain things like Suspend/Resume/Hibernate **will not work** properly.
If after using Wubi for a week or two you decide you want to keep Ubuntu, you can use the LiveCD to partition the hard drive(as dual boot or with only Ubuntu) and install Ubuntu. I recommend using at least 10 GB for the Ubuntu partition and for the SWAP partition double your RAM(if you have RAM 1 GB, use 2 GB for Swap).

Suggested reading: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  A most useful guide, especially for those new to Ubuntu.

The LiveCD- It makes no changes to your hard drive unless you choose to install Ubuntu. And yes I strongly advise that you try out the LiveCD before installing Ubuntu so that you can check hardware compatibilty.

---

### Post by Wovaki on 2008-12-19
> **balaknair said:**
> Hello Wovaki

If you use the Live Cd to partition your drive and keep Windows(as a dual boot), it *will not delete any files from Windows*, but will make space for the new partition by shrinking your existing Windows partition(ie, shrinking the free space on the Windows partition). But before you do this, make sure that you **defragment the hard drive under Windows** to eliminate the risk of corrupting fragmented files.

Making backups is a bit like taking out an insurance policy. In most cases(nearly all cases), there will not be any problems, but it adds to your peace of mind to make backups of all the data you've been working on and stuff that you want to save(family photos, videos etc).

If you just want to try out Ubuntu, I suggest using Wubi, so that if you don't like Ubuntu, you can just uninstall it later easily. Wubi creates a virtual hard disk on the existing Windows partition which is mounted when you boot into Ubuntu using a loopback mechanism, and it modifies the Windows bootloader so that an option to boot into Ubuntu is also displayed when you start up the PC. This means that the rest of the Windows partition is untouched.A Wubi installed Ubuntu will however be **slower** than a genuine Ubuntu install with its own partition(not by much if you have a fairly new system with enough RAM), and certain things like Suspend/Resume/Hibernate **will not work** properly.
If after using Wubi for a week or two you decide you want to keep Ubuntu, you can use the LiveCD to partition the hard drive(as dual boot or with only Ubuntu) and install Ubuntu. I recommend using at least 10 GB for the Ubuntu partition and for the SWAP partition double your RAM(if you have RAM 1 GB, use 2 GB for Swap).

Suggested reading: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  A most useful guide, especially for those new to Ubuntu.

The LiveCD- It makes no changes to your hard drive unless you choose to install Ubuntu. And yes I strongly advise that you try out the LiveCD before installing Ubuntu so that you can check hardware compatibilty.

Thanks for the reply!

My main concern with using the CD to install was losing all my windows files, I thought partitioning the drive (even keeping windows) would wipe out all my documents and stuff like that.

**If I use Wubi to install, the sleep/hibernate/resume wont work only on Ubuntu, or on my Windows boot too? Will this be fixed after I uninstall?**

I'm going to test Ubuntu first by booting up from the Live CD, then if I like that, I will install with Wubi for a few weeks. If everything goes fine then maybe I will look at partitioning my drive. **If I partion my drive to dual boot, and decide I want to get rid of one or the other, is it easy to do, and does it keep all my files intact for the OS I'm keeping?**

Another question, **if I install Ubuntu with Wubi, will it be as secure as partitioning my drive, for viruses and stuff like that?**
Because I know that basically the Ubuntu installation is stored right inside the Windows boot.

**What about Vista compatibility?**
I heard that the Live CD is not compatible with Windows Vista, but will it work fine and partition everything alright with Windows Vista?

[B]_Some information about my computer_:
Make: HP
Type: Laptop
RAM: 3GB
HDD: 200+GB (100+GB Free)[/B]

If more information is needed, please let me know. :D

My computer also has buttons on it for raising the volume, and controls that work with Windows Media Player (Back, Play/Pause, Forward, Stop, Mute) as well as some "QuickPlay" buttons that launch Windows Media Center. **Does anyone know if any of these things are compatible, or if its possible to make them compatible?**

**Thanks for all your help, I really appreciate Everyone's help!**
Wovaki

---

### Post by bodhi.zazen on 2008-12-19
Just some info on wubi :)

Wubi installs Ubuntu into a file on teh Windows partition and uses the windows boot loader to boot. It is otherwise similar to dual booting and is not virtualization.

WUBI FAQ : [http://www.goodbye-windows.com/downloads/mirrors/cutlersoftware.com/ubuntusetup/wubi/old/faq.html](http://www.goodbye-windows.com/downloads/mirrors/cutlersoftware.com/ubuntusetup/wubi/old/faq.html)

_General Information_ : The live CD allows you to try out the OS before you install. It will not touch the hard drive unless you tell it to.

If you do a "Standard" install make sure you first back up your data. While data loss is rare, it is but a mouse click away from destroying your data. Make sure you understand partitions (Linux does NOT use c:\ or d:\ to refer to partitions).

Otherwise have fun :)

---

### Post by balaknair on 2008-12-21
Hi Wovaki.

> **If I use Wubi to install, the sleep/hibernate/resume wont work only on Ubuntu, or on my Windows boot too? Will this be fixed after I uninstall?**
Sleep/Hibernate/resume will work normally in Windows, but not in Ubuntu installed via Wubi.

> **If I partion my drive to dual boot, and decide I want to get rid of one or the other, is it easy to do, and does it keep all my files intact for the OS I'm keeping?**

There are certain precautions you should take, like backing up all your important data, whether you're partitioning your hard drive or just applying a major system update in Vista. As Bodhi Zen said, accidents are just a mouse click away. 
Under normal circumstances, it's usually a painless procedure, using just the free space on your hard drive, and files under Vista will not be modified. **But you should defragment the drive from within Vista before starting the install process.**
Removing Ubuntu(on its own partition, not Wubi) is easy, if you know how. If you plan to remove Ubuntu later, you can either
a) make a backup copy of the Master Boot Record(that's the first few bytes on your hard disk that tells the system where to find the OS to boot from) before you install Ubuntu. This can be done with tools like HDHacker or Super Grub Disk, and can be used to restore/repair the MBR.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

b) alternatively, if you have a Vista install DVD, you can use that to repair the MBR.
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)

> Another question, **if I install Ubuntu with Wubi, will it be as secure as partitioning my drive, for viruses and stuff like that?**
Because I know that basically the Ubuntu installation is stored right inside the Windows boot.
I'm really not too sure about that. I don't think there is any difference, insofar as in either case Windows executables will not run under Linux unless you have Wine installed(and even then it'll ask for a confirmation before installing anything). So chances of a virus getting installed is pretty low. On the other hand, a virus may get downloaded on to your system even on Linux, though it won't be able to do any harm till you run it from inside Windows. My advice is to always use safe browsing practices regardless of OS, don't install apps from untrusted sources, and use an antivirus app(even on Linux- I use Clamav on Ubuntu and scan all downloaded files with it under Linux, and if I have to access them from Windows, I scan them again with BitDefender).

> **What about Vista compatibility?**
I heard that the Live CD is not compatible with Windows Vista, but will it work fine and partition everything alright with Windows Vista?


I've heard of problems, but never run across one myself. So I'm afraid i can't really offer much help there. In all the Vista machines I've installed Ubuntu as dual boot on, I haven't come across any problems(of course on my own Vista machine, it would involve removing Vista and installing WinXP first).

> My computer also has buttons on it for raising the volume, and controls that work with Windows Media Player (Back, Play/Pause, Forward, Stop, Mute) as well as some "QuickPlay" buttons that launch Windows Media Center. **Does anyone know if any of these things are compatible, or if its possible to make them compatible?**

I haven't installed on an HP laptop yet(mostly Lenovos and Dells and a few Acers), but I have installed on a Compaq laptop. On all the laptops I've installed Ubuntu on, Ubuntu Gutsy Gibbon gave me a few minor problems but Hardy Heron(8.04) worked flawlessly out of the box, except for inbuilt webcams, which needed some tweaking. And with Intrepid Ibex(8.10) even the webcams worked out of the box. That includes the multimedia keys and special function keys. So far the tweaking I've done on most machines after installing Intrepid is adding restricted packages and drivers, enabling Compiz and changing the theme and wallpaper. So I don't think you'll have much trouble there.

And yes it is possible to make them perform even better, modified to your specific tastes using the 'Keyboard Shorcuts' tool from the System preferences menu.

I hope this was helpful.

---

### Post by theozzlives on 2008-12-21
The nice thing about partitioning is you can have a seperate /home partition (invaluable if you ever need to re-install).

---

### Post by balaknair on 2008-12-21
> Wubi installs Ubuntu into a file on teh Windows partition and uses the windows boot loader to boot. It is otherwise similar to dual booting and is not virtualization.

No it's not virtualization, as in there is no host OS under which Ubuntu runs. What I meant to say was the file Ubuntu is installed into(named root.disk) is a virtual disk image.
The MBR and partition tables are not modified in a Wubi install; instead, AFAIK, it modifies the boot.ini file(bootrec.exe in Vista) so that it adds a line pointing to the linux loader(located somewhere within the C:\Wubi folder)--> initiates the Linux kernel, with initramd is mounted into RAM -->  this now mounts the virtual disk image(root.disk, located somewhere within the C:\Wubi folder)--> the file structure within the root.disk is set as the loopback device--> now the loopback device is booted as root / and now boots normally while initramd are all offloaded from RAM--> Ubuntu boots from the root.disk.

This is what I could make out from stuff I read(in response to another thread about problems with Wubi). Feel free to correct me if I'm wrong(in fact if you could point out mistakes I'd appreciate that; also could anyone point out any good articles about this sort of thing, I found the Wubi documentation pretty underwhelming).

Just my $0.02 worth.

---

### Post by Wovaki on 2008-12-21
Hello everyone.

I tried Ubuntu for the first time last night using the Live CD.
I must say that I do like it, and mostly everything worked fine.

The only thing I think I have a problem with so far is the screen resolution. It starts at 800x600 and the only other option is 600x400. My screen resolution is 1280x800 when I'm on windows, and its the way I like it. With 800x600 on Ubuntu, some windows don't fully fit on the screen.

I'm wondering if there is anyway to fix this?

> Removing Ubuntu(on its own partition, not Wubi) is easy, if you know how. If you plan to remove Ubuntu later, you can either
a) make a backup copy of the Master Boot Record(that's the first few bytes on your hard disk that tells the system where to find the OS to boot from) before you install Ubuntu. This can be done with tools like HDHacker or Super Grub Disk, and can be used to restore/repair the MBR.

**So I have to install something BEFORE I partition my drive to install Ubuntu with a dual boot?**

If I install Ubuntu with Wubi, then decide I want to partition my drive for a dual boot, is there a way to do this without losing all my stuff on the Ubuntu boot, or do I have to uninstall with Wubi, then partition my drive?

Thanks!
Wovaki

---

### Post by Wovaki on 2008-12-21
Sorry, I forgot something:
I know running Windows executables will not work in Linux, but what if I downloaded a media file, such as music or a video clip, and it had a virus in it, (using Wubi) will I still be protected from that virus?

Thanks
Wovaki

---

### Post by billgoldberg on 2008-12-21
**1. If I were to install Ubuntu using Wubi, and keep windows (dual boot?) would this be the same as just using the live cd to partition my hard drive?**

No.
[B]
2. If I downloaded a file on the Ubuntu boot that had a windows virus in it, and then switched to the Windows boot, would that virus then be able to work and do whatever it is supposed to do? (Security is the main reason I want to switch).[/B]

No. As long as you don't copy the file to your Windows partition it will do nothing to either OS.

[B]3. Using Wubi, is any of my Windows files or anything going to be deleted when I install/uninstall, or whatever else using Wubi?
[/B]

No.

[B]My next question doesn't really have anything to do with Wubi specifically, but using the Live CD, can I check to see if all my hardware is compatible, and can I do almost anything (browse the internet, test out apps, etc.) from the Live CD without installing Ubuntu?
[/B]

The live cd will give you a good indication of what will work and what not.

Some things like your graphics card driver you can only install after installation.

I don't know if you can download apps using the live cd, I don't think so.

Browsing the web using the live cd will work just fine.

That is over an ethernet connection or a out of the box supported wireless card.

If you need to install the wireless driver, it won't work using the live cd.

**Also will using the Live CD change anything, like delete stuff on my hard drive or anything like that?**

No. 

The live cd will never touch your HDD. 

You can mount your HDD and delete stuff manually (or copy it to another drive, great for rescueing a virus infected Windows machine).

But by itself it won't touch the HDD.

---

If you are afraid to install Ubuntu on your pc.

Just use some virtualization app to install Ubuntu in.

I suggest you try out Virtualbox.
 
If you don't know what virtualization is, take a look at this video:

[http://www.youtube.com/watch?v=lA52Y7I2hCE](http://www.youtube.com/watch?v=lA52Y7I2hCE)

---

### Post by billgoldberg on 2008-12-21
> **Wovaki said:**
> Sorry, I forgot something:
I know running Windows executables will not work in Linux, but what if I downloaded a media file, such as music or a video clip, and it had a virus in it, (using Wubi) will I still be protected from that virus?

Thanks
Wovaki

A Windows virus will never work on Linux (Ubuntu).

So yes, you'll be protected.

---

### Post by albinootje on 2008-12-21
> **billgoldberg said:**
> A Windows virus will never work on Linux (Ubuntu).

So yes, you'll be protected.

Never say never..
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031) (article from 2005)
and Wine is getting better every day ;-)

---

### Post by balaknair on 2008-12-21
Hi Wovakis

1) Screen Resolution: You will need to enable non-free hardware drivers to get the best out of some hardware like nVidia and ATI graphics cards, Broadcom WiFi cards etc.
You will be asked if you want to do so upon first login into Ubuntu after installation. Once the proprietary drivers are installed and enabled, you will be able to get higher screen resolutions.
Some newer graphics cards might require a couple of workarounds to get the best results though(especially ATI cards).

2) Installing something before partitioning/installing Ubuntu- No that's not what I meant. The options are needed only **if you want to remove Ubuntu and don't have a Vista install DVD**( With SuperGrubDisk, there is no installation(it runs off a bootable CD). HDHacker you have to install on Windows and create a bootable rescue disk. ). It's a hack or workaround, and needed only if you don't have a Vista DVD.

3) To move the Wubi Ubuntu to its own partition
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

4) Viruses: you will be protected as long as the infected files remain on the Ubuntu partition/disk and are not accessed from Vista. Running Windows executables within Linux AFAIK does nothing to your system. All the same, scan downloaded files with an antivirus program even on Linux(agreeing with albinootje there- Never say never).
You can use Clamav (Applications menu> Add/Remove Programs--> search for and install the 'Virus Scanner') or AVG for Linux ( [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl) )

---

### Post by Wovaki on 2008-12-21
Thanks, I have to defrag my computer, then I think I will try a Wubi install.

I **Don't** have the vista install disk sadly, so could you please walk me through what I should do before installing Ubuntu as a dual boot, just in case I want to get rid of it later on.

Although I wont need to worry about this if I install with Wubi, right?

Thanks!

---

### Post by bodhi.zazen on 2008-12-21
> **balaknair said:**
>  <clip> ...

This is what I could make out from stuff I read(in response to another thread about problems with Wubi). Feel free to correct me if I'm wrong(in fact if you could point out mistakes I'd appreciate that; also could anyone point out any good articles about this sort of thing, I found the Wubi documentation pretty underwhelming).

That is a very nice understanding / summary of who wubi works, thank you for posting that.

---

### Post by balaknair on 2008-12-21
For a Wubi install, to remove ubuntu just open the Windows Add/Remove Programs menu, select Ubuntu and click Uninstall. Reboot and you're done.
For more options and troubleshooting, you might find this guide useful:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

For uninstallation related info specifically in the above guide,
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)


For the Ubuntu-on-its own-partition-install, if you don't have the Vista DVD, I suggest you use Super Grub disk to repair the MBR.
For an illustrated guide on how to use SGD to repair a Windows installation, check this page:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

Hope this is useful.

Have fun with Wubi and Ubuntu.

---

### Post by Wovaki on 2008-12-21
Thanks for all your help, hopefully I can get this up and running alright. :D

Wovaki

---

### Post by HavocXphere on 2008-12-21
Firstly, congrats on the decision. I've been using linux as my main OS for about a month now. The only reason why I've still got Vista installed is for games.

Regarding the Virus:

> 2. If I downloaded a file on the Ubuntu boot that had a windows virus in it, and then switched to the Windows boot, would that virus then be able to work and do whatever it is supposed to do? (Security is the main reason I want to switch).
99,99% of viruses *cannot* run under linux, so they'd be dead in the water before they started. However,if you download a virus under linux, transfer it to the windows partition and then run the file **under windows**, the you'd activate the virus.

Also, there are attacks that work on *all* operating systems. e.g. redirecting you to a fake banking website. To counter these, you might want to check out Opendns.

---

### Post by balaknair on 2008-12-21
> **bodhi.zazen said:**
> That is a very nice understanding / summary of who wubi works, thank you for posting that.

You're welcome :P

If you found it useful, the pleasure was all mine.

---

### Post by PatrickMoore on 2008-12-21
> **Wovaki said:**
> Hello everyone!

This is my first post here, and I'm thinking about switching from Windows (Vista) to Ubuntu. Right now its a little scary, since I have never done this before, and I will have no clue what I am doing.

I'm hoping I can get some questions answered to help me along.

Since I am using Vista, I plan to install Ubuntu using the Wubi installer, so I have a few questions about that:

[B]1. If I were to install Ubuntu using Wubi, and keep windows (dual boot?) would this be the same as just using the live cd to partition my hard drive?

2. If I downloaded a file on the Ubuntu boot that had a windows virus in it, and then switched to the Windows boot, would that virus then be able to work and do whatever it is supposed to do? (Security is the main reason I want to switch).

3. Using Wubi, is any of my Windows files or anything going to be deleted when I install/uninstall, or whatever else using Wubi?[/B]


My next question doesn't really have anything to do with Wubi specifically, but [B]using the Live CD, can I check to see if all my hardware is compatible, and can I do almost anything (browse the internet, test out apps, etc.) from the Live CD without installing Ubuntu?

Also will using the Live CD change anything, like delete stuff on my hard drive or anything like that?[/B]


Thanks, any help is greatly appreciated!
Wovaki

i had more issues with dual booting xp than having a pure linux system.i'd say ditch the vista, go with intrepid

---

### Post by Wovaki on 2008-12-21
> **PatrickMoore said:**
> i had more issues with dual booting xp than having a pure linux system.i'd say ditch the vista, go with intrepid

I don't think I'm ready to say goodbye to Windows just yet.

About the Anti-Virus:
ClamAv/AVG will scan for both Linux and Windows viruses, right?

Thanks!
Wovaki

---

### Post by bodhi.zazen on 2008-12-21
> **Wovaki said:**
> Hello everyone.

I tried Ubuntu for the first time last night using the Live CD.
I must say that I do like it, and mostly everything worked fine.

The only thing I think I have a problem with so far is the screen resolution. It starts at 800x600 and the only other option is 600x400. My screen resolution is 1280x800 when I'm on windows, and its the way I like it. With 800x600 on Ubuntu, some windows don't fully fit on the screen.

I'm wondering if there is anyway to fix this?

Yes, but we need to know what videocard you have.


> **So I have to install something BEFORE I partition my drive to install Ubuntu with a dual boot?**

If I install Ubuntu with Wubi, then decide I want to partition my drive for a dual boot, is there a way to do this without losing all my stuff on the Ubuntu boot, or do I have to uninstall with Wubi, then partition my drive?

Thanks!
WovakiDual booting and wubi are both dual booting, but they are very different.

With wubi you install from windows. With traditional installation, you boot the CD, repartition your hard drive, and install.

There are many guides on how to install both wubi and the standard method, check the ubuntu wiki.

You can convert wubi to a standard partition, but it is somewhat complex and IMO it may be easier to just delete wubi and install using the traditional methods.

Make sure you understand how linux refers to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) 



> **Wovaki said:**
> Sorry, I forgot something:
I know running Windows executables will not work in Linux, but what if I downloaded a media file, such as music or a video clip, and it had a virus in it, (using Wubi) will I still be protected from that virus?

Thanks
Wovaki

Viruses ares essentially a non-issue on Linux. There have been a few exceptions, but they do not damage system files and are easily repaired. All known viruses have been patched long ago.

There are some people who repoort FUD re: wine, but wine is not windows and the wine developers are very much security conscious and will patch the code. Most viruses that have run on wine come either from people purposly trying to run the code or people that have misconfigured wine. wine is no more or less a risk then any other linux application and linux is NOT invulnerable. The Linux way, however, is to Keep your system up to date.

See this article :

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

See the stickies in the security section to learn about Linux security.

---

### Post by balaknair on 2008-12-21
> **Wovaki said:**
> I don't think I'm ready to say goodbye to Windows just yet.

About the Anti-Virus:
ClamAv/AVG will scan for both Linux and Windows viruses, right?

Thanks!
Wovaki

There aren't any Linux virii exploits in the wild at present(though of course that could change) and Open Source projects generally get security patches/updates very quickly once a vulnerability is discovered.
The need for an antivirus application on a Linux machine is more to prevent infection of Windows PCs(as in a network with both Windows and Linux PCs) or filesystems(such as you would see in a dual-boot machine). Linux-based antivirus applications are predominantly used on NFS and mail servers which may send files/mail to computers running other operating systems(usually Windows), and generally use definitions for, and scan for, **all known viruses for all computer platforms**, including Mac and mobile OS.

It's just good sense(not obligatory, but desirable) to use an antivirus app on Linux too, especially if you dual boot or if you share files with Windows machines. My personal recommendation would be to opt for ClamAV- open source, available from the Ubuntu repositories, and with pretty good detection rates(better than many commercial apps). AVG, Avast and Avira also offer free(for personal use) Linux versions of their antivirus programs, but are all closed source, and not available in the Ubuntu repositories(to the best of my knowledge).

A pretty long post in reply to a short question :D 

I hope you find this useful.

---

### Post by Wovaki on 2008-12-21
I think my Graphics card is Nvidia.

About the AntiVirus, is there any other reason to use ClamAv, besides being Open Source?

What do I need to type in to find the ClamAV in the Add/Remove Programs?

Also, is a Defrag needed to install Ubuntu with Wubi, or is that only for partioning the drive?

Thanks for the help!

---

### Post by bodhi.zazen on 2008-12-21
> **Wovaki said:**
> About the AntiVirus, is there any other reason to use ClamAv, besides being Open Source?

I can think of no good reason you should use antivirus in Linux, did you read the link I gave you ?

Linux security is not the same as Windows.

---

### Post by Wovaki on 2008-12-21
> **bodhi.zazen said:**
> I can think of no good reason you should use antivirus in Linux, did you read the link I gave you ?

Linux security is not the same as Windows.

Ok, but the main reason I would want it is to make sure I don't send a virus to windows using friends.


I was also wondering, what is the difference between Gnome and KDE?
Is it just the look?

Thanks

---

### Post by bodhi.zazen on 2008-12-21
> **Wovaki said:**
> Ok, but the main reason I would want it is to make sure I don't send a virus to windows using friends.

You will not.. Viruses do not propagate on Linux. The only way to "pass on" a virus is if you receive an infected file and pass that file on.

> I was also wondering, what is the difference between Gnome and KDE?
Is it just the look?

Thanks

They are both Desktop Environments. They each have a unique look and feel, and a different set of default applications, but at the core they are the same OS.

I suggest you try both.

---

### Post by balaknair on 2008-12-21
Hi Wovaki

Re ClamAV- the GUI version is available from the 'Universe' repositories. In Add/Remove programs, search for 'Virus scanner' or 'clamav'. It will download and install all needed files for you.
(I think the Universe repos are enabled by default, I don't remember for sure. Open System Menu> Administration> Software Sources--> On the first tab, the box next to 'Community maintained open source software(Universe)' must be checked) 

I recommend ClamAV over the other options since 
- it's a great product, 
- it's got better reviews than the closed source versions, 
- it works well in Ubuntu(some antivirus utilities are desgned specific to certain distros like Red Hat or SUSE), 
- it has an easy-to-use GUI in Clamgtk(which is what you get when you install 'Virus Scanner' in Add/Remove Programs), and because 
- it's available from the Repos, installation is easier(no need to hunt down the Linux version download page on the vendor's website, and then download the product/version you need, download and install). 
- Another very important reason(to me)- being open source, you can be pretty sure it'll continue to be maintained and updated by the company and the community. I've known proprietary antivirus apps discontinue their free Linux versions, and this isn't that likely with ClamAV.

---

### Post by balaknair on 2008-12-22
Hi

> I can think of no good reason you should use antivirus in Linux, did you read the link I gave you ?

Linux security is not the same as Windows.

> You will not.. Viruses do not propagate on Linux. The only way to "pass on" a virus is if you receive an infected file and pass that file on.


I must say I don't totally agree with you there. 

While Linux has no active virii in the wild at present, and is coded to be more secure by design(ie, it's not the virus magnet Windows is) and it's much harder to create a virus that infects a Linux PC unless the user gives it permission, the greatest vulnerability in any OS is the clueless user, not the code. Which is why malware authors are turning more to social engineering to infect PCs as vulnerabilities get patched.
An antivirus app on Linux would help in preventing 'passing on' malware to friends or to your own Windows installs, plus it's rather like insurance or locking your doors, as much for peace of mind as for security.
I do agree that just adding an antivirus is useless if you do not also follow secure computing habits. An antvirus app is an **addition** to secure computing habits, **not a replacement**. In the case of an outbreak of exploits for Ubuntu, the antivirus app would not be of much use, but using common sense and safe practices on your computer could prevent you becoming a victim.

Just an anecdote: I recently fixed a PC that had become excruciatingly slow and crash-prone for a friend currently in college(he's using XP). His PC had been used by many of his friends, all logging in with admin privileges(the default in XP), and a few of them feel Internet Explorer is so much better than Firefox(Firefox 'doesn't feel comfortable' was the reason one gave), and you guessed it, the system was infested with malware. When I asked him about what Antivirus app he'd been using, he said he had Norton- which turned to be an expired version and had not been updated in over an year. And the friend who had found Firefox 'uncomfortable', had found a great free antivirus app named Antivirus 2009. It seems he'd been browsing 'random stuff', with IE and no current AV protection, when he saw a warning that a virus had been found on his system, follow this link etc. etc. He did, there was an 'online scan' which 'found' over 200 viruses on his system. It offered to fix them for free if he would only 'Click here', so he did, and installed a Trojan dropper. To cut a long story short, it took hours to clean up that PC and get it up and running. 
This might not happen on Ubuntu at present, but if someone were to write a similar exploit for Ubuntu, and actually get the user to install the malware(in the guise of Firefox addons[ [http://www.itproportal.com/articles/2008/12/05/trojan-phishing-malware-disguises-firefox-add-/](http://www.itproportal.com/articles/2008/12/05/trojan-phishing-malware-disguises-firefox-add-/) ], or screensavers, or codecs), don't you think an updated antivirus app would help? The Firefox addon for example, is OS-independent, using javascript, and i think would run on Linux as well, if the user installed it. 

My take on security= Fully patched OS and apps + updated and configured antivirus, firewall, anti-spyware(Rootkit scanners and suchlike are also available if you're suitably paranoid about security like I am) + Firefox with NoScript, AdBlock Plus and Secure Login addons(and minimise the number of other addons, and install addons ONLY from the Mozilla addons repositories) + disable HTML in your eMail client + most important of all- **safe browsing habits** and a healthy dose of cynicism.

---

### Post by balaknair on 2008-12-22
@Wovaki: re Gnome vs KDE

Thorny issue here. Both have their diehard fans and detractors.

Gnome is the default in Ubuntu- it's simple and stable, and focuses on usability. Customising/Tweaking Gnome down to the last detail can be challenging to a novice.
KDE is prettier and far more customisable(at least in KDE 3.x, in KDE 4.x much of the customisability is hidden much as in Gnome), you can specify how each component of the desktop environment will look and behave. As a former KDE user, I can also vouch for how too much tweaking can mess up your install(you could say I was spoiled for choice, coming from Windows and seeing so many options I had to try them all :P ). KDE 3.x also seems more resource intensive than Gnome(all that prettiness comes with a price), though Gnome itself is getting more and more bloated with each release-nowhere near the Vista class, and still less bloated than XP, but still not the best choice for low-spec systems(<1 GHz, 512MB RAM).
Both come with a default set of common applications, but these usually work well on both desktop environments(eg: I use Amarok and Digikam even after switching to Gnome, Rhythmbox and F-Spot just don't compare).

For beginners to Linux at present, I would suggest starting out with Gnome for now. The current version of KDE 4 is still at an early stage in its evolution, and not fully mature. I found it stable and usable, but wouldn't work well with Compiz, and the inbuilt 3D desktop effects wouldn't work(kept crashing, apparently it's something to do with conflicts with the nVidia drivers, and hopefully will be fixed in KDE 4.2.x). The phonon audio subsystem also required a bit of tweaking to get it working. I'm waiting for KDE 4.2 wih Kubuntu 9.04 to give it another try.

Recommendation: Try both via the Live CDs(Ubuntu and Kubuntu) to get a feel of how they look/feel. If you want something easy and stable at present- go for Gnome.
If you want to try something 'radically different' and bleeding edge- try KDE 4.

---

### Post by Wovaki on 2008-12-22
Thanks for the replys.

I just finished Defraging my computer, and I am going to install Ubuntu using Wubi.

But how do I try the KDE environment using the Live Disk? I did not see an option to choose it.

Thanks!
Wovaki

---

### Post by bodhi.zazen on 2008-12-22
> **Wovaki said:**
> Thanks for the replys.

I just finished Defraging my computer, and I am going to install Ubuntu using Wubi.

But how do I try the KDE environment using the Live Disk? I did not see an option to choose it.

Thanks!
Wovaki

You need to download the Kubuntu desktop CD.

---

### Post by balaknair on 2008-12-22
KDE is available in Kubuntu, the KDE flavoured version of Ubuntu. On the Ubuntu CD, you find Gnome.
Similarly, Xubuntu uses another desktop environment called XFCE(which is not as 'pretty' as KDE or Gnome, but is very lightweight and is better suited to older systems with fewer system resources).

The Kubuntu CD can be dowloaded from 
[http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu)

Xubuntu CD
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

You can also install KDE and/or XFCE on a regular Ubuntu(Gnome) desktop as well, using the command 'sudo apt-get install kubuntu-desktop' or sudo apt-get install xubuntu-desktop'(but this can clutter up the applications menu a bit, with both KDE and Gnome apps getting mixed up, some of them performing the same tasks). This can't be done on the Live CD though. 
To try the KDE environment from the Live CD you have to use the Kubuntu Live CD.

---

### Post by media_ on 2008-12-22
I just took the plunge this past week and decided to install ubuntu.  And am I ever happy.  I love ubuntu thus far and it seems to really fit me.  I still kept xp on a seperate partition and am running ubuntu on it's own 20gb partition I made.  I have no idea why I waited so long.  I had tried a few live cds like knoptix and wasnt ever happy with it, ubuntu is just a great all around package.  Im still a newbie and am still learning, but that is what makes this so much fun for me.  I look forward to participating in the forums and eventually being able to help others out.

---

### Post by Wovaki on 2008-12-22
Well I just installed Ubuntu using Wubi, and I'm on it now! :D

A couple questions, why does it take so long to shut down?
I get a blank screen for a bit after it shows the Ubuntu logo, and the progress bar. Then something pops up about a Process being killed and it shuts down.

I'm also at a low resolution and cant get a higher one. And when the Drivers update thing pops up it allowed me to update my wireless driver, but not my graphics driver.

Should I go to: Visual Effects, then change it to normal so my graphics card (Nvidia) will update?

Thanks.

---

### Post by balaknair on 2008-12-22
Hmmm.

**Wubi shut down**: I'm not an expert on Wubi-related issues, but I think that's par for the course with Wubi, taking a little longer to shut down than a normal Ubuntu install. Basically it's because there're more a few extra steps involved. The process being killed isn't a problem either(it's what goes on behind the progress bar splash screen anyway). As I stated earlier in this thread, Wubi doesn't give you the same performance as a normal Ubuntu install, but it's an easy way to try out Ubuntu before committing to a switch.

**nVidia**: 
Now here we'd need a little extra info- what model/series is the nVidia card you're using? Older cards do not need the proprietary nVidia drivers. 
**NOTE:** *If you're already running 3D Visual effects, you've probably got the restricted drivers in use.*

What I suggest: to help us find what hardware(and drivers) you're using, open a terminal(Applications menu> Accessories> Terminal) and type in (or copy-paste) the command 

*lspci -v*

This will output a longish bit of text describing your hardware, and your graphics card info should be there close to the end. Copy and paste those lines here.

*eg:* this is what I get on my desktop, right near the bottom of the list-

 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at e800 [size=128]
	[virtual] Expansion ROM at fbee0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

Option 2:
You could also install the drivers yourself from Add/remove programs or try running the Hardware Drivers Manager (System menu> Administration> Hardware Drivers) 
If it sees your GPU needs special drivers, you can enable the restricted drivers there.

Option 3:
If you're sure you have an nVidia card, you can use Envy, which will fetch and install the latest nVidia drivers for you.
To install, type in a terminal-

*sudo apt-get install envyng-gtk*

Then run Envy from Applications> System Tools> Envy. It's a pretty nifty tool but is designed only for nVidia and ATI cards.
The Envy author's webpage- [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Wovaki on 2008-12-22
I installed some Ubuntu updates, and the shut down is faster now.

I got my resolution fixed too.

One thing, what program should be used to configure Ubuntu's firewall?

Thanks.

---

### Post by balaknair on 2008-12-22
> **Wovaki said:**
> I installed some Ubuntu updates, and the shut down is faster now.

I got my resolution fixed too.

One thing, what program should be used to configure Ubuntu's firewall?

Thanks.

That's good to hear. So that probably means the video drivers are already in use.

Firewall: try Firestarter
Applications menu> Add/Remove programs> in the search box type 'firewall' to get a list of firewall GUIs, Firestarter is the most popular one, rated 4 stars

The firewall in Ubuntu(IPTables) doesn't need much configuration though, since it's already enabled and set to a secure setting by default.

---

### Post by Wovaki on 2008-12-22
Alright thanks.

I was just wondering, does dial-up work on Ubuntu?

[Edit]
I'm also having a small problem with program title bars, sometimes they go white, and I have to click the minimize button or something in order to restore its color.

---

### Post by balaknair on 2008-12-22
*"I was just wondering, does dial-up work on Ubuntu?"*

If you have a hardware modem, yes it will. Many laptops have software 'winmodems' though, which can be tricky to get working in Linux.
I've had to set up dial up net access on just one such laptop, which I did following instructions listed here

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Wovaki on 2008-12-22
Alright, as far as I know mine is hardware. :confused:

What about the title bar stuff?

Thanks

---

### Post by balaknair on 2008-12-22
I'm talking about onboard internal modems on laptops(external modems will of course be hardware modems).
To check the dial up modem and see if it's being detected, plug it in and in a terminal, type the command 
*wvdialconf*

This will let you know if the connected modem is detected or not.

About the program title bars:
I think what you're referring to is the title bars getting grayed out when unfocussed like what you see in the screenshot(the focussed window in front has the orange/brown titlebar, the unfocussed window in the background has the geryish titlebar). That's just the default behavior, not a bug. You can also change the way it looks from System> Preferences> Appearance--> Themes. You can also customize the title bar alone in a theme (Themes>customize--> Window decoration)
Just take a look at the screenshot to see if that's what you're experiencing.

---

### Post by Wovaki on 2008-12-23
No, it grays out sort of like that, except sometimes even on active windows, and the Maximize and Exit buttons are not visible, and the minimize button is only partially visible.

I'm on my windows boot right now, but I will take a screen shot soon.

Thanks.

[Edit]
Here is a screen shot from Firefox.
[ATTACH]97360[/ATTACH]

And that is when it is active.
Thanks

---

### Post by balaknair on 2008-12-23
OK, I see what you mean.
I'm afraid that's something I've never come across before, not sure what's causing it.
Is that the default theme you're using? And is it just the title bars that are affected or do any other buttons like 'Save', 'Cancel' or the toolbar also show glitches?
Could you try changing the Window border in Themes and see if this still happens? Maybe try the clearlooks theme or something similar.
The most likely cause I can think of is it might be a glitch in the theming engine.

---

### Post by Wovaki on 2008-12-24
> i wouldn't know but vistas partition editor is really easy just right click computer go to manage then click the tab for disk management then right click the c drive and schrink the volume by whatever size you want to allocate to ubuntu then boot into live cd and make sure to install to all contiugus free space or something along that line

Would this work?
When I checked (using the method above) windows said there was around 23GB of memory I could shrink, would this be enough for a Linux install?

And does that mean that I would have a 23GB hard drive pretty much?

Thanks!

---

### Post by balaknair on 2008-12-24
I think that would mean you have 23 GB free space.
Ubuntu would need a minimum of 5 GB, so I guess you could free up ~15GB space for Ubuntu, which should be enough for now, till you get the hang of Ubuntu and have made up your mind regarding switching.

Since you installed Ubuntu via Wubi, I'd suggest using it for a couple of weeks and then maybe consider a separate Ubuntu install.

---

### Post by WASHAD on 2008-12-24
Why do I think my reply will give you any information that you don't already have? Well, I'm pretty new to Ubuntu as well, though I have tried it several times in the past. 

If you had asked me a couple of revisions ago if it were a good idea to make the switch to Ubuntu, I'd have told you to run for the hills. The latest editions of 8.10, though, is really nice. For the first time everything works and I haven't had to get under the hood with the command line. 

I'd say go for the full on partition; it is really easy. If you use the default install option, you can just adjust the slider with the mouse to adjust the partition size as you want it and the rest takes care of itself. 

I would definately dual-boot though. 

SteveJ

---

### Post by Wovaki on 2008-12-24
Alright, so what would be a good amount of space to use for a Ubuntu install?

I'm on Wubi right now, but I would like to make a partition for Ubuntu soon, I really like it so far. :D

I switched to Clearlooks, and so far it seems to be fine.
I was on Human before.

Is there any way that I can RIP DVD's, so that I can watch them on my computer without having the dvd in?
I know you can rip a iso, then burn that to a dvd, but can I watch them on my computer?

Thanks

---

### Post by balaknair on 2008-12-24
There are quite a few apps to rip DVDs.

Application Menu> Add/Remove Programs> search for DVD rip to see the list of available applications.

I personally use DVD-rip, it transcodes the DVD into a mpeg or avi file

---

### Post by Wovaki on 2008-12-24
I can't find dvd-rip in the add/remove.

But I found this command on a guide will this install it?
> sudo apt-get install dvdrip

---

### Post by sportscrazed2 on 2008-12-24
i ran ubuntu in wubi for about a week before i decided to do a full dualboot and it's about as fast maybe a little faster than wubi. and no windows viruses shouldn't carry over to windows

---

### Post by balaknair on 2008-12-24
You'll have to enable the 'Multiverse' repositories

System menu> Administration> Software Sources---> enable the entry 'Software restricted by copyright or legal issues(multiverse)'

Now either

**a)** Open **Add/Remove**--> You will be asked to reload the list, click OK--> the list will be updated--> In the 'Show' menu next to the 'Search' box, select 'All available applications' --> search for dvd rip--> select the app you want---> click 'apply changes'

or

**b)** **in Terminal**-

*sudo apt-get update*

*sudo apt-get install dvd-rip*


you can now access dvd-rip from Applications menu> Sound & Video> dvd::rip

---

### Post by Wovaki on 2008-12-24
Thanks, I got it. :D

I will try Ubuntu out some more on Wubi, and maybe in a week or two I will partition my drive, and give Ubuntu its own partition.

Thanks

---

### Post by balaknair on 2008-12-24
> **Wovaki said:**
> Thanks, I got it. :D

I will try Ubuntu out some more on Wubi, and maybe in a week or two I will partition my drive, and give Ubuntu its own partition.

Thanks

Great.
You're welcome.
Enjoy :popcorn:

---

### Post by Wovaki on 2008-12-25
Thanks for all your help!

But I have one more request.

Could you please help me get onto dial up with my Ubuntu boot?

I only have dial up right now, and I have to use windows for it. :(

Thanks

---

### Post by balaknair on 2008-12-25
OK, I'll try

The best set of info on this subject I know of is here:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)


First we need to know what modem you're using and/or if it is supported in Ubuntu.

1) Connect the modem/cable while logged into Ubuntu.
Open a terminal and type

```
wvdialconf
```

2) If your modem is detected, it's usually fairly simple from here on to configure your connection.
If it is not detected, we need to find some workarounds.
In any case, you can check [[COLOR="DarkOrange"]_here_[/COLOR]]("http://xmodem.org/modems/index.html") for a list of supported laptop modems and see if your model is supported or not.

---

### Post by Wovaki on 2008-12-25
Ok, I will try that.

Just to let you know, my modem is built into my laptop, all I do is plug in the phone cord and click connect, on windows anyways.

Thanks

---

### Post by Wovaki on 2008-12-25
I tried that, and it could not detect my modem.

I don't even know how to find out what my modem is so I can check that site that lists the compatible modems.

---

### Post by balaknair on 2008-12-26
Try to find out what modem you have within Windows.
Start > Settings > Control Panel >  System > Hardware > Device Manager > Modems > Modem-->Double click to see the properties--> check the Manufacturer and Product information

---

### Post by balaknair on 2008-12-26
Have to go out for a while(my sister's here for the holidays and I have to take her out for lunch shortly). I'll check back as soon as I get back, though that might take a couple of hours.

I also just thought of something- if it's too much trouble to get your dial-up to work properly with Ubuntu, and you have only dial-up available where you live, you'll have to go through this again when you reinstall/upgrade Ubuntu or if a kernel upgrade messes up the drivers you have installed. I can see two options if you want to switch to Ubuntu full time: getting an external modem to connect to your dial up ISP, or getting a new internet connection- broadband/cable/ADSL- anything you can connect to via the Ethernet port on your PC.

---

### Post by Wovaki on 2008-12-26
_Modem Information_:
Manufacturer: CXT

Thats all I could really find on here, tell me if more information is needed.

Hopefully I can get this up and running, I'm tired of switching to windows to go on the internet. I also noticed that on my Ubuntu boot I don't have the "Network" in my system > administration.

I typed "network-admin" in the terminal and it said I don't have it installed, on the help site it says to go to network, or type "network-admin" in the terminal to set up dial up, but I can't install it since I can't get online with Ubuntu.

Is there a way to download on windows, so I can transfer it with a USB drive?

Thanks

---

### Post by balaknair on 2008-12-26
You can download network-admin from the packages.ubuntu server here
[http://packages.ubuntu.com/intrepid/gnome-network-admin](http://packages.ubuntu.com/intrepid/gnome-network-admin)

---

### Post by Wovaki on 2008-12-26
Alright I will download those now.

I guess its a good thing I kept that md5checksum thing installed to check the files. :)

I'm also downloading gnome-ppp which is supposed to do something with dial up as well.

I will let you know how things turn out!
Thanks

---

### Post by balaknair on 2008-12-26
CXT= Conexant

[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

Conexant does not provide Linux drivers. Commercial drivers may be purchased from Linuxant for $19.99. IMO it's cheaper to get an external dial up modem or a used PCMCIA Linux comaptible modem. 
The page also mentions some Dell drivers for CXT modems on Dell machines, maybe those will work.

To further identify your modem, you can use scanmodem
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

Wishing you luck.

---

### Post by balaknair on 2008-12-26
Gnome-ppp is a GUI frontend for wvdialconf, lets you set up your dialup connections and manage them, once wvdialconf detects your modem(for which you have to install the drivers first). It's a pretty easy tool. But you have to get your modem to play nice first.

---

### Post by Wovaki on 2008-12-26
Thanks for all your help!

I really appreciate it!!!

---

### Post by balaknair on 2008-12-27
> **Wovaki said:**
> Thanks for all your help!

I really appreciate it!!!

You're most welcome. Glad to be able to help.

**PS:** if you do get your dial-up working on the internal modem on your laptop, do let me know what worked for you. It's one of the issues(along with USB CDMA wireless modems) that bug me the most when I have to install and configure Ubuntu on laptops for friends/family. Sometimes a fix which works on a Dell won't work on an HP or Vaio with the same chipset- it gets pretty frustrating after a while.

---

### Post by Wovaki on 2008-12-27
Well I couldn't get it working...

I tried downloading a driver or something from the link you gave me, it was supposed to be a driver from Dell or something.

But it didn't work, any idea how I can uninstall the driver since its not working?

I think for now I will just go online with Windows when I need to, hopefully soon I will get a better connection than dial-up and wont need to worry about it any longer.

Thanks for your help!

---

### Post by balaknair on 2008-12-27
You might have to restart the system to load the driver module, or maybe do a modprobe, before it can be used. Did you try it after restarting?

If you know the name of the file(package) that you installed, just open Synaptic (System menu> Administration> Synaptic Package Manager), search for the package(I think it would be something like hsfmodem), click the little checkbox> mark for removal> Apply.

You could also just let it be(it's probably not doing any harm).

---

### Post by balaknair on 2008-12-27
Just some more stuff you could try:

It seems the Linuxant commercial drivers offer a free demo license key(but the speed will be limited to 14.4 kbps). For a Wubi install(since it's a temporary setup) I think it could prove useful.

They also provide a Windows based tool to identify your Conexant modem.
[http://www.linuxant.com/drivers/modemident.php#listmodem](http://www.linuxant.com/drivers/modemident.php#listmodem)

Or just download the installer
[http://www.linuxant.com/drivers/hsf/full/archive/cnxtinstall.run](http://www.linuxant.com/drivers/hsf/full/archive/cnxtinstall.run)

Save it to the desktop on Ubuntu, then open a terminal

```
cd Desktop
sudo sh cnxtinstall.run

```
The installer will try to identify the modem and its settings, and if it can connect to the internet, will download and configure the proper drivers. If unable to connect to the net, it will list the appropriate driver file you need. You can then download the drivers from here
[http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)

---

### Post by Wovaki on 2008-12-28
Thanks, I will try these. :)

I appreciate you helping me out so much!

Wovaki

---

### Post by balaknair on 2008-12-28
No problem
Glad to help :D

---

### Post by oldsoundguy on 2008-12-28
there is a distinct chance that if it is an internal modem .. it is a Winmodem, and it will not WORK in any Linux build.

I have a v.92 USRobotics Sportster external modem I used for a long time as a back up before I went to VoIP dialtone.

It virtually loads out of the box.

Also note .. doing updates on a dial up can be a "bring your lunch" occasion.

---

### Post by balaknair on 2008-12-28
> **oldsoundguy said:**
> there is a distinct chance that if it is an internal modem .. it is a Winmodem, and it will not WORK in any Linux build.

I have a v.92 USRobotics Sportster external modem I used for a long time as a back up before I went to VoIP dialtone.

It virtually loads out of the box.

Also note .. doing updates on a dial up can be a "bring your lunch" occasion.

Yep.
It's a Conexant chipset, and AFAIK, CXT on laptops are mostly winmodems.
It's MUCH better to switch to cable/DSL broadband(though not DSL USB modems, also a trouble spot with Gutsy and Hardy, though so far Intrepid has worked just fine with USB modems I've had to set up for friends/family, better than Vista actually).
An external dial-up modem or PCMCIA dial-up modem would be good options for those who have access only to dial-up. Broadband isn't available everywhere.

And yes, updating can be a pain on slow dial up connections. But then again I've found even browsing painfully slow on dial-up. On any OS. Can't be helped. I guess slow Internet is better than no Internet.

---

### Post by mikjp on 2008-12-28
Don't fool around with Wubi and other aliens. 

Just backup your files first. Then format the hard disk with three partitions:

/                (10-20 GB)
/home            (the rest)
/swap            (1 GB)

Install Ubuntu. 

Restore your files from backup to /home/username

It's only rock'n'roll music, but I like. :guitar:

mikko

---

### Post by perl20 on 2008-12-28
dON'T SWITCH to Ubuntu if you are a Windows user.You'll have to learn everything all over again. Unless you are a geek, don't do it. I'm paying for it :(, it's a headache.

---

### Post by balaknair on 2008-12-28
> **perl20 said:**
> dON'T SWITCH to Ubuntu if you are a Windows user.You'll have to learn everything all over again. Unless you are a geek, don't do it. I'm paying for it :(, it's a headache.

Do I smell flamebait?

It takes time and effort to learn something new. If you're not willing to put in that effort, it's best to stick to the devil you know. Many people, including me, have found it worthwhile, the benefits of switching to Ubuntu(and the 'headache' of continuing to use Windows) far outweighing the 'pain' of learning something new(though to be honest, the prospect of learning something new was part of Ubuntu's appeal for me).
Give Ubuntu a try. If it works for you, consider switching, if not return to Windows. You'll find help here in Ubuntuforums for both.


As for your headache,
 
```
Take a tablet Advil 200mg stat, and repeat every 4-6 hours. 
If pain persists, consult your GP.
```
](*,) ---> :)

That's the best advice I can offer for your headache over the internet.

And yes, I really am a doctor(surgeon) in real life.

:D

---

### Post by Wovaki on 2008-12-29
Well I did that and it tried to download stuff, of course I couldn't download it since Ubuntu can't connect to Dial-up.

But it said this:
> Needed package: hsfmodem

Also recommended package: alsa-driver-linuxant

And then it also gave me this:
> 
HSF: [http://www.linuxant.com/drivers/hsf/full/downloads](http://www.linuxant.com/drivers/hsf/full/downloads)
phpHCF: [http://www.linuxant.com/drivers/hcf/full/downloads](http://www.linuxant.com/drivers/hcf/full/downloads)
phpDGC: [http://www.linuxant.com/drivers/dgc/downloads](http://www.linuxant.com/drivers/dgc/downloads)
phpRIPTIDE: [http://www.linuxant.com/drivers/riptide/downloads](http://www.linuxant.com/drivers/riptide/downloads)
phpALSA driver: [http://www.linuxant.com/alsa-driver](http://www.linuxant.com/alsa-driver)

But I don't know what to do from here. Hopefully you could help me out.

Thanks!

---

### Post by balaknair on 2008-12-29
You can download the driver .deb installer file from 
[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)

Choose the version you want from the list given on the page(based on the kernel version).

To know the kernel version, in a Terminal type
```
uname -r
```

Intrepid desktop ships with the 2.6.27-7-generic kernel, so I think that's the one you'll need.
[http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.01full/hsfmodem_7.80.02.01full_k2.6.27_7_generic_ubuntu_i386.deb.zip](http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.01full/hsfmodem_7.80.02.01full_k2.6.27_7_generic_ubuntu_i386.deb.zip)


You'll also need the alsa-linuxant package(recommended by Linuxant, not mandatory for Ubuntu 8.10, but you might as well install it now).
[http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.19git20081204_all.deb](http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.19git20081204_all.deb)


Download both files while booted into Windows, and then boot into Ubuntu, and confirm kernel version with 'uname -r'.

a) Install the alsa-linuxant package .deb file(just double click on it).

b) Reboot

c) Open the .zip file. Inside there will be another .deb file, extract it and double click the .deb file to run the installer. 

d) Now you can try using your dialup modem, try wvdialconf, or gnome-PPP if you have that installed.

Hopefully, this will fix this issue for you.

Keep in mind however, these drivers are not free. You need to purchase a license key at $19.99 to get full 56 kbps speed from the modem. Without a license key('free' evaluation mode), you will be limited to14.4Kbps. Since it's a Wubi install, don't bother with buying one now. You can consider it when installing Ubuntu on its own partition(though I recommend switching to broadband; or getting an external 'hardware-modem', it'll probably work out even cheaper and will work out of the box with Linux- look at the list of supported modems at [http://xmodem.org/modems/index.html](http://xmodem.org/modems/index.html) ).


All the best.

PS: I'll be driving to my hometown today(leaving in an hour). I'll be on the road and without internet access for the next two days. So I'll check back here in this thread then. Let me know how it goes.
Wish you luck.
And happy new year.

---

### Post by Wovaki on 2009-01-01
Well, I installed both those things, I had to download a different hsf driver, because my Ubuntu version was different that the one you gave me, but I ran into a few problems with the alsa driver, so I just reinstalled and it said it installed fine.

But I still cannot connect to dial-up. When I use gnome-PPP it says "Could not open modem." or something like that.

---

### Post by balaknair on 2009-01-01
Yeah, now you know what I mean when I say that getting softmodems to work in Linux is a pain. :(

It's often not worth the effort you have to put in, stuff that works on one machine often doesn't help on another machine with same chipset. That's why so many folks say it's easier to switch to a new connection(non-dialup), or get an external modem(or if your laptop supports it, a Linux compatible PCMCIA card).

I've just gone through my usual troubleshooting stuff and the Linuxant website, and other than restarting the laptop and trying Gnome-PPP one more time, I can't think of anything else. Sorry about that.

Gotta get to work right now, but if I come with anything else I'll post it here.

---

### Post by Wovaki on 2009-01-02
That's alright!

You have helped me so much, its made trying out Linux so much easier. Hopefully soon I will be able to get a better connection than dialup.

If I have anymore questions I will ask them on here! :D

Thanks!

---

### Post by balaknair on 2009-01-03
OK.

Hope you have fun with Linux.

All the best.

---

