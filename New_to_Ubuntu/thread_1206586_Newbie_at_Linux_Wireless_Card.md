---
title: "Newbie at Linux: Wireless Card"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by alasdairsim on 2009-07-07
Today I finally installed Linux on the Laptop, an Acer Aspire 3630.

I installed Ubuntu Jaunty 9.04.

My wireless card is a Broadcom 4318. I've done a bit of research and noticed that this is particularly difficult to install, and I tried some of the methods , however being a complete noob at linux its hardly suprising that I still can't get it to work.

Any suggestions? Is my version of Linux the most suitable for this card?

I've tried:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

Plus a few other methods.

Any help would be most appreciated as all i need to use the internet for is writing for my blog, researching and the like.

Alasdair

---

### Post by Paddy Landau on 2009-07-07
I don't know the answer, but with my brother's Broadcom yesterday, all we did was add Medibuntu to the repositories and then install all updates. After that, the wireless worked (and I can't tell you why).

---

### Post by nielsek on 2009-07-07
have you tried this: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102) ?

---

### Post by alasdairsim on 2009-07-07
What I think I stumbled on was this bit; [http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595](http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595)

installing the acer driver. =s

---

### Post by Zero++ on 2009-07-07
Have you tried getting the Windows Wireless Drivers app. It's in the add/remove under the Applications menu. I had tons of trouble with my wireless USB and this fixed it in 10 seconds. You just need the .ini (driver file) for windows and the program should do the rest. Here's a link to the homepage  [http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/)

Hope this helps!

---

### Post by alasdairsim on 2009-07-07
> **Zero++ said:**
> Have you tried getting the Windows Wireless Drivers app. It's in the add/remove under the Applications menu. I had tons of trouble with my wireless USB and this fixed it in 10 seconds. You just need the .ini (driver file) for windows and the program should do the rest. Here's a link to the homepage  [http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/)

Hope this helps!

Thanks! Its now recognized my network card and the light comes on. But even though it says it's connected to my home network it has no signal strength?

I know it isn't the card because I used it under windows this morning in the same place and it's strength was "excellent".

---

### Post by random turnip on 2009-07-07
Im no expert, all i can tell you to do is check that the driver is enabled and that there is only 1 driver trying to access the card and make sure that you are fully updated (get an ethernet cable), mine didn't work in 8.10, but works flawlessly in 9.04.

---

### Post by alasdairsim on 2009-07-07
UPDATE.

Well its finally found my network but it fails to connect. Signal strength is there and ive entered the correct network key; the little 'connecting' animation plays for about 30 seconds then it just says wireless disconnected?

---

### Post by Paddy Landau on 2009-07-07
Have you done the correct configuration for nsidwrapper?

Read here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by theozzlives on 2009-07-07
Are you using Kubuntu by chance, Kubuntus network manager does just that with the wireless... only fix I know is to use a different network manager.

---

### Post by alasdairsim on 2009-07-07
> **theozzlives said:**
> Are you using Kubuntu by chance, Kubuntus network manager does just that with the wireless... only fix I know is to use a different network manager.

Yea I think so. Where do I get another manager from?

---

### Post by theozzlives on 2009-07-07
That'll be hard without internet, but I've heard good things about wicd. Maybe it comes in a *.deb file that you can download with Windows.

---

### Post by alasdairsim on 2009-07-07
> **theozzlives said:**
> That'll be hard without internet, but I've heard good things about wicd.

I have it connected to a LAN at the minute and my desktop is upstairs so i can access the internet, ha.

It seems to stall on 'Obtaining IP address".

---

### Post by LewRockwell on 2009-07-07
I'm always very cautious about hacking on something before working diligently to cover all the standard bases regarding setting up a new operating system.

I've had good luck with both the latest Ubuntu(Jaunty) and the latest Puppy Linux(4.2.1) regarding hardware issues.

First of all, if you've hacked on it...stop

Do the necessary back-ups, clones, burn CD/DVDs...whatever you need to do for secure data retention

Then give your hard drive a good scrubbing with the erase disk function on the Parted Magic LiveCD([http://www.partedmagic.com/](http://www.partedmagic.com/))

Parted magic also has Clonezilla for your data management, Testdisk and Photorec for data recovery, and Gparted for your repartitioning after scrubbing the hard drive

If for some reason you need Clonezilla LiveCD by itself then go here([http://www.clonezilla.org/](http://www.clonezilla.org/))

While you're downloading stuff you might as well pick up Super Grub Disk just to have it onhand([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

After back-ups, scrubbing, and repartitioning, then you can do a fresh, clean install and I also recommend having a hard wire ethernet connection for your first update session right after the installation

******************

I should note that if you're doing a dual-boot with windows and you don't want to go through the pain of reinstalling it then there are additional steps required

You'll want to back-up anything you aren't willing to lose permanently
You'll want to organize retained data and to get rid of useless and/or outdated stuff that's just wasting valuable space
I use CCleaner([http://www.ccleaner.com/](http://www.ccleaner.com/)) or if you prefer using CNET for your downloads([http://download.cnet.com/ccleaner/](http://download.cnet.com/ccleaner/))

Then, run checkdisk and defrag from your normal windows account
Then, reboot the machine into safe mode(probably by depressing the F8 key about twice per second as you first turn the machine on...you may need to experiment to do this properly)
Then, in safe mode, defrag several times(the first few times it can be quite time consuming while the data is organized and compacted)

It's likely that windows was given your entire hard drive to play in and so now we want to shrink the size of the primary partition that windows is in so that we can add more partitions

I shrink the windows partition in steps and after each reduction I reboot into windows safe mode and run a defrag(you'll note that it is common for windows to notice a partition size change during the boot and for it to run checkdisk to correct any deficiencies)

***Note: I have ALWAYS done the procedure in this manner and it has ALWAYS been successful, but you should always be mindful that the world is not perfect***

As an partitioning example:

Say you have a 120GB hard drive with windows on it
You'll follow the shrinking procedure to reduce the windows partition to perhaps as little as 20-30GB
Then you'd add a swap partition equal to your equipments maximum ram capacity(you'll note in other discussions regarding swap size that other recommendations suggest differing amounts depending on your usage and whether or not you have hibernation enabled...I forego all that with my simple and straight-forward method of 1xMaxRam)

So we'll say you've got a 4GB max ram machine...so a 4GB swap partition it is...

Then you'll create a third primary partition for Ubuntu and again I would set the size at 20-30GB

Now you will take the rest of the unallocated space on the drive and make it an extended partition

Inside that extended partition you can create logical partitions for additional data storage and/or additional operating systems that you might want to install and experiment with

In the dual/multi-boot scenario you'll be using the Grub bootloader and I highly recommend learning how to use the Supergrubdisk AND how to manually edit the grub file(menu.lst)

You can search my posts for additional information including one gentleman who has over a hundred operating systems on one machine

As always, take your time and do the research first...the search engine is indeed your best friend and will deliver the whole world to your fingertips!

.

---

### Post by LewRockwell on 2009-07-07
> **theozzlives said:**
> Are you using Kubuntu by chance, Kubuntus network manager does just that with the wireless... only fix I know is to use a different network manager.

original post reports Ubuntu 9.04 Jaunty...

.

---

### Post by LewRockwell on 2009-07-07
> **alasdairsim said:**
> Yea I think so. Where do I get another manager from?

your original post reported you were using Ubuntu 9.04 Jaunty

are you now trying Kubuntu?

.

---

### Post by alasdairsim on 2009-07-07
> **LewRockwell said:**
> your original post reported you were using Ubuntu 9.04 Jaunty

are you now trying Kubuntu?

.

Hey, sorry, read the Kubuntu post wrong; i was in a rush to go out at the time, ha.

No its Ubuntu Jaunty 9.04.

Its not a dual-boot with windows; I have nothing of value on this laptop at the minute, its really just for playing around with Linux. I use for desktop for anything important.

---

### Post by LewRockwell on 2009-07-07
> **alasdairsim said:**
> Hey, sorry, read the Kubuntu post wrong; i was in a rush to go out at the time, ha.

No its Ubuntu Jaunty 9.04.

Its not a dual-boot with windows; I have nothing of value on this laptop at the minute, its really just for playing around with Linux. I use for desktop for anything important.

Sweet! Then you can scrub it clean and go to town!

Enjoy!

.

---

### Post by alasdairsim on 2009-07-07
> **LewRockwell said:**
> Sweet! Then you can scrub it clean and go to town!

Enjoy!

.

I did a clean installation of Ubuntu; the LAN works fine on it, the wireless just doesn't seem to get past "obtaining IP address".

---

### Post by LewRockwell on 2009-07-07
> **alasdairsim said:**
> I did a clean installation of Ubuntu; the LAN works fine on it, the wireless just doesn't seem to get past "obtaining IP address".

have you tried rebooting(power cycling) your router?

.

---

### Post by alasdairsim on 2009-07-08
> **LewRockwell said:**
> have you tried rebooting(power cycling) your router?

.

I have. My wireless connection works fine on my desktop.

Now it doesn't even get to 'obtaining IP', it says 'putting interface down' for about a second then nothing happens =s

---

### Post by alasdairsim on 2009-07-08
After installing Wifi-Radar I got the following message when trying to connect:

"SIOCSIFNETMASK: Cannot assign requested address
SIOCADDRT: Invalid argument
Unsupported driver '-P'."

---

### Post by alasdairsim on 2009-07-09
Anyone?

---

