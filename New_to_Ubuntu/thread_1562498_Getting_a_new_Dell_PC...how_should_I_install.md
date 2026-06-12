---
title: "Getting a new Dell PC...how should I install?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by TheEddy on 2010-08-27
I am thinking of getting one of their pc's that come with windows 7 by default.  I plan on uninstalling windows 7 just to get it out of the harddrive.  I will then install ubuntu instead.

Or should I leave it on there and partition the disk and install ubuntu then?

Or should I use wubi?

Or should I just buy one of their laptops that come with ubuntu pre installed?

---

### Post by lordhaworth on 2010-08-27
Get a dell laptop that comes with ubuntu and then install a real ubuntu over that. That will save you money given the one with windows install costs lots more.


Trust me - its worth installing ubuntu from a live cd/download rather than settling for the one that comes with a ubuntu laptop.

---

### Post by TheEddy on 2010-08-27
> **lordhaworth said:**
> Get a dell laptop that comes with ubuntu and then install a real ubuntu over that. That will save you money given the one with windows install costs lots more.


Trust me - its worth installing ubuntu from a live cd/download rather than settling for the one that comes with a ubuntu laptop.
Wait, so there's difference?

---

### Post by lordhaworth on 2010-08-27
> 
Wait, so there's difference?



Theres no difference in the hardware, but the ubuntu that comes with a dell laptop is a bit outdated now and is also dell-ified. This means that a lot of stuff is quite restricted (or so I found) - for example the list of programs available in the add/remove programs was much smaller in the pre-installed dell version.

---

### Post by lordhaworth on 2010-08-27
Don't get me wrong, if you ar enew to ubuntu the pre-installed dell version is fine to get going with and worth getting over a windoows one if you are definitely wanting ubuntu given that it is cheaper

---

### Post by tom.swartz07 on 2010-08-27
If you do happen to get a computer with Windows on it, boot to windows just once to get all of the hardware initialized.

I had a friend that installed Ubuntu on the first boot and couldn't get the wifi to work. After wracking my brain, I tried booting to windows to see if it was actually a defective antenna, but it turned out it just needed to be turned on and used once.

Also, when you first boot to windows, take advantage of the chance to update all of the hard-to-get-at stuff, Dell is notorious for only giving BIOS updates in .exe formats that will not work with WINE. Check and make sure you have all of the proper drivers, updates, etc.


AFTER all of that, and youre sure that the computer is all good to go, wipe the drive and install Ubuntu. Then youre good as gold to go.

---

### Post by I_Want_To_Learn on 2010-08-27
Last time I called Dell, they didn't give me any price difference between their laptops with Windows 7 compared to their laptops with Ubuntu....that was a while ago though.

IMO, I would get a PC with Windows 7. You'll then have the newest version of Windows anytime you need it (sometimes it's good to have it as backup) & install the newest version of Ubuntu via reformat or dual-boot (very easy to do). Ubuntu is free to use...Windows is paid software. If there's not much price difference, why not get the paid software included?

---

### Post by Iowan on 2010-08-27
For what it's worth, theres an entire [subforum]("http://ubuntuforums.org/forumdisplay.php?f=342") for Dell support. Dunno if that's a good thing, but hopefully you can find some Dell-specific answers there. :)

---

### Post by sidzen on 2010-08-27
Here's what I would do:

Get SystemRescueCD and burn it to a CD -- [http://sourceforge.net/projects/syst...sysresccd-x86/]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") 
(I recommend 1.3.5)
Use from sysresccd  either *dban* or the dd command < dd if=/dev/zero of =/dev/sda bs=4096 conv=notrun,sync > to wipe hard drive with zeros for a clean install.
Partition your hdd with *gparted* (fom sysresccd), making sure to flag the / partition as_ bootable_.
Install the ubuntu of your choice & enjoy!

---

### Post by uRock on 2010-08-27
> **TheEddy said:**
> I am thinking of getting one of their pc's that come with windows 7 by default.  I plan on uninstalling windows 7 just to get it out of the harddrive.  I will then install ubuntu instead.

Or should I leave it on there and partition the disk and install ubuntu then?

Or should I use wubi?

Or should I just buy one of their laptops that come with ubuntu pre installed?
You are going to pay the same price either way. Get your copy of Windows 7, then shrink the partition down to about 50GB, so that you can have run to play, then install Ubuntu of the rest of the hard drive.

---

### Post by LiquidMeson on 2010-08-27
just curious, but what laptop where you originally look at?/pc? link

---

### Post by dFlyer on 2010-08-27
First - I would Clone my Window 7 Drive. Should you ever need to update the BIOS, it would be a lot easier, just to restore windows and upgrade the BIOS and than boot the ubuntu live cd to make sure all you hardware works correctly, before proceeding to the next step.

Second - Install ubuntu 10.04.1, will work great out of the box, at least it does on my Dell Studio 1735.

Third - Only if you want the Dell Recovery and Dell System diagnostic tools you will need to roll a cd/dvd using Dell Recovery Media Creator - they (Dell) recommend dvd but a cd works just as well and uses less space.

---

### Post by lordhaworth on 2010-08-28
There was certainly a cost difference ~2yr ago by about £70 which is huge on a ~£300/£400 laptop. I will have a look at their website, but given that ubuntu OS is free and Windows7 is not I would be very surprised if they cost the same

---

### Post by lordhaworth on 2010-08-30
wft? I queried them about cost difference and was sent the following:

> 
Thanks for contacting Dell. ubuntu OS is provided only for desktops. Are you looking at the deskotps or laptops

Thanks
UK sales.


I have told them that I am only really interested in cost difference so desktop will do. Don't know if this is a recent development and might affect the OP decision... 

? What about netbooks? Confused face

---

### Post by libssd on 2010-08-30
> **I_Want_To_Learn said:**
> IMO, I would get a PC with Windows 7. You'll then have the newest version of Windows anytime you need it (sometimes it's good to have it as backup) & install the newest version of Ubuntu via reformat or dual-boot (very easy to do). Ubuntu is free to use...Windows is paid software. If there's not much price difference, why not get the paid software included?
Agreed; much as I love Ubuntu and loathe Windows, there are times when you absolutely **must** have Windows, even if it's only once a month. But, if you do install Ubuntu in a partition, make sure that you boot in Windows once a month to download security updates. The longer the interval between boots, the more there are, and the longer it takes.

---

### Post by uRock on 2010-08-30
> **libssd said:**
> Agreed; much as I love Ubuntu and loathe Windows, there are times when you absolutely **must** have Windows, even if it's only once a month. But, if you do install Ubuntu in a partition, make sure that you boot in Windows once a month to download security updates. The longer the interval between boots, the more there are, and the longer it takes.
And be ready to restart and run them again, as we know how they love to have multiple updates that can only go one at a time. Adobe has an update about once every other week that wants a restart, also.

---

### Post by migs73 on 2010-08-30
I got my Dell with Vista. It was so rubbish it made me dump MS and go Ubuntu. Best thing I ever did.
I now have Ubuntu on my hard drive as my only OS and used my dell DVD to install Vista in Virtualbox, for those annoying times when only MS will do.
Definately remember to boot into it at least once or twice a month otherwise you'll spend hours and hours on updates.

Was reticent about using Vbox as it sounded daunting, but couldn't have been easier. DON'T use the OSE one in the repo's though, go to the website and download the PUEL one from there and follow all the Debian based instructions on the page.

---

