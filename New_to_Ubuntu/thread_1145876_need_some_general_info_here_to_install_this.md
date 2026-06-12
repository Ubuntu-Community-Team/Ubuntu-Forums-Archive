---
title: "need some general info here to install this"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by mal1958 on 2009-05-02
I am a total noob to this, so please keep the terms short and simple.  

I burned a copy of the Ubuntu 9.04 to a disk and tried to boot from it to check out the live version and it was bypassed and windoze loaded.  I checked the Bios settings and the CDR I am running is set to be bootable.  Is the iso image of the 9.04 Ubuntu bootable?  

I want to run Linux solo, using every gig of this 58-60 gig HD for linux.  I have a program called 'Crossover' that my brother gave me.  He got it from the company when he was experimenting with linux a little while back and gave up.   My question is do I need to dl an image for a floppy to boot with to install the system and wipe windoze off my system forever, or is the CD with the Ubuntu distro supposed to be bootable.

I give you all fair warning, since I am a noob, I will be plauging this place and you folks for quite some time.  Hope you don't mind.

Will respond to this in the morning, since it is 1:33 am here and I have been burning the candle at both ends for the last 36 hours.

Mike  aka Mal

[COLOR=Red]EDIT:  I forgot to add, that I used the windoze program Alcohol 120% to burn the image and I have a Lite-On CD-RW SOHR 5239V CD-RW drive in addition to a _NEC DV-5800A DvD rom drive.  The burn went with out a hitch and all, it just doesn't seem to want to boot.[/COLOR]

---

### Post by techstop on 2009-05-02
It sounds like you just burnt the iso file to a data disk. You need to use something to burn an *image*, the image being the iso. When you open the burned disc, you should see a range of files and folders, not just the .iso file you downloaded.

---

### Post by lisati on 2009-05-02
Some tips can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by dse.37 on 2009-05-02
That's odd, it should boot to the live CD. Did you double check your BIOS settings to see if you're reading from CD/DVD-ROM first? The only other thing I could suggest is to burn a new image with something different to see if that helps...

[CDBXP]("http://http://cdburnerxp.se/") is freeware and was always reliable for me.

---

### Post by mal1958 on 2009-05-02
I did an edit to my post, but here is the jist of it.  I burnt the image using Alcohol 120 % and the Image burning wizard.  The burn went fine, and I have a disk with a range of files on it, not one big file that ends in .iso.  I may not know much about Linux, or Ubuntu, but I do know computers and windoze.  

I know how to burn the files to disk, I am just wondering if it may be my hardware.  I am hoping that there is somebody here who might be able to tell me.

Mike

---

### Post by jmszr on 2009-05-02
mal1958,

In addition to the above advice I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide and Free Ubuntu Pocket Guide by Keir Thomas are of particular note but the entire sticky is full of good information. 

Edit: Here is the section from Psychocats about burning an .iso : [http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

---

### Post by mal1958 on 2009-05-02
> **jmszr said:**
> mal1958,

In addition to the above advice I would suggest this sticky by umg6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide and Free Ubuntu Pocket Guide by Keir Thomas are of particular note but the entire sticky is full of good information.

   I am a few steps ahead of you here.  I have hit many of the stickied threads here, and some sites that have drivers, and or programs that I may find useful and downloaded them to my second HD or copied their URL to a text file and then copied that to a separate disk.  I am trying to be a good boyscout (IE.  Be Prepared) for this shift.

Mal

---

### Post by jmszr on 2009-05-02
mal1958,

         You seem to be on solid ground as far as your preparation. If the BIOS is set then perhaps a different CD burning program at a slow speed?

---

### Post by -kg- on 2009-05-02
OK, it seems you have a good iso burn, and I will assume that you know enough about BIOS to be able to determine whether it is set to check the CD drive before the hard drive.

Since you were able to burn the .iso in the first place, the drive should be OK.  Have you tried to boot to any other CDs, such as the Windows Installation or Rescue Disk (if you have one)?  Did you check in BIOS whether the drive is being recognized?  Perhaps it's being recognized too late to be able to use the checking feature for autoboot.

Is this a laptop?  On some laptops (including mine) at boot up time you see a selection to go into BIOS (F2 on mine) AND a selection to select the boot device (F12 for me).  When I want to boot to a different device, I press F12, and it allows me to select any of the connected drives or my CD drive.

---

### Post by jmszr on 2009-05-02
mal1958,

      After rereading your initial post I think the problem is you are trying to boot from the CD rather than inserting it while the computer is running Windows and then rebooting (restarting}.
Try that if you haven't already and I have misread.

---

### Post by mal1958 on 2009-05-02
> **jmszr said:**
> mal1958,

      After rereading your initial post I think the problem is you are trying to boot from the CD rather than inserting it while the computer is running Windows and then rebooting (restarting}.
Try that if you haven't already and I have misread.


I did both to be precise.  I had the cd in the drive and did the Start/turn off computer/Reboot, I did the Start/Turn off computer/Shutdown and then repowered it back up.  Still the thing will not boot from the cd.  I will be checking to see if I can boot from the windoze XP cd, but I seem to remember doing that already at one point in the past.  

Mal

---

### Post by LinuxGuy1234 on 2009-05-02
Change the boot order in your BIOS to be CD first then Hard Drive.

---

### Post by halitech on 2009-05-02
if you have another system, maybe try to boot the cd in that to see if it works. If it does then we know we are dealing with an issue on the original cd. If it doesn't then we know its a bad burn.

---

### Post by lsemmens on 2009-05-02
It could be as simple as not quick enough with the "any key" button during boot.
Straight after POST it should pop up the option to "press any key to boot from CD...." before defaulting to Windoze if you don't hit a key in the requisite time about 2 secs IIRC.

---

### Post by jmszr on 2009-05-02
mal1958,

Did you happen to run a md5sum on the ubuntu download before burning the image to disc?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) . That's all I have if it doesn't seem to be a hardware problem

---

### Post by cariboo on 2009-05-02
Does autorun work when you are in Windows? If not then you have a bad burn.

---

### Post by RyanVanDiemen on 2009-05-02
if you have an option to boot from usb,you can install from usb key.but you need a computer that can boot from live cd and then create start-up usb key.anyway,have you tried the cd on different computer? If it boots,the problem is in your hw or bios.if it doesn't burn it again or download the image again

---

### Post by mal1958 on 2009-05-02
@ Cariboo907   AutoRun works fine from Windoze.  I know the burn is good.

To everybody else, I am going to give it a shot and pray.  wish me luck,  I also burned a copy of Xubuntu JIC I run into problems with Ubuntu running out of resources.  Both burns autorun perfectly.

Mal

---

### Post by mal1958 on 2009-05-03
I am singing for joy.  Xubuntu installed, windoze is off, and I have great video, audio, and can play movies on it.  I had to settle for Xubuntu because my machine is older (8 1/2 years) and couldn't handle the full version.  I will be plagueing this place to learn as much as I can, and hope that all you nice folk who helped me install this won't get sick of seeing me.  Thanks a mil.

Mal

---

### Post by presence1960 on 2009-05-03
> **mal1958 said:**
> I am a total noob to this, so please keep the terms short and simple.  

I burned a copy of the Ubuntu 9.04 to a disk and tried to boot from it to check out the live version and it was bypassed and windoze loaded.  I checked the Bios settings and the CDR I am running is set to be bootable.  Is the iso image of the 9.04 Ubuntu bootable?  

I want to run Linux solo, using every gig of this 58-60 gig HD for linux.  I have a program called 'Crossover' that my brother gave me.  He got it from the company when he was experimenting with linux a little while back and gave up.   My question is do I need to dl an image for a floppy to boot with to install the system and wipe windoze off my system forever, or is the CD with the Ubuntu distro supposed to be bootable.

I give you all fair warning, since I am a noob, I will be plauging this place and you folks for quite some time.  Hope you don't mind.

Will respond to this in the morning, since it is 1:33 am here and I have been burning the candle at both ends for the last 36 hours.

Mike  aka Mal

[COLOR=Red]EDIT:  I forgot to add, that I used the windoze program Alcohol 120% to burn the image and I have a Lite-On CD-RW SOHR 5239V CD-RW drive in addition to a _NEC DV-5800A DvD rom drive.  The burn went with out a hitch and all, it just doesn't seem to want to boot.[/COLOR]

I haven't used Alcohol in quite some time, but I believe you have to select the option to burn an image from the .iso file.

---

### Post by -kg- on 2009-05-03
> I will be plagueing this place to learn as much as I can, and hope that all you nice folk who helped me install this won't get sick of seeing me. Thanks a mil.

Our pleasure, even though you seem to have figured it out yourself more than we were able to help.

:lolflag:

Anyway, "plague" away!  We promise we won't get any sicker of seeing you than anyone else! :P

;)

---

### Post by mal1958 on 2009-05-19
Glad to hear that.  I love the control I can have with this OS and want to get the most out of it.  Will be a regular here, for the knowledge, the talking, and the friendships.

BTW,  I have xubuntu installed alread and it is great, save for the problems with some of my games.  Other then that, I love it.

Mike

---

### Post by lisati on 2009-05-19
> **mal1958 said:**
> Glad to hear that.  I love the control I can have with this OS and want to get the most out of it.  Will be a regular here, for the knowledge, the talking, and the friendships.

BTW,  I have xubuntu installed alread and it is great, save for the problems with some of my games.  Other then that, I love it.

Mike

Welcome to the team and congratulations for your success! I hope to see you around on these forums for quite a while yet.....

---

### Post by mal1958 on 2009-05-20
> **lisati said:**
> Welcome to the team and congratulations for your success! I hope to see you around on these forums for quite a while yet.....

If I can solve the problems that I am having with Alpha Centauri Alien CrossFire (I have both the Windoze and Linux version (from Loki)) and the problem in getting Civilization 3 up and running (Only the Windoze version that I am trying to get wine to run) then you will see me.  If not, I will pop in, but may have to fall back onto the hated Windoze so I can get my Sid Meier's fix.

Mike

---

