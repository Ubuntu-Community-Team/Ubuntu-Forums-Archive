---
title: "Bios"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by weezyrider on 2011-02-28
How do I get Ubuntu from controlling the BIOS? I have a dual boot, 2 different hard drives. They are separate when running and I want them that way. All of a sudden I can't select which drive by either the BIOS or the boot menu. I have to go thru Ubuntu's menu. I don't want Ubuntu to have anything to do with XP. XP is for Photoshop only, it is not allowed online and that's the way I want it. I did not give Ubuntu permission to change things. Ubuntu has its own drive. I ran the computer this way for years. 2K on one drive and the XP drive isolated.  Thanks W

---

### Post by Hedgehog1 on 2011-02-28
Greeting weezyrider!

The Grub (**GR**and **U**nified **B**oot loader) menu added XP as a boot option, but it is only runs XP if you select it.

So it is safe from the internet when shown in grub.

It is necessary for you computer to have a single place to boot from, that is why Grub shows both OS options.

Sorry it came as a surprise, but it does not put you at risk.

***The Hedge***

:KS

*p.s. I keep Windows 7 around for Photoshop and Sony Vegas; i know where you are coming from.*

---

### Post by grahammechanical on 2011-02-28
By the way, Ubuntu is not controlling the BIOS. And neither is the GRUB program. The BIOS program runs first of all. Without the settings in the BIOS your computer would be just so much metal and plastic.

 After the BIOS has done some checks and worked out what kind of machine it is, it then searches the disc that the BIOS is set to boot from and it looks for an operating system. In your case it most likely finds the GRUB program on the XP disc, which in turn gives you a menu to pick an OS from. At this point Ubuntu has not loaded.

How did you manage to switch operating systems when you had Windows 2000 on one disc and XP one another? Did you have a menu to make your selection from? Or did you go in the BIOS and change the boot disc order?

If you were doing the first thing, then Ubuntu is working in the same way. If you were doing the second thing, then surely the Ubuntu way is an improvement. Yes?

Regards.

---

### Post by weezyrider on 2011-03-01
How did you manage to switch operating systems when you had Windows 2000 on one disc and XP one another? Did you have a menu to make your selection from? Or did you go in the BIOS and change the boot disc order?

If you were doing the first thing, then Ubuntu is working in the same way. If you were doing the second thing, then surely the Ubuntu way is an improvement. Yes?

Regards.[/QUOTE]
No, Ubuntu is not an improvement!

I used the BIOS. Why this is annoying me is that the machine would always boot into the last drive I selected until I changed it.  The machine was designed for Photoshop, that is its primary function. However, to keep everything at maximum speed and simplicity for PS, it is on its own drive with no internet allowed unless for an Adobe install. There is no security on the drive. 2K was the junk drive. Also used for banking as it was behind both router and personal FW and AV and antimalware. I downloaded and virus scanned stuff for the XP drive using 2K.   The first install of Ubuntu left the system alone. I reinstalled Ubuntu and that's when the boot system got changed. I tried to boot from the BIOS as normal, and got told that something (looked like a string of numbers from a CAB file) couldn't be found. Tried F11 and got the same thing. Did get to XP thru Ubuntu. Now if you can tell Ubuntu somehow to** leave the drive selection alone until I change it **- that would be OK. 
W

---

### Post by Mark Phelps on 2011-03-01
To accomplish what I think you want (each drive to be independently bootable), you have to install Ubuntu with the "other" drive disconnected; otherwise, you run the risk of installing GRUB to the "other" drive -- and that prevents it from being independently bootable anymore.

And actually, when you installed Ubuntu with both drives connected, you DID give it permission to modify the "other" drive -- you just weren't made aware of it.

So basically, to restore independently bootable drives, you would have to do the following:
1) Remove GRUB from the MBR of the XP drive, replacing it withan XP-compliant version.  You can do this by disconnecting the Ubuntu drive, inserting an WinXP CD, booting into Windows command line and running the commands "fixmbr" and "fixboot"
2) Install GRUB to the MBR of the Ubuntu drive.  You do this by having the XP drive disconnected, booting into an Ubuntu LiveCD, and reinstalling GRUB.  Read the link below, section 12, for details:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by weezyrider on 2011-03-01
That would mean another trip to the tech as that is beyond me. I wish that there was a caveat before I installed Ubuntu. That's one reason I dislike MS. They think they know everything! How do you wipe the drive? I'll go find another copy of XP. No OS has the right to reconfigure a computer! The hardware is mine! W

---

### Post by mcduck on 2011-03-02
> **weezyrider said:**
> That would mean another trip to the tech as that is beyond me. I wish that there was a caveat before I installed Ubuntu. That's one reason I dislike MS. They think they know everything! How do you wipe the drive? I'll go find another copy of XP. No OS has the right to reconfigure a computer! The hardware is mine! W

It's not "reconfiguring your computer", and it's not touching your BIOS (no OS *can* do that).

On the other hand, *every OS* installs a bootloader of some kind. So does Ubuntu. At least it installs one that acknowledges other operating systems on the computer, unlike Windows does... :D

---

### Post by Hedgehog1 on 2011-03-02
> **weezyrider said:**
> That would mean another trip to the tech as that is beyond me. I wish that there was a caveat before I installed Ubuntu. That's one reason I dislike MS. They think they know everything! How do you wipe the drive? I'll go find another copy of XP. No OS has the right to reconfigure a computer! The hardware is mine! W

weezyrider,

We can walk you through putting your PC back to pure XP without you having to reinstall XP or wipe the drive.

The process has three steps:

(1) Replacing the GRUB Boot Loader with the Microsoft Boot Loader (Called the FIXMBR step)

(2) Using Gparted (**G**nome **PART**ition **ED**itor) to delete the Linux partitions.

(3) Using Gparted to expand your XP partition to use your the whole drive again.

Please be aware that if you dual boot any 2 computer OS's (Even Windows 7 and XP) you will get the same type of menu.  It may be Microsoft's, it may be the open software GRUB, but this is unavoidable for dual boot.

You are welcome to clear your drive and reinstall XP (There are some performance benefits to doing that from time-to-time). 

While you decide how you want to get rid of Ubuntu; please take a little time to try it.  It is on your drive, so you will never have a better opportunity.

We want you to be happy with whatever OS you prefer - really.

***The Hedge***

:KS

**EDIT:** Umm, we do have a few Anti-Windows zealots on the forum.*** They give great technical advice, though.***

---

### Post by mastablasta on 2011-03-02
> **weezyrider said:**
> That would mean another trip to the tech as that is beyond me. I wish that there was a caveat before I installed Ubuntu. That's one reason I dislike MS. They think they know everything! How do you wipe the drive? I'll go find another copy of XP. No OS has the right to reconfigure a computer! The hardware is mine! W
 
 
Since theses things are beyond your knowledge then why not let good boot loader  programme handle this?
 
Ok as others already explained but i am not sure if you quite understand.
 
you have winxp and win2k on two different disks. Every os needs a bootloader which are instructions on how to boot and what to preload on boot. Each of these two disks has it's own bootloader installed (you probably didn't know this). Now you installed another OS which also has it's own bootloader. but this bootloader can recognise other bootloaders and operating systems and loads even before them giving you a choice on which system to boot.
 
Until you boot up the system the system doesn't load.  and so this has no effect on your system.It also doesn't connect the winXP to the internet.
If i was you i would leave it as it is.
 
Also you said you use Win2K for cleaning up XP disk if necessary. this is rediculous, because new  antivirus software usually works only on XP (and later versions of Windows OS).  also if you connect to internet by Win2K and if you have WinXP disk inside - get a virus on Win2K disk and it can "jump" easilly to winXP disk. so unless you unplug the WinXP disk every time you are done with it the file system will still mount and viruses can still get on it from your other disk.
 
To protect yourself efficiently from the scourge - get an antivirus (Avira and Avast are free), firewall (Zone Alarm and Comodo are free) and close the ports that are opened by default. If you want to surf and feeling paranoid then the use of firefox with adblock and no script plugin does the trick.
 
a lot of people use antivirus, but don't use a descent firewall and then wonder how can they get trojans and such malware on their computer.

---

### Post by victorhugo289 on 2011-03-02
You do what I used to do. I too once had two operating systems, Windows XP and Windows 98, both on two separate hard disks, "Master" and "Slave", and I had to chose between each of them by disabling one of the disks in the BIOS.
Basically it is not necessary to do that, I think the answers given by previous posts to mine here explain clearly the reason why, better than I could. But I do understand what you mean. :D

---

### Post by Mark Phelps on 2011-03-02
> **weezyrider said:**
> ...How do you wipe the drive? 
No need to wipe the drive. 
> I'll go find another copy of XP. 
If you can find an XP CD, just follow the instructions in step 1).  No need to wipe or reinstall XP.  Just repair the boot loader and MBR -- and you'll get XP back.
> No OS has the right to reconfigure a computer! The hardware is mine! 
Every OS installation HAS to do basic configuration steps as part of its installation in order to leave the PC in a state such that the OS will launch when you complete the installation.  They ALL install a boot loader of some type -- Linux and MS Windows OS's.

The OS you install last will overwrite the MBR so that when you next boot the PC, that OS is the one that will run.

This is how OS installations work.

---

### Post by weezyrider on 2011-03-02
[LIST]
[*]Now  that I've calmed down a bit, how secure is that system? Can anyone or  anything access that drive w/o permission? And will I have to get  permission from Ubuntu to do whatever I want on the XP drive? I  originally took the XP HD offline as I did not agree with the EULA, but  wanted Photoshop. MS was ballistic over piracy then, and I figured what  MS couldn't find, it couldn't mess with.  I'm now at the stage where  upgrading PS wouldn't do me any good. I started with 3, and still do  most of the stuff manually. It will take me forever to really work with  the newer version. The computer is generic, custom, and should have no  trouble with updating or fixing. BTW, I usually disable or toss whatever  I can out of Windows. I found by doing that, NOT using Office or MS  apps or security, and not letting Windows d/l files willy-nilly, the  system rarely crashed. 98SE didn't crash, either.
[*]Can I download Windows files to a USB using Ubuntu? I have another dedicated offline box that has updatable software.
[*]Can I tell  Ubuntu NOT to update without going through that whole checkbox? I prefer  to read first, and sometimes new is not always an improvement.  I would  still like to DOWNGRADE some apps. I've given up on the new Stellarium,  but want to try the last version that seemed to be stable.
[*]How do you get tags to work? <br></br> doesn't.
[*]Thanks
[/LIST]

---

### Post by srs5694 on 2011-03-02
> **mcduck said:**
> It's not "reconfiguring your computer", and it's not touching your BIOS (no OS *can* do that).

Actually, OSes *can* change the BIOS -- both BIOS settings and the BIOS itself. Just think about it: There are BIOS flash utilities for DOS (and perhaps Windows; I haven't looked for one lately), which completely replace the BIOS with another one. I've also personally encountered configurations (with a Hackintosh) in which the OS scrambles the computer's BIOS settings. Such unwanted BIOS settings changes are rare, though.

That said, I don't think this is happening in weezyrider's case, although I'm not 100% positive of that. (The claim that s/he "can't select which drive by either the BIOS or the boot menu" is very unclear, but could indicate some sort of interference with the BIOS.)

> **weezyrider]how secure is that system? Can anyone or  anything access that drive w/o  permission? And will I have to get  permission from Ubuntu to do  whatever I want on the XP drive?[/quote]

It's unclear what you mean by this. Security of access to the hard disk is handled by the OS, and so depends entirely on the OS's security mechanisms. IIRC, a typical Ubuntu installation allows all users to read from and write to any NTFS or FAT partition on the disk, although my memory might be faulty (I usually customize my disk-access procedures immediately after installing any OS). You can change these settings in Ubuntu by editing the /etc/fstab file (try Googling on "Linux fstab" to find lots of information about it).

When the computer is not running Linux, then Linux has absolutely no influence over how the disk is accessed.

The GRUB boot loader that seems to have so concerned you is just a program that's launched *before* any OS is running, in order to help choose and load an OS. GRUB doesn't normally write to the disk (and I'm not even sure if it can said:**
> Can I download Windows files to a USB using Ubuntu? I have another dedicated offline box that has updatable software.

Yes.

> Can I tell  Ubuntu NOT to update without going through that whole  checkbox? I prefer  to read first, and sometimes new is not always an  improvement.  I would  still like to DOWNGRADE some apps. I've given up  on the new Stellarium,  but want to try the last version that seemed to  be stable.

Perhaps I just didn't get enough sleep last night, but I find your double negative construction in the first sentence very confusing. Given the rest of the sentences in this paragraph, I think you're asking about the ability to deny automatic package updates. You can certainly do so. Downgrading to an earlier version is usually trickier, but it can be done. One way is to to download a Debian package file for the version you want, uninstall the current version, and install the package file. Another way is to use version selection mechanisms in apt-get. Type "man apt-get" and then type "/downgrade" to find the relevant section in the documentation. I've never tried this second method, so I don't know much about it. Whatever you do, Ubuntu, like most Linux distributions, is designed to check for updates on a regular basis and will nag you about upgrading. It's certainly possible to disable checks for updates, but I've never looked into how to do it.

> How do you get tags to work? <br></br> doesn't.

In what context? Those are HTML tags, which you'd normally apply in HTML documents. If you're asking about this forum, it's got its own tags that you can apply in the editor. See [here](http://ubuntuforums.org/misc.php?do=bbcode) for more information. Note that forum tag use is OS-independent; you'd enter the same tags in Linux, Windows, and OS X on any given forum. There may be some differences from one forum to another, although most use similar tags for most purposes.

---

### Post by victorhugo289 on 2011-03-02
> **srs5694 said:**
> (The claim that s/he "can't select which drive by either the BIOS or the boot menu" is very unclear, but could indicate some sort of interference with the BIOS.)


It's not unclear at all, it totally makes sense.
The Ubuntu GRUB consists of 2 parts, one is on the Boot sector of the 1st hard disk, on the first 512k, and the other is on the Ubuntu partition, the actual GRUB menu is on the Ubuntu partition.

--If the user disables the Ubuntu partition he/she will only see the terrifying "Grub rescue>".
--If the user disables the 1st hard disk --Windows XP in this case-- he/she will not be able to even boot the system.
That is why he/she can't select which drive by either the BIOS or the little BIOS's boot menu, that's the menu he refers to.

---

### Post by Hedgehog1 on 2011-03-02
> **weezyrider said:**
> 
[*]Now  that I've calmed down a bit, how secure is that system?
 Can anyone or  anything access that drive w/o permission? And will I have to get  permission from Ubuntu to do whatever I want on the XP drive?


Unlike Windows, Unix was built as a multi user system, and security is part of it's basic design.  You are much more likely to be annoyed at how it won't let you mess with something until you give the root password, frankly.

If you are concerned about security, Unix/Linux is a better choice than the MS Windows products...

As to accessing your XP drive from Ubuntu; by default it was made accessible to you because you did the install.  You have that power because you created this little Linux world.  If you wanted other to log in and use your PC, you could limit what they can do.

> 
I  originally took the XP HD offline as I did not agree with the EULA, but  wanted Photoshop. MS was ballistic over piracy then, and I figured what MS couldn't find, it couldn't mess with.  I'm now at the stage where  upgrading PS wouldn't do me any good. I started with 3, and still do  most of the stuff manually. It will take me forever to really work with  the newer version. The computer is generic, custom, and should have no  trouble with updating or fixing. BTW, I usually disable or toss whatever  I can out of Windows. I found by doing that, NOT using Office or MS  apps or security, and not letting Windows d/l files willy-nilly, the  system rarely crashed. 98SE didn't crash, either.


I am a Photoshop geek; running CS5 myself. If you are still running CS3, you will find much (but not all) of that same functionality in Gimp.  It really depends on the filters you use.

It is a free alternative, but it depends on your specific needs.

> 
[*]Can I download Windows files to a USB using Ubuntu? I have another dedicated offline box that has updatable software.


Mostly, yes.  The downloaded fix need to be one that is a complete file (ends with a .exe or .zip).  Windows updates are harder to do this way; but MS is starting to offer ISO based updates you can burn to a CD on your Ubuntu system and load on your isolated Windows system.

> 
[*]Can I tell  Ubuntu NOT to update without going through that whole checkbox? I prefer  to read first, and sometimes new is not always an improvement.  I would  still like to DOWNGRADE some apps. I've given up on the new Stellarium,  but want to try the last version that seemed to be stable.


If you menu to: System >> Preferences >> Startup Applications, you will get a selection box that allow you to turn off the automatic updates.  Then you can run them when you are ready, and choose what you want to have run.

> 
[*]How do you get tags to work? <br></br> doesn't.
[*]Thanks


Got me on that - I think they have to be upper case in this forum to work, thought.

***The Hedge***

p.s. Are you, by any chance, a star gazer?  Just wondering...

---

### Post by srs5694 on 2011-03-02
> **victorhugo289 said:**
> [quote=srs5694](The claim that s/he "can't select which drive by either the BIOS or the  boot menu" is very unclear, but could indicate some sort of  interference with the BIOS.)It's not unclear at all, it totally makes sense.[/quote]

I'm not saying that it doesn't make sense; I'm saying that it's unclear what "it" is. That is, weezyrider was being unclear in communicating what's wrong. It sounds to me as if the claim is that the BIOS's option to select the boot disk (by hitting a function key during the BIOS self-checks) isn't working. If so, this could be a sign of some sort of change to the BIOS. OTOH, it could be that weezyrider was simply thrown by a change from either no boot selector or some Windows-centric boot selector to GRUB, or perhaps when GRUB overwrote the usual boot loader, one or both of the usual BIOS-driven options began behaving differently than expected. A more precise description is in order before any firm advice can be given.

> The Ubuntu GRUB consists of 2 parts, one is on the Boot sector of the 1st hard disk, on the first 512k, and the other is on the Ubuntu partition, the actual GRUB menu is on the Ubuntu partition.

A small correction: The first part of the GRUB boot code resides in the first sector of the hard disk, which is 512 *bytes* in size, not 512 *kilo* (or even *kibi*)bytes. In fact, the boot loader shares this sector with the Master Boot Record (MBR) partition table, so the actual boot loader code space is limited to 440 bytes (or 446 bytes if it overwrites the partition table's serial number, as I hear some do, but I don't think GRUB does). Depending on the configuration, more code is likely to reside in the following 60-some sectors, totalling a bit over 30 KiB in size, and then more on the Linux partition and files stored there.

---

### Post by Jerry N on 2011-03-02
There is a little confusion here I think - but maybe I am confused!
In my case I installed XP and Win 7 on drive with drive 2 disconnected.  I then disconnected drive 1, reconnected drive 2,  and installed Ubuntu 10.04 and Kubuntu 10.10.  I then reconnected drive 1.  This left drive 2 as the first drive in the boot list and grub IS NOT installed on drive 1.  I can select which drive to boot with F12 during boot - I don't change the drive order in the BIOS.  Grub finds the Windows drive and puts Windows in it's list of boot options but if I select the Windows drive during boot using F12, grub does nothing.  I do not do an "update grub".

On GIMP:  GIMP does about anything I would want to do to a JPEG file but the current version does not work with 16 bit color depth and if it loads 12 or 16 bit RAW files (it does not load Nikon D7000 RAW files) it truncates them to 8 bits.  It also truncates 16 bit TIFF files to 8 bits and does not read Adobe dng.  The 16 bit problem is supposed to be addressed by GIMP 2.8, if it is ever released, but I don't know about Adobe dng.  (Format information for Adobe dng is in the public domain so there's no proprietary data problem.)  Old Photoshop CS2 and Adobe Elements 8 both work fine with .dng files.

Jerry

---

### Post by cloyd on 2011-03-02
I would strongly recommend : Just try it. It is more secure than windows. If you are running Ubuntu, nobody from outside can access your Windows files. You can download windows files from Ubuntu, and you can copy them into your windows system or your Ubuntu system..  You can access your windows files from Ubuntu. Viruses in any form of Linux are practically non-existent  (not impossible, just very, very rare). I don't think anyone has every heard of a security breach on a windows disk that happened through a system booted in Ubuntu or any other linux distribution.   When you are on-line with Ubuntu, Micorsoft does not have access to your system for updates or anything else. When you are on-line, no one has access to the windows system. 

In the utterly unlikely event that you did get a virus on the Ubuntu system, a virus written for Ubuntu would not be dangerous to Windows (and vice-versa). 

One last thing I hope you consider. Yes, Linux in general, and Ubuntu in specific does have updates. You will find that Ubuntu upgrades are: 

1. More polite. If the update notification pops up, and you are thinking "not now" and tell it so, it does not continually keep popping up like they do in windows. After you shut it down, you do the upgrade when you feel like it. 

2. I've never had an upgrade w/o my permission. That happened lots of times with Windows.

3. I've never had an upgrade change a basic preference such as my internet browser. But windows did. 

4. I have yet to have an upgrade that didn't work well. I guess it could happen. I've only been using Ubuntu about 16 months now.  However, I do remember a ton of issues after service pack two in xp. Never anything like this in Ubuntu.

5. Most upgrades do not require you to reboot. If they do, it seems that 90% of the time it was because they installed a new kernel. When you do get a new kernel, you also keep the old one, so if you liked the old one better, you can still use it.  If you get an upgrade to your web browser, it will probably ask you to restart the web browser . . . but not the whole system.

I would recommend you get the upgrades. There have been times they definitely improved performance. Linux is secure. The upgrades are one reason. Experience has shown me that the developers are doing a much more careful job of checking the upgrades before sending them out than Microsoft. 

I dual booted for 6 months or so on both my machines. Now, I dual boot on only one, because I just don't use windows that much. (One machine is Windows free!)  GRUB is easy to use . . . I feel a lot safer using the GRUB menu than I would always having to go into BIOS. 

If you think Ubuntu just might do the things you want to do, give it a try. You may really be surprised at how much you come to like it.

---

### Post by Jerry N on 2011-03-02
> **cloyd said:**
> 
2. I've never had an upgrade w/o my permission. That happened lots of times with Windows.

3. I've never had an upgrade change a basic preference such as my internet browser. But windows did. 

4. I have yet to have an upgrade that didn't work well. I guess it could happen. I've only been using Ubuntu about 16 months now.  However, I do remember a ton of issues after service pack two in xp. Never anything like this in Ubuntu. 

I have never had an upgrade w/o my permission in Windows or in Linux and I have been using Windows a long time - since Win 3.0 but skipping ME and VISTA. BTW, I have never gotten a virus in Windows, but I hide behind antivirus, Zonealarm firewall, and a router, and I'm careful about what I open.  

You have just as much choice about what to upgrade in Windows as you do in Linux.  Windows has never upgraded something like the browser unless I gave it permission.  (I don't do automatic updates, Windows or Linux).   

Ubuntu has had disastrous updates but not in the 3.5 years that I have been using it.  Ubuntu has a lot more updates than Win 7 but I am not saying that is a good thing or a bad thing.

Jerry

---

### Post by weezyrider on 2011-03-02
@Hedgehog - yes, I am a stargazer. Refractor nut. Favorite observing site is Arches NP when we go to Utah.

When I tried to boot from the bios as normal, I got a string of numbers  and the message that this string of numbers was unavailable.  Unfortunately, that string of numbers that Grub posted looked like  something from XP's registry. Had Ubuntu said the Seagate drive was  unavailable, it wouldn't have been such a shock. It looked like Ubuntu  had been searching in XP's registry.

I'm sure Gimp is very capable, but I don't like the interface. I like the Suite of Adobe software on XP. 

There's nothing personal on either drive. I usually turn the box off  when I go out, but I have left it on. I really don't want anyone to have  access even though there is nothing there. 

No one in the family will use my computer. If they don't know how to  turn on the mouse, a doubleclick on the Wacom simply defeats them. Try  to use Firefox, and between Adblock, Noscript, and the fact that I turn  off images half the time, they can't work that, either. 

About the HTML tags. I wrote a post, previewed, and it looked  like a  long run-on sentence. I was trying to get paragraphs in somehow. Tonight, this post does have paragraphs.

I am liking the speed of Ubuntu more and more.

W

---

### Post by cloyd on 2011-03-02
Jerry, admittedly, I've only been using Ubuntu, well, since Nov 09. I am sure there have been bad upgrades, but I've never had one.

Not everybody has has their default browser changed, but Microsoft did indeed change mine to Bing. I changed it back . . . hey that's not my browser, it is my search engine! Ok. It switched me over to Bing. I know it didn't do it to everybody. My bad.  Bing . . . Google : search engines. Firefox . . . Internet Explorer : browsers . . . I'm slapping my forehead right now. When I get done, I'll look like a Neanderthal., 

Windows always got very insistent about update. I'd say, "not now" and it would keep on popping up. It would usually happen when I logged in to do get some information off of it when I needed to leave and tend to other business.  It really didn't like "no" for an answer. It seemed that those updates came at the most inconvenient times. Maybe it was my settings. I did have one occasion when I was working along, and an update started, then shut my machine down to reboot with no input from me. Again, maybe a setting got messed up, but I did not like it. Not everybody has had this experience. 

I used a good anti-virus program and paid an annual subscription for it. In general, they kept me virus free, but got one bad virus anyway (it blocked access to my cd/dvd drive), and a certain well known utilities/computer security company charged me $100 to clean it off my machine. If the truth be known, I probably shouldn't have visited one site (I didn't go there any more, either). 

My point . . . our experience may be some different, and there may be some real reasons for that. Still, I think Ubuntu keeps us more in the driver's seat than Windows.  But even more, I think the point I was wanting to make is that updates in Ubuntu have, for me, been a much more pleasant experience for me than in Windows. 

In honesty, I also have to say, ever now and then, something comes up and I must have windows. It isn't all bad, but I like Ubuntu worlds better.

---

### Post by JKyleOKC on 2011-03-02
> **weezyrider said:**
> When I tried to boot from the bios as normal, I got a string of numbers  and the message that this string of numbers was unavailable.  Unfortunately, that string of numbers that Grub posted looked like something from XP's registry. Had Ubuntu said the Seagate drive was unavailable, it wouldn't have been such a shock. It looked like Ubuntu had been searching in XP's registry.That mysterious string of numbers was most likely the "uuid" for the drive that contains Ubuntu. A "universal identifier" is a very large number that's generated in a manner that's supposed to make it unique (but since there are only a few trillion possibilities for the number of bits used, it's not really guaranteed unique, just most likely to be). Ubuntu generates such identifiers for each drive that it finds on a system, and uses them instead of the Windows "A: B: C: D:" terminology. It also has a couple of other methods to identify drives but none of them are usually of interest to anyone but true geeks like many of us here.

As victorhugo289 mentioned earlier in this thread, the GRUB loader gets installed in the Master Boot Record of the first drive, which would be the C: drive for Windows, but then looks to a drive identified by a uuid for the next step of the boot process -- and with the Ubuntu drive disconnected, it couldn't find it. That's what generated the frightening error message.

Your confusion is quite understandable! In fact, Windows itself uses the same kind of identifiers for many of its internal needs, and the registry is full of them.

A few messages back, Jerry N posted a solution that works quite well but implementing it would require you to open the box and disconnect drives, or go back to the tech to get it done. However if done it would work exactly the way you want it to, with no need to go into the BIOS.

---

### Post by Hedgehog1 on 2011-03-02
> **weezyrider said:**
> @Hedgehog - yes, I am a stargazer. Refractor nut. Favorite observing site is Arches NP when we go to Utah.

I was guessing that.  Do you process your observation images using Photoshop? Do you capture images with cmos imagers, or with Film?

> 
I'm sure Gimp is very capable, but I don't like the interface. 


It is very different, I agree.  But it is handy when you don't want to boot over to the XP side.  I still use CS5 for the complex work.

> 
About the HTML tags. I wrote a post, previewed, and it looked  like a  long run-on sentence. I was trying to get paragraphs in somehow. Tonight, this post does have paragraphs.


I see!  Well done.

> 
I am liking the speed of Ubuntu more and more.


Glad to hear it.  

***The Hedge***

:KS

**p.s. You may have noticed in the other posting that we engineers cannot resist a good technical argument.  It's a nerd thing.  I do it too...**

---

### Post by weezyrider on 2011-03-03
@ Cloyd. MS never did that to me. I turned off all the updates after the fiasco with the scanners and cameras. I also turned off all notifications and put in my own paid AV and FW. I never did use IE - I think I have IE 5 - I also don't use Office or anything else from MS. If there is a critical update, the computer goes to the tech and gets it. After the nonsense with MS inserting the drm files in FF - anything extra from MS is banned by the firewall and in the hosts file. I can't run Bing.  Groupon, either. If the update just patches IE, or Word, then to hell with it. 

I pay for Eset's Nod32. I've used it for years as it was the only AV at the time that didn't require IE. It worked off of Winsock. I was running 98Lite, which effectively removed IE from anything using it. I could not use a program that required IE. 

I'm looking at Nod32 beta for Ubuntu. I do want to check files I download for the XP computers. 

@Hedgehog - I haven't really done any astrophotograpy. I use an Alt-Az mount. 
I did buy a 500 F8 mirror lens that does pretty well on the moon. It's soft, but PS cures that. And it was cheap enough that I don't need to feel guilty about not using it. I mostly edit my own photos, and some for friends.

@Jkyle - thanks for the explanation of that number. It was startling.

After all the assurances, I'm going to leave well enough alone. Since nothing can bother the XP drive, I'll keep booting from Grub. 

W

---

