---
title: "Question about XP on one drive and Ubuntu on second drive"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by white94cam on 2009-01-10
Hello all,

I've been trying to do as much research as I can before posting up questions that I'm sure have been answered before.  I'm wanting to be able to boot up my computer, choose between Ubuntu and XP (using GRUB I guess?) Anyhow, onto the matter at hand...

I'm currently running XP on my primary drive, and I have a totally blank secondary drive which I'm going to install Ubuntu on. This is my understanding of what needs to be done to achieve my goal:

Insert Ubuntu CD, restart, boot from CD
Begin installation process - locate secondary hard drive (IDE drives, so I assume hdb?)
Allow it to partition however it wants
Install GRUB on the XP drive
Finish install

Sorry for the ignorance on the matter, but I wanted to double check that what I'm doing will work.  Also, stupid question - what do I need to do as far as drivers on the Ubuntu drive?  Do I need to find them and install them myself (and for what devices)?

Thanks in advance

Drew

---

### Post by Mutt77 on 2009-01-10
It would be easier to remove the xp drive then install Ubuntu on the drive still in the machine. Then re-install the xp drive then install grub as your bootloader. Gpart could also help during the install with both drives installed. Not sure if Gpart now sees two drives. I use Ubuntu exclusively on laptop then XP on a desktop for using Dreamweaver.

---

### Post by oilchangeguy on 2009-01-10
> **Mutt77 said:**
> It would be easier to remove the xp drive then install Ubuntu on the drive still in the machine. Then re-install the xp drive then install grub as your bootloader.

+1 on this. here's what i did, when i had a dual boot with two hard drives. disconect the drive with windows. set the ubuntu drive to master. install ubuntu. then re-connect the windows drive, set it to slave. grub picked up the drive, and i could select which os to boot into.

---

### Post by white94cam on 2009-01-10
> **Mutt77 said:**
> It would be easier to remove the xp drive then install Ubuntu on the drive still in the machine. Then re-install the xp drive then install grub as your bootloader.

So I can install Ubuntu on a totally blank hard drive without any drivers?  Also, I read that it was better to keep the Windows drive in and upon installation Ubuntu would automatically recognize it and it would load XP as an option in the GRUB menu.

But, I really have no idea what I'm talking about haha, which is why I'm here asking for advice:mrgreen:

---

### Post by Mutt77 on 2009-01-10
Yes it would be easier. And grub will pick the xp drive upon re-install. LEAVE UBUNTU DRIVE AS MASTER FOR THIS TO HAPPEN. Don't worry about drivers if needed then you can connect and get them most drivers are preinstalled or easy to configure.

---

### Post by stanz on 2009-01-10
Yeah, having grub on the same drive as Ubuntu is painless.
Also, making the Ubuntu drive the "Master", and the xp HD the "Slave" will give you the choice of which to boot.
** Ya need to open your box - switch the cables - and boot to the install cd.
Ubuntu will recognize xp...possible "hdb"
and you'll install Ubuntu on "hda".

_** Check thru the Wiki/Doc's ...there must be a good step by step for ya to guide ya!**_

---

### Post by white94cam on 2009-01-10
Okay...cool.  I guess I'll give it a shot here in a few minutes.  I've never used a Linux OS before so I'm excited to see what it has to offer

---

### Post by oilchangeguy on 2009-01-10
> **white94cam said:**
> Okay...cool.  I guess I'll give it a shot here in a few minutes.  I've never used a Linux OS before so I'm excited to see what it has to offer

if you are leaving your windows hard drive plugged in, back up any data BEFORE you attempt to install ubuntu.

---

### Post by fr0sty on 2009-01-10
I agree with you all the way up until you say allow it to partition how it wants. Try following this amazing guide to help you with installation. guide and if this isnt good enough iv typed out how to do the manual installation for the harddrive: 

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

I would recomend doing a manual partition. This way it doesnt resize your xp harddrive. you will have to specify that it to install to the second harddrive. Its really simple:

1. create a 2gb "swap"
2. create however big you want ubuntu partition with the label as "/" you will want that in the "ext3 journaling system format"
3. from there it should be pretty straighforward.
4. When you install ubuntu, Grub will (or should) automatically install over your XP bootloader. (dont worry, grub should add XP to its boot list choices.)

Then you have installed ubuntu. Yay

5. as for drivers, the most important ones will be Wireless and Graphics.

To get the Wireless one (if you use wireless) you are going to need to physically hook the computer with an ethernet cable. THen hopefully ubuntu will find a driver for your wireless adapter. If not, then go to "applications", then click "Add/remove". The window that opens, you will want to click the box next the the "show" and change the selection to "all available applications". Say yes to the questions about adding unsupported applications. Then in the searchbox on the upper right corner, type in the word "ndiswrapper". Select the application called "Windows Wireless Drivers" for installation and then click "apply changes"
Close the window once installation has completed. Now click "system", go to "administration" and then at the bottom should be "windows wireless drivers." click that. The program will open. (it can be super-duper slow to load and look like its crashing, just give it time). if you had a CD with your wireless drivers for xp on it, slap in the cd drive and then copy the 32bit .inf file from the drivers folder on the disk to your documents. then switch back to the "windows wireless driver" program and click "install new driver". navigate to where you saved the .inf file in your documents and then click it. Then if things go well, you should have working wireless. (if it finds your hardware.)

Ok. now for the graphics. Just simply go to "system", "administration" and then click "hardware drivers" and click to "enable the driver. it will then proceed to download and install the driver. You will need to reboot after the install. For all the cool effects of compiz-fusion. go to "applications", and click "add/remove". Then type in "ccsm" and install the package. Once you have rebooted and the graphics drivers are installed, you can click "system" go to "prefrences" and then click "advanced desktop effects settings" and wala u can begin customizing. 

Hopefully this guide is helpful and not too confusing. Good luck! (feel free to message me if you need help)

---

### Post by fr0sty on 2009-01-10
i should be doing ubuntu docutmentation if that guide works out.

---

### Post by white94cam on 2009-01-10
> **fr0sty said:**
> i should be doing ubuntu docutmentation if that guide works out.

lol :mrgreen:

Thank you guys for all your help....I'll report back later today

---

