---
title: "Another Wireless Question..."
date: 2009-09-24
forum: New to Ubuntu
---

### Post by bedforce on 2009-09-24
So I want to set up my wireless pci card (Linksys WMP45G), but my computer (desktop) is too far from the router so _I cannot establish a wired connection_.  I've done this once before, so I know it can be done, but that was a year ago; I've forgot how and I just built a new computer and want to set it up again.  And as much as I love Ubuntu and it is awesome and everything, I really wish they could have made it so I don't need to connect to the internet to connect to the internet.  Any help would be greatly appreciated!

~Mike

---

### Post by swoody on 2009-09-25
Hello bedforce, and welcome back ):P

Have you already tried looking under System>Administration>Hardware Drivers for an available wireless driver? If it's not there, can you please post the output of:
```
lspci | grep Network
```

---

### Post by anewguy on 2009-09-25
If you have or can get the Windows driver files (the .inf and .sys files) for your card, then you can install using ndiswrapper.   Ndiswrapper can be installed from the LiveCD - it's in the n folder under main/pool or pool/main - I don't have my CD handy or I'd give you the exact path.  Ndiswrapper and ndisgtk are both there.  By using them, you won't need a wireless connection until you've installed them.

If you need help with ndiswrapper just post back.

Dave :)

---

### Post by bedforce on 2009-09-26
Thanks Dave, this is looking familiar now :)

I've installed the ndiswrapper.  I'm not sure where it went though...

I've got the driver files; I have  these 4 files of interest in my driver folder:

AUTORUN.INF
netani.inf
wnihdd50.sys
wnihdd51.sys

Where do I go from here?  Thanks a lot!  Once I get internet in Ubuntu I won't have to reboot into windows and back again to get information and the process of troubleshooting and setting up the system gets much easier.

---

### Post by anewguy on 2009-09-27
> **bedforce said:**
> Thanks Dave, this is looking familiar now :)

I've installed the ndiswrapper.  I'm not sure where it went though...

I've got the driver files; I have  these 4 files of interest in my driver folder:

AUTORUN.INF
netani.inf
wnihdd50.sys
wnihdd51.sys

Where do I go from here?  Thanks a lot!  Once I get internet in Ubuntu I won't have to reboot into windows and back again to get information and the process of troubleshooting and setting up the system gets much easier.

Are you sure on the model?  You initially said wmp45g, but linksys doesn't have that as a valid model number - they DO have a wmp54g though - would that be it.  If it's wmp54g we would also need the model number - it should be on the card itself on the Linksys label.

Could you do the following in a terminal window and post back the line that says it is the wireless adapter?  After that, I can be sure you've got all the files and can give you the ndiswrapper instructions with no problem.  Just want to be sure on the chipset.


Are you sure those are the wireless drivers?  AUTORUN.INF is just the file on the CD that tells Windows what to run when the CD is recognized, so it isn't needed.  Netani.inf looks good but not sure on the 2 .sys files.


dave :)

---

### Post by anewguy on 2009-09-27
Okay, after looking at the Linksys support site, I have to assume that the adapter is a WMP54G of some verion (4.1, 4.0, 2 or 1.4).  Versions 4.1 uses the rt61.sys and Rt61.inf files, version 4.0 uses the rt2500.sys and Rt2500.inf files, and finally versions 2 and 1.4 both use the Broadcom drivers bcmwl5.sys and bcmwl5.inf.

If you have the CD that came with the card, look for a folder called "Drivers" on it as it appears that the zipped files that I downloaded from Linksys for each version actually contain the files needed to burn a CD for installation.  See if you have that folder and what is in it and post back.  If you don't have that folder, we can look in device manager in Windows or in the windows directory paths for one of the files to try to determine what you have and need.

If any of the files I mention sound familiar from doing this in the past let me know.  The Broadcom cards are now supported in a B43 restricted driver in Ubuntu, but since you have no net access in Ubuntu (you can't direct connect can you?) I don't believe we can use that, in which case we can use ndiswrapper to install the driver.

Just post back what you find out either about the version, the lspci, or from looking at the installation CD.  That way we can help you get this going fairly easily I think!

Dave :)

EDIT:  Just thought - I'm looking at the Linksys support site for US products -> there is a WMP45G that appears to be a UK or outside the US version.  Is that what you have?  I've seen this model number on google and it seems to from UK posts.  I did go to the Linksys european english site but it's not there under support either.

---

### Post by bedforce on 2009-09-27
Oops, sorry about the confusion.  I do have a WMP54GX (54 not 45) card.  Here's the Linksys website for support/driver download

[http://www.linksysbycisco.com/US/en/support/WMP54GX/download](http://www.linksysbycisco.com/US/en/support/WMP54GX/download)

It says there is only one version (1.0) and that's the driver.  The files in that download also match those in my :C/program files/linksys folder in windows.   I'll reboot now in Ubuntu and give the results of that command.

---

### Post by bedforce on 2009-09-27
Here are the results from the lspci | grep Network command:

mike@computadora:~$ lspci | grep Network 06:01.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)

Which is odd because I don't recognize one word of that lol.  Maybe I should just try to use that ndiswrapper on what I have for the drivers?

---

### Post by anewguy on 2009-09-27
If you haven't already, install ndisgtk - it should be in the same folder, etc., as ndiswrapper is on the LiveCD.  Once you have installed it, open a terminal window and type:

sudo ndisgtk <press enter>

Once it is up, select install new driver and point it to the netani.inf file.  It's been quite a while since I used it, so I really don't remember it, so if you have any questions just post back.

Dave :)

---

### Post by bedforce on 2009-09-27
hmm... So I installed the ndisgtk and ran the *sudo ndisgtk* command, then installed the netani.inf file.  It then gave me a warning: "unable to see if hardware is present" with a big red X :(  

It doesn't seem to know what card I have plugged in to the pci slot.  Let me give you some more backround that may or may not help you to help me.  I had a computer that was a Dell, 4-5 years old, and about a month ago I built a new computer of various high end parts.  I scrapped what I could from the dell, including the wireless pci card, dvd drive and a couple other peripherals.  Now I'm trying to put Ubuntu on this new computer, which I might add has had no problems to date in Windows XP.  Just in case, I'll post the result of the lspci command from the terminal.  Any help at this point would be greatly appreciated once again!  Thanks a lot Dave

---

### Post by bedforce on 2009-09-27
mike@computadora:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:01.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by anewguy on 2009-09-27
Seems a little strange - the system knows the hardware is there (seen in the lspci output), but apparently the driver isn't taking.

Try this in a terminal window:

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter>

Then try ndisgtk again.  You did install ndiswrapper previously like I mentioned in one of my older posts, right?

If that still doesn't work, then try this:

sudo ndiswrapper -l <press enter>

If this returns anything, then do:

sudo ndiswrapper -e xxxxxxxx <press enter> where xxxxxxxx is the driver returned in the ndiswrapper -l previously.  Do this until nothing is returned from the ndiswrapper -l.

change directory to where the driver files are:

cd xxxxxxxx <press enter> where xxxxxxxx is the path to the folder containing the driver files.

sudo ndiswrapper -i netani.inf <press enter>

sudo ndiswrapper -l <press enter> 

This should show the driver installed and the device as active.  If not, post back what it does say or any error messages.

If OK so far:

sudo ndiswrapper -m <press enter>

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter>

Then try your wifi again.  I have seen various reports on this card on the net and in this forum - some suggest the old Broadcom drivers must be blacklisted, still others suggest that the card is difficult at best to get working in Ubuntu and recommend buying a different card.

If you decide to buy a different card, please post back first so we can point you to a site that shows which wifi cards are supported in Ubuntu or can be made to work.

Dave :)

---

### Post by anewguy on 2009-09-27
> **bedforce said:**
> Here are the results from the lspci | grep Network command:

mike@computadora:~$ lspci | grep Network 06:01.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)

Which is odd because I don't recognize one word of that lol.  Maybe I should just try to use that ndiswrapper on what I have for the drivers?


I forgot to answer this earlier - what the lspci is showing you is that the system knows of the hardware for a wireless adapter and that the chipset is Airgo Networks AGN100 rev 03.  This tells us we must get the driver for that chipset and also look for any other posts on the Airgo AGN100 chipset.  This may include posts for adapters other than yours even from other card vendors - it's the chipset that matters.

Dave :)

---

### Post by bedforce on 2009-09-29
So here's some commands and outputs I just put in the terminal:

mike@computadora:~$ sudo depmod -a
mike@computadora:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mike@computadora:~$ 
mike@computadora:~$ sudo ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netani : driver installed
    device (17CB:0001) present
mike@computadora:~$ 
mike@computadora:~$ sudo ndiswrapper -e 17CB:0001
couldn't delete /etc/ndiswrapper/17CB:0001: No such file or directory


I'm not sure what to do from here.  I'd rather not buy a wireless card, especially since the one I have works fine and incompatibility may not be (although probably is) the problem.  So you're saying I need to download a driver for my Airgo AGN100 integrated chipset?  Isn't that integrated in the motherboard?

---

### Post by anewguy on 2009-09-29
First, it would be sudo ndiswrapper -e netani I *think*, not the device id.  Try that and let me know what happens.

I believe the wireless is a separate card, not built in to the motherboard, but either way it doesn't matter - a driver is still needed to use the device, and the device is built with that chipset, so the driver applies to the chipset.  As an example, if you look at the support site for the wmp54g you will see 4 driver versions listed, each for a specific chipset used in that version, even though the model (wmp54g) is the same.  In the case of the wmp54gx I could only find 1 driver, and it does appear you already have those files.

Not sure exactly what is going on - this stuff about a config file and ndiswrapper I haven't seen before - maybe it's new and ndiswrapper is migrating to a different format/syntax.  There are some posts on the net and in this forum if you search either for ubuntu wmp45gx   -or- ubuntu airgo agn100.  You can also substitute Linux for ubuntu in those searches and it will show info on more than just Ubuntu which may be helpful.

Reading some of those may give you an idea I haven't posted, or may help you in determining how much of a hassle you want to go through (there seems to be an issue with speed in Ubuntu with certain releases and these cards).  After reading through those, you'll be in a better position to judge if you want to continue with what you have or if you'd be better off buying another adapter from the supported list.

Whatever you decide, please post back and I'll see if there is more I can do to help you or not.

Dave :)

---

### Post by bedforce on 2009-10-04
Wow I don't know how you guys remember all this stuff... anyway thanks Dave; I followed your last instructions and they worked!  I'm on Jaunty Jackalope now :)  I used:

sudo ndiswrapper -r netani.inf

to remove the driver that failed, copied the file that contained the driver *.inf file and the *.sys files and all that to my home folder, then did: 

cd /mike/home/Linksys/Driver

to get to that folder, and installed the driver with: 

sudo ndiswrapper -i netani.inf

and it worked!  It could have been that I was trying to load the driver directly from my USB flash drive.  Many thanks again for your help!

Mike :)

---

### Post by anewguy on 2009-10-06
Glad it worked - but did it keep working after boot?

Normally you have to do:

sudo ndiswrapper -m

sudo depmod -a

sudo modprobe ndiswrapper

just to get the ndiswrapper kernel module loaded to test.  The ndiswrapper -m is supposed to be sure that happens at boot also, but it seems that most of the time you have to add ndiswrapper to the end of the /etc/modules file.

Let me know it's still working for you.

BTW - someone helped me out, that's how I learned.  We all do the "play it forward" kind of thing here - learn from someone, then try to help someone else.  Hopefully you know enough now you might be able to help someone else with a similar problem - it can't hurt to try.

dave :)

---

### Post by bedforce on 2009-10-11
I didn't use any ndiswrapper -m, depmod -a or modprobe; I only did what I said in an earlier post.  It's been working fine since I got it running that first time, so I figure I'll let well enough be.  I'll be sure to "play if forward" if I see someone has a similar problem, and many thanks again!

Mike :)

---

