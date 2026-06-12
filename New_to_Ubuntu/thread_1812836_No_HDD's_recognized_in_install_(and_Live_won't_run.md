---
title: "No HDD's recognized in install (and Live won't run)"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by Damaged_1 on 2011-07-26
Hi all (first post)
 
new PC with an AMD setup...running a Phenom II and an MSI 990G-E45 MoBo. Have 2 WD SATA 3.0 drives connected, and 4 Gigs of DDR3 1330 RAM
 
Figured I would try out Ubuntu instead of dragging XP onto the new hardware, and decided to go 64 bit to take full advantage of the RAM.
 
Downloaded 11.04 and tried to run it live from USB. Got to the brown splash screen with the pinwheel and "ubuntu" logo, but it never went beyond that (left it sitting for 20 minutes). Also tried installing, and made it to the section to select the HDD's and nothing was shown.
 
I have since (reluctantly) slipstreamed my drivers in XP and loaded it, and all the hardware is working properly...so I assume my chipset isn't recognized by Ubuntu?
 
I know how to handle this in Windows, but not Ubuntu...can I get some guidance here please?

---

### Post by Foxheadz on 2011-07-26
not sure about the hard drives not showing up but i had the same live boot problem and discovered that surprisingly just spamming the enter button once the splash screen shows up tends to work. If that doesn't work at the splash screen hit Esc and post what it stops at

---

### Post by Damaged_1 on 2011-07-26
I did try the Esc key...nothing happened...pinwheel kept spinning...
 
Will downoad and try again to see what happens...

---

### Post by Hakunka-Matata on 2011-07-26
Welcome to the Forums.  

Writing .iso files to USB sticks can be problematic as you will see posted in many threads.  Many people swear by unetbootin, use it to build your USB liveCD if you aren't already.  A suggestion...

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Damaged_1 on 2011-07-27
No problem...I will try that again this morning and see what happens. I previously used the method on the Ubuntu page for building the USB.
 
In the meantime, what can I do about the driver situation (if it is the driver) that is causing me to not be able to install? Is the 880 based MSI board natively supported in 11.04?

---

### Post by Mark Phelps on 2011-07-27
Noticed you mentioned SATA 3.0 drives, which you probably have connected to special SATA ports on your motherboard, right?

I have a similar situation, in that of the SATA ports, six are SATA 2.0 and two are SATA 3.0.

It's possible that the Ubuntu installer can't see drives connected to the SATA 3.0 ports because it doesn't have drivers from them. This is a similar situation to the desktop CD installer NOT being able to see RAID installs.

---

### Post by Damaged_1 on 2011-07-27
Thanks Mark...yes, that is my thought as well...the installation is missing the proper drivers for the chipset on the MoBo, so it can't see the storage devices...just don't know how to remedy this.
 
Tried UNetbootin, made a new USB, and it tried to load live...then rebooted, my MoBo stated a Flood error, and disabled the USB device in the boot options.
 
I used an 8 Gig USB, and also selected 4 Gigs for space for persistence across reboots.
 Trying it again with a 1 Gig and 0 space for persistence...will see what happens.


*EDIT*
I am now able to boot Live, so that's a start...need to try and solve the installation issue now so I can install this on my second HDD and have a dual boot...


*EDIT_2*
I can see my HDD's in the filesystem browser (I am in Live now)...I wonder if my problem previously was a bad USB image? Would stand to reason if I can see the drives in Live, then the OS (and installer) has the proper storage drivers...

---

### Post by amjjawad on 2011-07-27
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)


Have you checked that to begin with?

Yes, it might be a bad LiveCD or LiveUSB.

Is everything okay now? are you able to access your both HDDs?

---

### Post by Damaged_1 on 2011-07-27
I can indeed see my HDD's in Live...

Have not tried installing it yet, as I need to do more research to keep from borking my XP HDD and can make a dual boot system.

I have XP on SATA HDD 1, and want to install Ubuntu (or Kubuntu?) on the second SATA drive.

---

### Post by amjjawad on 2011-07-27
> **Damaged_1 said:**
> I can indeed see my HDD's in Live...

Have not tried installing it yet, as I need to do more research to keep from borking my XP HDD and can make a dual boot system.

I have XP on SATA HDD 1, and want to install Ubuntu (or Kubuntu?) on the second SATA drive.

Why XP? I feel sorry for your machine :)
Just kidding but seriously, XP is 11 years old? and it's better to install Windows 7 but that's my personal opinion.

Hmmm, how about installing Ubuntu temporary on an External HDD or USB Drive and see how things will go with your Hardware? in that case, your internal HDDs won't be touched at all ;)

Let me know if you need more info!

---

### Post by Hakunka-Matata on 2011-07-27
Good to see you can boot to liveCD on USB.  If you want to play it safe and ensure you don't bork your XP installation on SATA1, you could unplug SATA1, and attempt (test) an install of Ubuntu to SATA2.  That method would prevent Grub from overwriting the MBR of SATA1.  After that you would be able to choose XP, or Ubuntu by changing the 'first boot device' in BIOS.

---

### Post by amjjawad on 2011-07-27
> **Hakunka-Matata said:**
> you could unplug SATA1, and attempt (test) an install of Ubuntu to SATA2.  That method would prevent Grub from overwriting the MBR of SATA1.  After that you would be able to choose XP, or Ubuntu by changing the 'first boot device' in BIOS.

Simply, you can choose "where" to install GRUB2 during installation and there is absolutely no need to unplug anything but I understand it's an extra step to be safe ;)

---

### Post by Hakunka-Matata on 2011-07-27
> **Damaged_1 said:**
> I can indeed see my HDD's in Live...

Have not tried installing it yet, as I need to do more research to keep from borking my XP HDD and can make a dual boot system.

I have XP on SATA HDD 1, and want to install Ubuntu (or Kubuntu?) on the second SATA drive.

@amjjawad;

The OP indicates he wants to play it safe, and yes of course the usual way to install Ubuntu on the second drive would be to simply select it during installation, (if installation works correctly).  That would leave him with a XP OS that would not boot on it's own, as the MBR of that drive would be modified (windows bootloader wiped out) by Grub2 when it installs.  That is the meaning of "playing it safe" as I intended it to be understood.

---

### Post by amjjawad on 2011-07-27
> **Hakunka-Matata said:**
> @amjjawad;

The OP indicates he wants to play it safe, and yes of course the usual way to install Ubuntu on the second drive would be to simply select it during installation, (if installation works correctly).  That would leave him with a XP OS that would not boot on it's own, as the MBR of that drive would be modified (windows bootloader wiped out) by Grub2 when it installs.  That is the meaning of "playing it safe" as I intended it to be understood.

Obviously, you missed my point and forgot how GRUB2 works during and after installation ;)

HDD1 has XP
HDD2 suppose to have Ubuntu

HDD1 MBR has XP Boot Loader
HDD2 MBR will have GRUB2

During Installation Process, the installer will run "sudo update-grub" and that means BOTH OS will be bootable once the installation is done and the machine will be rebooted.

As long as the user select and decide "where to install GRUB2 (NOT UBUNTU)", there is no need to plug/unplug anything.

If he selects to install GRUB2 in the MBR of sdb then the MBR of sda won't be even touched.

** All what needs to be done is to enter BIOS and set sdb (HDD2) to boot first then sda (HDD1) to boot second.**
This should be done even before installing Ubuntu.

Ok?

Edit:
I didn't say it's wrong, I said it's an extra step to be safe :)

---

### Post by Damaged_1 on 2011-07-27
Why XP? Cause it's what I have a license for  :)


Would love to go to Win7, but am looking to switch to Ubuntu instead for my more modern OS.

And don't feel too sorry for it...XP SP3 actually runs quite well on here...I just want to go to a more modern OS with 64 bit capabilities, and Linux is attracting me for the newer programs and tools...and it's free.

Worst case, I could install Ubuntu on the second HDD as a stand-alone, then select which HDD to boot from in BIOS each time I want to switch....figured there was an easier way to do dual boot menu with 2 HDD's though.

---

### Post by amjjawad on 2011-07-27
> **Damaged_1 said:**
> Why XP? Cause it's what I have a license for  :)

Right! I totally forgot that :D


> Would love to go to Win7, but am looking to switch to Ubuntu instead for my more modern OS.

+1
Good choice ;)

> And don't feel too sorry for it...XP SP3 actually runs quite well on here...I just want to go to a more modern OS with 64 bit capabilities, and Linux is attracting me for the newer programs and tools...and it's free.

You won't regret it :)

> 
Worst case, I could install Ubuntu on the second HDD as a stand-alone, then select which HDD to boot from in BIOS each time I want to switch....figured there was an easier way to do dual boot menu with 2 HDD's though.

Yes, you can do that OR you can do as I explained in my previous post ;)
However, IMHO, I find it much easier to select with OS to boot into rather than keep changing BIOS Booting Sequence (HDD Boot Priority).

Good luck with that ;)

Just keep us informed, ok?

---

### Post by Damaged_1 on 2011-07-27
Lots of replies while I was posting that last reply...lol

I am probably going to do this in a 2 step process...

Step 1 - unplug XP HDD, install Ubuntu on second, and ensure all is well.

Step 2 - after verification, then I will use the method in amjjawad's signature
**[1-2]** [Scenario 2: Dual Booting System from Scratch, Each OS on its own HDD.          ]("http://ubuntuforums.org/showpost.php?p=10259596&postcount=8"))

I think in the meantime, I may do a Live USB of Kubuntu for comparison to Ubuntu...

I plan on doing image, audio, and movie file editing and encoding, along with general web browsing, email, and office type docs. Would one of these distros be better than the other for this?

---

### Post by Hakunka-Matata on 2011-07-27
@amjjawad; [I]touché, I stand corrected.  live and learn

OP, sorry to distract from your mission
[/I]

---

### Post by amjjawad on 2011-07-27
> **Damaged_1 said:**
> [FONT=Verdana][SIZE=1][SIZE=1][FONT=Arial][SIZE=2]I plan on doing image, audio, and movie file editing and encoding, along with general web browsing, email, and office type docs. Would one of these distros be better than the other for this?[/SIZE][/FONT]
[/SIZE][/SIZE][/FONT]

Not really. Both have the same repositories and you can install the same application here or there. However, both have its own default programs if that matter to you :)

```
sudo apt-get update
sudo apt-get install <packagename> -y

```

is all what you need to get the app you want.

I personally don't like KDE but that's me.

---

### Post by amjjawad on 2011-07-27
> **Hakunka-Matata said:**
> @amjjawad; [I]touché, I stand corrected.  live and learn
[/I]

No one said you are not correct so please read carefully next time ;)

Disagree but do NOT disrespect.

Peace!

---

### Post by Damaged_1 on 2011-07-27
I am going to call this one solved, as I believe my Live issues were from either using an 8 Gig USB, or the process of creating the Live USB originally. I also believe my install issues stemmed from the same, though I have yet to test it (but feel confident that was the case).

Thank you all VERY much for your help.

With that said, I am in Live now with Mint 11...I think I like this very much. Things are a bit more where I expect to find them...may be a better first step for me to get into Linux. Was not a big fan of the new desktop in Natty.

Any caveats I should be aware of with Mint Vs. Ubuntu?

---

### Post by Hakunka-Matata on 2011-07-27
Glad to see you have it working.  Unity is a problem for lots of people, myself included.  It's a simple matter to choose the "Classic" desktop if you wish.
[http://http://forums.somethingawful.com/showthread.php?threadid=3408193]("http://http//forums.somethingawful.com/showthread.php?threadid=3408193")

You can mark this thread Solved using [COLOR=Red]Thread Tools, [COLOR=Black]upper right hand corner.  [/COLOR][/COLOR]

---

