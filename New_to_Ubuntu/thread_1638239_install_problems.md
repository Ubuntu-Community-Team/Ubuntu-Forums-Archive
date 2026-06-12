---
title: "install problems"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by SnoopNL on 2010-12-05
Hello,
 
When I try to install ubuntu 10.10 64 bits I get a serious problem.
Whenever I start the install (cd or usb) I get my windows 7 64 bit desktop shown, all jittered.
The installer freezes here and I need to hard reset my pc (reset button).
Live cd does not load, it gives me the same problem.
Anybody any suggestion?
 
Hardware:
Intel Q6600
4GB DDR2-800
Nvidia 240 GT 512 GDDR5
DVD RW drive.
MSI G31M3-F [http://global.msi.eu/index.php?func=proddesc&maincat_no=1&prod_no=1470](http://global.msi.eu/index.php?func=proddesc&maincat_no=1&prod_no=1470)
 
With latest BIOS loaded.
 
Anybody any suggestion?

---

### Post by Penguin=) on 2010-12-05
I think your Ubuntu installation disk may be scratched OR corrupted.

Did you make the disk yourself from a ISO?
Or did you request one from the people who made Linux?

---

### Post by lindsay7 on 2010-12-05
Is your computer set up to start from a cd or dvd drive first?  Are you wanting to do a wubi install or a full instll?

---

### Post by SnoopNL on 2010-12-05
I downloaded it myself.
I will redownload it now and post results as soon as I am ready.

---

### Post by Verbeck on 2010-12-05
try checking the md5sum of the iso before downloading again


from windows, you can :
> 
[LIST=1]
[*]Download and install [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum"), a  free and open source hash verification program. 
[*]Right-click the ISO file. 
[*]Click  Send To, then winMD5Sum. 
[*]Wait for winMD5Sum to load and finish the checksum (this  may take a significant amount of time depending on your computer's  performance). 
[*]Copy the corresponding hash from [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")  into the bottom text box. 
[*]Click  "Compare"
[/LIST]
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by SnoopNL on 2010-12-05
MD5 checksums are the same.
So not a bad iso?
 
What could this be?

---

### Post by Penguin=) on 2010-12-05
> **SnoopNL said:**
> MD5 checksums are the same.
So not a bad iso?
 
What could this be?


No, its not a bad ISO then.

---

### Post by SnoopNL on 2010-12-05
I figured that out.
 
But what can cause this?
There is no extra hardware connected, only usb mouse and keyboard.
Monitor is connected through DVI.
 
Any help would be welcome.

---

### Post by Penguin=) on 2010-12-05
I think the most likely explanation is Windows 7.

It may be conflicting "against" Ubuntu.

Did you partition it or did you erase the full drive and just use Ubuntu?

---

### Post by Verbeck on 2010-12-05
if it successfully booted from the cd/usb, then the windows desktop(or any other os) should not appear.
it could be a badly burnt cd.. but you've tried with a usb with the same result..

have you checked the boot order?

---

### Post by SnoopNL on 2010-12-05
I want a dual boot with this.
 
So I did not partition anything.
I have 2 partitions.
 
I have 1 main with win 7 on 1 hdd.
I also have a second hdd with a NTFS partition (entire drive).
I want to take the second harddrive and resize the partition for use of ubuntu.
The win7 disc is sata, the 2nd disc is IDE.
Sata Disc is 320GB the IDE disc is 250 GB

---

### Post by SnoopNL on 2010-12-05
I tried it, changing the boot order.
Same problem.
 
Anybody got any clue?

---

### Post by SnoopNL on 2010-12-05
Still nothing.
Deactivated my Kaspersky, because it showed a allowed pdm.rootshell when using the tool to create the USB, still same problem.
 
I made a screenshot of what it looks like when the installer halts.
You see the ubuntu loading screen, the bulbs light up and then it halts.
[http://yfrog.com/03imag0099cj](http://yfrog.com/03imag0099cj)
 
As you can see, this is my user desktop of windows 7 all scrambled up.
 
I will reboot and disable the disc let's see how that works
 
Edit:
Ok same problem.
Tried something else:
Opened a VMWare of XP.
Disabled Kaspersky on the host win7 x64.
 
Copied the iso to xp.
Made the new usb on the xp.
Same problem: Whut the H.... ?
 
Is this a dev. problem?
 
I wont revert to 10.04, I simply will not!
 
Edit 2:
Tested on VMware 7.
Working there.
 
Ok... this becomes weirder and weirder.
 
I need help on this!

---

### Post by SnoopNL on 2010-12-06
Bump!
 
Come on guys, don't quit on me when it gets tougher!
 
I want this to work!

---

### Post by SnoopNL on 2010-12-07
Bump!
 
Anybody?
I am stuck here.

---

### Post by SnoopNL on 2010-12-07
Ok...
 
Nobody seems able to help.
I will just go with opensuse then if i haven't figured this out by tomorrow.
 
Seems the forums are not so full of support as they would be with a bunch of linux fanatics.

---

### Post by Hippytaff on 2010-12-07
I understand your frustration...what graphics card do you have?

---

### Post by SnoopNL on 2010-12-07
> **Hippytaff said:**
> I understand your frustration...what graphics card do you have?
 
HEllo,
 
Finally someone that replies!
I have a Nvidia Geforce GT240 GDDR5 512MB from XFX on PCI-E 16x

---

### Post by Hippytaff on 2010-12-07
I think therein lies the problem...how far into the boot process do you get...you should be able to get as far as where you choose an os?

if so press e, then change 'quiet splash' to 'nomodeset'

if this doesn't work post back

---

### Post by SnoopNL on 2010-12-07
> **Hippytaff said:**
> I think therein lies the problem...how far into the boot process do you get...you should be able to get as far as where you choose an os?
 
if so press e, then change 'quiet splash' to 'nomodeset'
 
if this doesn't work post back
 
Hello
 
I get the menu stating install to hdd.
After that it is what i posted in the picture of the screen.

---

### Post by Hippytaff on 2010-12-07
What I would do is this - download the minimal or alternative cd, install from there, then, install the recommended drivers (as you proceed with the install you will get asked if you want to install proprietery drivers, then install the desktop
```

sudo apt-get ubuntu-desktop

```

---

### Post by SnoopNL on 2010-12-07
> **Hippytaff said:**
> What I would do is this - download the minimal or alternative cd, install from there, then, install the recommended drivers (as you proceed with the install you will get asked if you want to install proprietery drivers, then install the desktop
```

sudo apt-get ubuntu-desktop

```
 
Ok here is what I came across:
I managed to install with your help, but now comes the fun.
I reboot.
Select ubuntu from GRUB and BAM! the same problem is back.
If I enter my password I hear that ubuntu lets me into my account, but still the same screen.
 
In the boot I read : GPU lockup. So it the problem begins at the GPU.
 
Why would I need a minimal/alternate cd?
This is a mainstream system.
 
I want it to work as it is from the box.
How do I load something like a safe videodriver or something?
If I can only get into ubuntu, that will be all I need.

---

### Post by Hippytaff on 2010-12-07
the nomodeset fix (if you can get the option by pressing e) is the safe graphics mode. I was thinking, if you can install a command line (ie no graphical user interface) based version, you could install your graphics drivers before you install the gui/ubuntu-desktop (gnome and x-org)

Edit -> If you can get into your account, press CTRL+ALT+F1 - you'll be dropped into a terminal. you could try installing the drivers from here!? just a thought :-)

---

### Post by SnoopNL on 2010-12-07
> **Hippytaff said:**
> the nomodeset fix (if you can get the option by pressing e) is the safe graphics mode. I was thinking, if you can install a command line (ie no graphical user interface) based version, you could install your graphics drivers before you install the gui/ubuntu-desktop (gnome and x-org)
 
Edit -> If you can get into your account, press CTRL+ALT+F1 - you'll be dropped into a terminal. you could try installing the drivers from here!? just a thought :-)
 
Thank you!
I will try this tomorrow , it is 1 AM here now.
 
Keep you posted!

---

### Post by Hippytaff on 2010-12-07
Let me know how it goes...bed time for me too :-)

---

### Post by SnoopNL on 2010-12-08
> **Hippytaff said:**
> Let me know how it goes...bed time for me too :-)
 
Ok...
 
It became worse.
Now i do not even see the scrambled windows bootscreen, now i see all glitched colours like purple and grey running across.
 
Is there a way to boot to a commandline version?
I can install from there i guess?
 
Edit:
 
I got it working!
trick was : load the failsafe drivers.
Then install the updated nvidia driver.
Reboot
Done!
 
To Hippytaff: you are great.
Thank you for your help.
 
You are someone who does not quiet at the first try that fails.
I will now make sure to make my fullest of the linux experience.
 
Also, CentOS is next, after that OpenSUSE.

---

### Post by Hippytaff on 2010-12-08
Glad you sorted it - excellent!

Remember to mark the thread as solved in the thread tools at the top of the page so others with the same issues can do what you did...also it might be worth expanding what you did for the benefit of those future issues that others will have too ;-)

oh - and if your distro hopping for a bit try INX for a lesson in cli onlyness (you'll be amazed what you can do without Xorg if you really want to

---

