---
title: "PLEASE HELP! netgear wg511 v2 in ubuntu 10.10"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by thecompans on 2010-11-15
this is driving me NUTS! i am so close to going back to xp!
can somebody PLEASE just give me a staight explanation as to how the heck i get this working? all the other forums give random mixed solutions and its so confusing!:(

---

### Post by thecompans on 2010-11-15
> **thecompans said:**
> this is driving me NUTS! i am so close to going back to xp!
can somebody PLEASE just give me a staight explanation as to how the heck i get this working? all the other forums give random mixed solutions and its so confusing!:(

oh and also i cnat figure out how to install this ndiswrapper.tar.gz so can you help me with that first? thanks:confused:

---

### Post by thecompans on 2010-11-15
> **thecompans said:**
> oh and also i cnat figure out how to install this ndiswrapper.tar.gz so can you help me with that first? Thanks:confused:

please respond! Come on!

---

### Post by thecompans on 2010-11-15
> **thecompans said:**
> please respond! Come on!

im switching to damn small linux

---

### Post by BrandonC19 on 2010-11-15
Well we would certainly be glad to help, but first we need to know, what exactly is going on?

---

### Post by anewguy on 2010-11-16
First - it's a volunteer forum - it takes time, something you did not do was WAIT for someone to answer.  It's not instant, sometimes it can be a few minutes, others a few hours and others yet a few weeks.

Now to try to help with your problem:

You apparently read something that said you needed to use ndiswrapper.  I'm not going to go out and search to see if there is an alternative at this point - instead I'm going to give you directions for getting ndiswrapper installed and your driver loaded.  So......

[LIST=1]
[*]FORGET the .tar file you have for ndiswrapper
[*]After booting ubuntu, put the installation CD in the drive (or if from USB, plug in the USB flash drive)
[*]If a message comes up about a software source having been mounted, cancel it
[*]Using "Places", click on your CD drive or USB stick on the screen
[*]Navigate to the /pool/main/n folder.  You will find 2 folders there that we will be using:  ndisgtk and ndiswrapper.
[*]The order is important in installing these, so please follow step-by-step:
[LIST]
[*]navigate to the ndiswrapper folder.
[*]Double-click on the ndiswrapper-common file first to begin its installation.  If prompted for a password, it is your normal password but it won't show on the screen as you are typing it.  Wait for the installation to finish.
[*]Double-click on the ndiswrapper-utilities file to begin its installation.  Same thing for password if prompted.  Wait for the installation to finish.
[*]Go back 1 folder, then navigate to the ndisgtk folder
[*]Double-click on the ndisgtk file to begin its installation.  Same thing applies here for password.  Wait for the installation to finish.
[/LIST]
[*]This has just installed everything for ndiswrapper and its GUI front end ndisgtk.
[*]Now you need the Windows XP (*ONLY*) drivers (.inf and .sys files) for your adapter.  If your Ubuntu is 64-bit, then the drivers must be 64-bit.  If you just downloaded normal Ubuntu you should use the 32-bit drivers.  If you are dual-booting you can copy/paste these files from the Windows partition.  Just paste them onto your desktop.
[*]Click on System/Administration/Windows Wireless Drivers.  If prompted for a password, just enter your normal password.
[*]Click "New" (or perhaps it's add - don't have it open right now).
[*]In the driver file box, browse to the desktop and click on the drivers .inf file, then click "OK" (or "Add" - again don't have it opened).  When it finishes it should show your device.
[*]Close out of the ndisgtk window.
[*]Right-click on the network manager icon on the top bar.  Be sure "Enable Wireless" is marked as enabled - if not then enable it.  Wait a couple of minutes.
[*]Left-click on the network manager icon - you should now see wireless networks. [/LIST]

A few things to be aware of:
[list=1]
[*]If your router is not broadcasting the network ID (in other words, it's a hidden network) you must left-click on network manager and select connect to hidden network and fill in the information as asked.
[*]If your router uses encryption, you will need the type and the password/passphrase.
[*]If your router uses MAC filtering, and if you have never used wireless from this device through your network, then you will need to add the MAC address of the device to the router list.
[/list]


Dave

---

### Post by plucky on 2010-11-16
This [Link](http://ubuntuforums.org/showthread.php?p=9716636#post9716636) might help.

OR

This [link](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)

As it has the same chipset.

Good Luck

---

### Post by anewguy on 2010-11-16
Somehow I think the OP bailed since they posted the thread, waited 1 hour, then posted more replies about not getting help and going to a different distro.  All in all, we will probably be best without them until they change their attitude anyway.

Dave ;)

---

### Post by Hippytaff on 2010-11-16
> **anewguy said:**
> Somehow I think the OP bailed since they posted the thread, waited 1 hour, then posted more replies about not getting help and going to a different distro. All in all, we will probably be best without them until they change their attitude anyway.
 
Dave ;)
 
If it's any consolation Dave, I have the exact same Wirless card on the wifes Laptop which I'll be installing Lubuntu on and was wondering whether Ndsiwrapper would be able to get it working, and now I know :-D

---

### Post by anewguy on 2010-11-16
> **Hippytaff said:**
> If it's any consolation Dave, I have the exact same Wirless card on the wifes Laptop which I'll be installing Lubuntu on and was wondering whether Ndsiwrapper would be able to get it working, and now I know :-D

As far as I know it works with lubuntu - it should, as I think lubuntu is just a modified (slightly lighter?) version of ubuntu, and either way it will still have the kernel in its guts.  I would guess you just have to be sure you are matching kernel versions - I wouldn't try ndiswrapper for a newer kernel (if there even is such an animal as a "new" version of ndiswrapper).  If it's not on the installation media, let me know and I can email the ndisgtk and ndiswrapper stuff as an attachment for you to try if you want.

Dave ;)

---

### Post by Hippytaff on 2010-11-16
Thanks Dave. It's going to be a pain because for some reason the ethernet port is a different fitting to any of the ethernet cables I have which is odd (I thought they were standard, but obviously not). So O'ii be doing everything offline with just a usb pen to install wrapper and my laptop for reference.

Waiting until I've got time and peace and quiet for a few hours. :-)

---

### Post by anewguy on 2010-11-16
Hippytaff - I just downloaded and burned the lubuntu 10.10 CD, and the structure is the same - in /pool/main/n both the ndisgtk and ndiswrapper stuff is still there.

Just to let you know as you had me curious!

Dave ;)

---

### Post by anewguy on 2010-11-16
> **Hippytaff said:**
> Thanks Dave. It's going to be a pain because for some reason the ethernet port is a different fitting to any of the ethernet cables I have which is odd (I thought they were standard, but obviously not). So O'ii be doing everything offline with just a usb pen to install wrapper and my laptop for reference.

Waiting until I've got time and peace and quiet for a few hours. :-)

What kind of port is it?  Is it possible to take a picture of it and post it here so we can see it?

Also - what kind of laptop?  Given that, maybe I can look on the support page and see if it shows anything regarding the port.

On the side - I like working with you - you don't anger the OP, you keep things down to a level which one hopes the newbie can understand, and you seem to me to be providing good answers!  It's a pleasure when there are people like you on the forum!

Dave ;)

---

### Post by Hippytaff on 2010-11-17
Thanks Dave :-) only been using ubuntu for six months, learned quite a bit so I like to help out where I can with the basics that had me stumped origianlly.
 
The Laptop is an old Sony Vasio - I don't think about looking at the support page. Will do that too. I think I'm getting into new thread teritory here though. Feel free to PM me though.
 
Cheers
Gareth

---

### Post by skippergimp on 2010-11-17
Thanks for the info.  I have an old laptop which I have started using again.  

The thing I find strange is that my card used to work without *any* effort in linux.  I upgraded the distro or did a fresh install and it stopped working and I haven't had the time to investigate.

For me, this is the second time a piece of hardware that just *worked* with no effort has stopped working in linux.

---

### Post by Hippytaff on 2010-11-17
When you installed 10.10 did you enable proprietary (restricted) drivers, and did you have the ethernet cable plugged in (ie were online).
 
Which card is it? if it worked on a previous version it should in theory work in 10.10. If you go to System menu there should be an option in one of the menus to get alternative drivers. (Can't remember where in systyem, and I'm not at home to check)
 
if you can post the output of
```

lspci

```
we can have a look at what drover you need and whether this is just a matter of installing the driver as per above or whether there is more to it :-)

---

### Post by skippergimp on 2010-11-17
Propritary drivers repo enabled.

Ethernet plugged in during install but still had loads of updates post install. I thought I had ticked the perform update during install option.

lspci below:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
02:05.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
02:05.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

---

### Post by skippergimp on 2010-11-17
Sorry, forgot to mention details about the card.

Netgear 54Mbps wireless PC card 32bit cardbus WG511

---

### Post by Hippytaff on 2010-11-17
In that case ndiswrapper and the gui ndisgtk need to be used to wrap the windows xp driver for it to work in linux. Look into ndiswrapper - any troubles post back...Dave (anewguy) is probably better placed to talk you through this :-)

---

### Post by skippergimp on 2010-11-17
Any ideas why the card isn't working fresh out of the box?  I think I bought it as it was listed as linux compatitable.  Do you know if the prism54 driver been removed/changed?

[This]("http://wiki.debian.org/prism54#supported-p54pci") link suggests that the card should work without ndiswrapper

---

### Post by Hippytaff on 2010-11-17
Maybe something needs blacklisting in that case - Sometimes there is a driver conflict.

Also try
```

rfkill unblock all

```
to unblock any soft/hard wireless blocks :-)

---

### Post by anewguy on 2010-11-20
The link you provided does provide the instructions for downloading and installing the drivers - did you do that?

Dave ;)

---

### Post by skippergimp on 2010-11-20
Previously, the prism drivers were automatically loaded during installation.  It appears that this isn't the case anymore.  I will look at ndiswrapper tonight.

---

### Post by anewguy on 2010-11-20
You could always install the drivers as per the link you provided.  If you choose instead to use ndiswrapper, please remember the following:
[LIST]
[*]DO NOT FOLLOW OLD POSTS THAT SAY TO INSTALL FROM SOURCE
[*]boot ubuntu
[*]put your LiveCD in the drive and wait for it to spin up.  If a message comes up about a disk with software packages just cancel the message.
[*]using "Places", open the CD and navigate to the /pool/main/n/ndiswrapper folder
[*]double-click on the ndiswrapper common file to install it.  When prompted, just enter your normal password (it won't show on the screen).  Wait for the installation process to finish.
[*]double-click on the ndiswrapper utilities file to install it.  When prompted, just enter your normal password (it won't show on the screen). Wait for the installation process to finish.
[*]go back 1 folder to the /pool/main/n folder
[*]now go to the ndisgtk folder
[*]double-click on the ndisgtk file to start installation.  When promted just enter your normal password (it won't show on the screen).  Wait for the installation process to finish.
[/LIST]

This has installed ndiswrapper and it's GUI'd front-end ndisgtk.  Next we need the Windows driver and then to install it:

[LIST]
[*]the driver files (the .inf and .sys files) must be for Windows XP
[*]the driver files must match the "type" of ubuntu:  if you just downloaded normal Ubuntu you need the 32-bit drivers.  However, if you downloaded and installed the 64-bit version of Ubuntu you will need 64-bit drivers.
[*]copy these drivers to your desktop
[*]start up ndisgtk by going to System/Administration/Windows Wireless Drivers
[*]click on add (or perhaps it's "new")
[*]point it to your desktop and the .ini file for your driver
[*]when finished, it should show your device.
[/LIST]

Now some other things to check:

[LIST]
[*]right-click on the network manager icon and be sure the "Enable Wireless" is enabled
[*]left click on the network manager and you should see wireless networks.
[*]if your network is "hidden" (e.g., the router is set not to broadcast the ESSID), you will have to use network manager and manually set up the connection to a hidden network
[*]remember to match encryption and the password/passphrase
[*]if the router uses MAC filtering, and if this PC has never connected to the router with the current adapter, be sure to add the PC's MAC address to the router's table
[/LIST]

You should be set to go.  Let us know if you have any problems or questions along the way, and let us know if it works for you.

Dave ;)

---

### Post by Hippytaff on 2010-11-20
> **anewguy said:**
> You could always install the drivers as per the link you provided.  If you choose instead to use ndiswrapper, please remember the following:
[LIST]
[*]DO NOT FOLLOW OLD POSTS THAT SAY TO INSTALL FROM SOURCE
[*]boot ubuntu
[*]put your LiveCD in the drive and wait for it to spin up.  If a message comes up about a disk with software packages just cancel the message.
[*]using "Places", open the CD and navigate to the /pool/main/n/ndiswrapper folder
[*]double-click on the ndiswrapper common file to install it.  When prompted, just enter your normal password (it won't show on the screen).  Wait for the installation process to finish.
[*]double-click on the ndiswrapper utilities file to install it.  When prompted, just enter your normal password (it won't show on the screen). Wait for the installation process to finish.
[*]go back 1 folder to the /pool/main/n folder
[*]now go to the ndisgtk folder
[*]double-click on the ndisgtk file to start installation.  When promted just enter your normal password (it won't show on the screen).  Wait for the installation process to finish.
[/LIST]

This has installed ndiswrapper and it's GUI'd front-end ndisgtk.  Next we need the Windows driver and then to install it:

[LIST]
[*]the driver files (the .inf and .sys files) must be for Windows XP
[*]the driver files must match the "type" of ubuntu:  if you just downloaded normal Ubuntu you need the 32-bit drivers.  However, if you downloaded and installed the 64-bit version of Ubuntu you will need 64-bit drivers.
[*]copy these drivers to your desktop
[*]start up ndisgtk by going to System/Administration/Windows Wireless Drivers
[*]click on add (or perhaps it's "new")
[*]point it to your desktop and the .ini file for your driver
[*]when finished, it should show your device.
[/LIST]

Now some other things to check:

[LIST]
[*]right-click on the network manager icon and be sure the "Enable Wireless" is enabled
[*]left click on the network manager and you should see wireless networks.
[*]if your network is "hidden" (e.g., the router is set not to broadcast the ESSID), you will have to use network manager and manually set up the connection to a hidden network
[*]remember to match encryption and the password/passphrase
[*]if the router uses MAC filtering, and if this PC has never connected to the router with the current adapter, be sure to add the PC's MAC address to the router's table
[/LIST]

You should be set to go.  Let us know if you have any problems or questions along the way, and let us know if it works for you.

Dave ;)

Dave, I've copied this to a file for future reference, just checking your ok with that :-)

---

### Post by anewguy on 2010-11-20
> **Hippytaff said:**
> Dave, I've copied this to a file for future reference, just checking your ok with that :-)

I have no problem with it - everything is open source, and my advice is open-source as well ;)  Some would say that some of my advice is so open-source it has holes in it ;) ;)

BTW - if you find an error or typo let me know.  And.....you're smarter than me - as I was typing this I was thinking "jeez, seems like I type this a lot...." - duh!!!  Should have just saved it in a file as you are!  ;)

Have a good one!

Dave ;)

---

### Post by Hippytaff on 2010-11-20
Dave, my memory is so bad I've learned to commit everything to file (and then usb stick) :-)

---

