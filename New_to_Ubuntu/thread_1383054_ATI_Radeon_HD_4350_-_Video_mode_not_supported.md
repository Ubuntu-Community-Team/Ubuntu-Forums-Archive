---
title: "ATI Radeon HD 4350 - Video mode not supported"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by MichaelKalman on 2010-01-16
I have a ATI Radeon HD 4350 which worked great with Vista. I have got Ubuntu yesterday and am loving it! It's so perfect! The only problem I have is I went to System>Admin>Hardware Drivers ... installed the recommended driver and when I restarted my PC, my monitor showed me the error Video Mode Not Supported, I was lucky enough to use my Moms monitor which worked, so I uninstalled the driver I installed ... After that my monitor worked again. I'm wondering. For games . . . if I dont install the driver will my games still use the video card and will I get the GFX of the video card without installing the drivers, if not, please let me know which drivers I should install, where I can get them, how I can install them. Thanks, all help appreciated.

---

### Post by MarkC502 on 2010-01-16
You could install and run envyng to let you easily download and install a recent ATI graphics driver.

Here is the command to install envyng, just run this in a terminal.

sudo apt-get install envyng-core

Here is the command to run it once you get it installed.

sudo envyng -t

This will open the program with a simple interface with simple choices, just select the choice that says install ATI driver and then it will do everything for you and once its done reboot your PC and report back.

P.S. Once you reboot you should right click on your desktop and go to Change desktop background and then the visual effects tab and select "Extra" if you want 3D type desktop graphics support ( Needed for Compiz 3D cube Etc )

---

### Post by MichaelKalman on 2010-01-16
Did what you said, screwed my PC over. Now my resolution is screwed and I cant change it back from System>Pref>Display .. How do I uninstall Envyng ... Is there another solution?

---

### Post by MichaelKalman on 2010-01-16
May I mention it is stuck at 800x600 or the one below ... 640x480. HELP ME! The resolution is annoying. I just uninstalled Envyng. It's still not fixed.

---

### Post by MarkC502 on 2010-01-16
Ill try to help all I can, first though I didn't see what version Ubuntu you are using as that would help. Also before you uninstall envyng did you uninstall the driver it installed? If not I would reinstall it then run it and choose "Uninstall ATI driver" to undo what it did earlier.

I did some googling on your exact card and found the following links

[https://answers.launchpad.net/ubuntu/+question/75218](https://answers.launchpad.net/ubuntu/+question/75218)

In which I found that apparently the problem is that there are no open source radeon HD drivers available yet. Your only option appears to be to download the installer directly from ATI and install it yourself. I only own Nvidia graphics cards but they distribute linux drivers via the same type of .run script file and I can outline generally what the steps are to install it but this does require command line usage to accomplish.

FOR NVIDIA .RUN PACKAGE INSTALL ( Should be very similar to ATI & Probably will work to install ATI )

1. I download the .run file from Nvidia for 64bit linux ( you would download the 32 or 64 bit version of ATI driver depending on what you are running ) 

2. I put the run file in my home directory.

3. I press Ctrl+Alt+F1 to go to another text only login , and I login with my user name and pass.

4. I am now at a command line and I need to stop the Xserver to stop the graphics environment that is running in the background with the following command.

IF UBUNTU 9.04
sudo /etc/init.d/gdm stop

IF UBUNTU 9.10
sudo service gdm stop

5. Now you are still at the command line and you should be in your home directory already ( type dir and hit enter to list the contents of the directory ) so you should just have to run the command to install the ATI driver package and it should do the rest.

Command would be as follows

sudo sh name-of-file-you-downloaded.run

This would launch the installer and once its done you should only have to reboot to be using the new driver.

Command to reboot

sudo shutdown -r now

Hope that works......

---

### Post by 3rdalbum on 2010-01-16
> **MarkC502 said:**
> I only own Nvidia graphics cards but they distribute linux drivers via the same type of .run script file and I can outline generally what the steps are to install it but this does require command line usage to accomplish.

-1. The procedure to install ATI drivers is totally different to Nvidia drivers.

Your second-best solution would be to install the ATI driver again from the Hardware Drivers program, and edit the /etc/X11/xorg.conf file to reflect your monitor's native resolution and refresh rate. No idea why ATI's driver won't do this (I haven't used ATI drivers for years) but it's a known problem.

Your best solution is to install an Nvidia graphics card. ATI is really pretty bad on Linux.

---

### Post by MarkC502 on 2010-01-17
I just saw someone elsewhere that stated that to use ATI's propriatary driver you had to use 8.04 and then install their driver as it does not work with newer Ubuntu but you will need to research that.

---

### Post by admiralspark on 2010-01-17
ATI basically has no decent support for their graphics cards in Linux (which they should, since they produce the most cost-effective gfx chips, but I digress).
On the kernel version that 9.10 is based on, there is NO support for the ATI HD graphics cards. The newest kernel update (which will be part of 10.4 Lucid Lynx) has more support for ATI cards, but may still have problems. Like mentioned before, there are plenty of nVidia cards that are cheap (read: eBay but not from HongKong), your best bet for 3D is with those. 

I own an ATI Radeon XPress 200M, I've used the newest Knoppix distro and had great success with 3D (and compiz, yay!). Unfortunately for Ubuntu/ATI users, we have to wait a few more months.

---

### Post by braddcadd on 2011-03-30
Has this story change in the last year?  I have a homemade computer with ATI HD 4350 and the screen keeps freezing.  I suspect the graphics card.  The user does not need any fancy 3D stuff or openGL, just wants to try Ubuntu.

Any help is welcome.  I fixed this problem many years ago by editing xorg.conf.

---

### Post by Mark Phelps on 2011-03-30
> **braddcadd said:**
> Has this story change in the last year?  I have a homemade computer with ATI HD 4350 and the screen keeps freezing.  I suspect the graphics card.  The user does not need any fancy 3D stuff or openGL, just wants to try Ubuntu.

Any help is welcome.  I fixed this problem many years ago by editing xorg.conf.

I don't know about the 4350 specifically, but I recently upgraded my desktop PC to a 4290 -- and both the default open-source drivers and the fglrx drivers work great. No problems of any kind.

Suspect the 4350 problems might have been with that specific card.

---

### Post by mastablasta on 2011-03-30
if it's freezing it can be from a number of reasons. including overheating of CPU. overheating of graphics card, leaking capacitors on motherboard, graphics card....
 
and yes with latest ubuntu 4xxx and 5xxx cards should work especially after ATI drivers are installed.

---

### Post by braddcadd on 2011-04-01
I monitored the temps with a cron job of "sensors | textfile" each minute.  No changes there.  I think the hardware is good since it ran fine with window$ last week.

I changed the driver (or at least I think I did) by editing xorg.conf.  I change it from "fglrx" to "radeon".  It hasn't crashed since then.  Think this could have fixed the problem?

---

### Post by Blackoulis on 2011-04-13
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by alphacrucis2 on 2011-04-14
> **Blackoulis said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

+1.

Download Catalyst 11.3 direct from AMD. Install using the buildpkg method. Make sure you choose the right one (32 or 64 bit)

Step 1. Make sure fglrx is purged. sudo apt-get --purge remove fglrx*
Step 2. Run the amd catalyst installer with the buildpkg parameter to create the required deb files.
Step 3. Install the deb files via dpkg -i
Step 4. sudo aticonfig --initial -f
Step 5. Reboot

For more information read this howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by thelusiv on 2011-05-24
I'm having the same problem with this card in Ubuntu 11.04. I have tried installing the driver through the additional hardware drivers interface as well as via the buildpkg method with the latest version of the driver from ATI. Either way, I get a blank screen when X initializes. I have tried disabling TLS, as well as turning off ACPI services. Does anyone have any ideas on how to fix this? The card is in a Dell Optiplex 960.

---

### Post by coffeecat on 2011-05-24
> **thelusiv said:**
> I'm having the same problem with this card in Ubuntu 11.04. I have tried installing the driver through the additional hardware drivers interface as well as via the buildpkg method with the latest version of the driver from ATI. Either way, I get a blank screen when X initializes. I have tried disabling TLS, as well as turning off ACPI services. Does anyone have any ideas on how to fix this? The card is in a Dell Optiplex 960.

I have a  Radeon HD 4350 card in a home-built machine. It has worked just fine with the default open source driver in Lucid, Maverick and Natty - 3d and compiz included. I tried the fglrx driver from Additional Drivers in Natty. It installed OK and worked OK. I could see no difference in ordinary day-to-day work between the opens source driver and the fglrx. Or, perhaps, moving windows was a little bit stuttery with the fglrx driver so I reverted to the open source one. 

The fact that you are getting a blank screen when X starts suggests you are looking along the right lines at things like ACPI. I'm sorry I can't be of much help, but there is some outdated information in this thread and I wanted to make clear that the Radeon HD4350 can work in Ubuntu with both the FOSS and proprietary drivers. There must be some other issue with your specific hardware that is causing the problem.

The early posts in this thread are from January 2010 are now quite dated in their information. The then current open source ati driver in both Jaunty and Karmic could drive this card, but without 3d acceleration. Things are much better now.

---

