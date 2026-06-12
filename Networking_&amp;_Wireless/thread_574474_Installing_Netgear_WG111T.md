---
title: "Installing Netgear WG111T"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by wirelessnoob on 2007-10-12
I'm currently trying to setup my external wireless card, a Netgear WG111T in a live CD version of Ubuntu Linux for AMD64. However, after I install Ndiswrapper and follow the instructions given in the help section for wireless cards and Ndiswrapper, the wireless card still does not appear in the Network connections. Can anyone help me with this? I'd greatly appreciate it. :)

---

### Post by wildwil on 2007-10-14
Hi,

I'm also having trouble getting my USB Wireless dongle working.

I have been reading and trying various approaches using the **ndiswrapper**. There is even a website supporting it and is available here: [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

I've downloaded ndiswrapper v 1.48 and tried, in vain I might add, to get it installed properly. But have failed and sayy it needs the dependencies.

I am totally new to Linux/Ubuntu, but I can already see why Microsoft has such a BIG market share. They don't ASK customers to off and do a load of detective work and then compile stuff and the such like.

My aim is to have my daughter's PC up and running on Ubuntu and free/cheap software and to spread the word (Ubuntu) upon my sucess.

 We're have to keep trying I suppose. ;)

---

### Post by wirelessnoob on 2007-10-14
Actually, I think it's mostly because the wireless card drivers do not support Linux that we have to go to a lot of trouble to get them working, and not because of Linux itself. (I may be wrong though.)

Anyway, _[this post]("http://ubuntuforums.org/showthread.php?p=3457392")_ claims that Ubuntu 7.10 (Gutsy Gibbon) will support the WG111T dongle. Can anyone else verify this?

---

### Post by kevdog on 2007-10-14
Im not sure if it does or not, but am tired of people whining in these forums without doing a little research.  Ubuntu or linux isnt windows -- it actually requires some thinking.  As far as the driver's -- most manufactures dont supply linux drivers so hence the often time tedious instructions for installing drivers in linux.

---

### Post by wirelessnoob on 2007-10-20
OK, so I have been able to set up my wireless card in Ubuntu 7.10! :) Here's a short explanation:

Setting Up Netgear WG111T in Ubuntu 7.10 (Gutsy Gibbon)

1. Start up Ubuntu. Then plug in your USB drive, or whatever has the drivers.
2. Install ndiswrapper common and utils, and then install ndisgtk.
3. Copy the drivers from the drivers for WG111T (version 1.2) and paste them to the desktop.
4. Go to System -> Applications -> Windows Wireless Drivers.
5. Install athfmwdl.inf and netwg11t.inf.
6. Plug in the wireless card. (Unplug first if necessary.)
7. Go to System -> Applications -> Network and find the wireless connections. Connect to the network, and it should work! (If you use network security, you may have to go through some extra steps to set it up.)

However, I'm now facing a problem with installing Ubuntu 7.10 to my hard drive. I want to dual-boot Windows Vista and Ubuntu 7.10, but when I get to the partitioning portion of the installation, I only have two options instead of three. (The three can be seen _[here](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)_.) I have "Guided - use entire disk" and "Manual", but not the other one. I don't want to erase Windows, so I don't think I should use "Guided - use entire disk", and I don't know how to set up the partitioning using "Manual". Can anyone help?

EDIT: By the way, I'm running Windows Vista, if that might have anything to do with it.

---

### Post by bgeh on 2007-10-21
i've tried it, doesnt work, the driver installs fine and the hardware is detected, but the wireless network configuration never appears in network manager

any ideas?

---

### Post by newbiekw on 2007-10-23
> **wirelessnoob said:**
> OK, so I have been able to set up my wireless card in Ubuntu 7.10! :) Here's a short explanation:

Setting Up Netgear WG111T in Ubuntu 7.10 (Gutsy Gibbon)

1. Start up Ubuntu. Then plug in your USB drive, or whatever has the drivers.
2. Install ndiswrapper common and utils, and then install ndisgtk.
3. Copy the drivers from the drivers for WG111T (version 1.2) and paste them to the desktop.
4. Go to System -> Applications -> Windows Wireless Drivers.
5. Install athfmwdl.inf and netwg11t.inf.
6. Plug in the wireless card. (Unplug first if necessary.)
7. Go to System -> Applications -> Network and find the wireless connections. Connect to the network, and it should work! (If you use network security, you may have to go through some extra steps to set it up.)

However, I'm now facing a problem with installing Ubuntu 7.10 to my hard drive. I want to dual-boot Windows Vista and Ubuntu 7.10, but when I get to the partitioning portion of the installation, I only have two options instead of three. (The three can be seen _[here](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)_.) I have "Guided - use entire disk" and "Manual", but not the other one. I don't want to erase Windows, so I don't think I should use "Guided - use entire disk", and I don't know how to set up the partitioning using "Manual". Can anyone help?

EDIT: By the way, I'm running Windows Vista, if that might have anything to do with it.

Hi..i had no problems in dual boot, my laptop working well with my window xp and ubuntu 7.10.  I suggested you to use manual method instead of using entire disk. i've no sure what will happen if you selected it, here is the link you can refer to:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

make sure you read it and understand before you get your partition works.  I prefer the ubuntu installation taking place in text base instead of GUI. Dude, hope it helps. 

But i am having problems in getting my netgear usb wifi adapter exactly same model with yours - WG111T working.  I need some guide from you too, would you mind to list out more detail regarding the 7 steps you had mentioned above? like those command how to get it works? 

thanks and cheers!

---

### Post by wirelessnoob on 2007-10-27
OK, here are some more detailed instructions:

Go to the following three sites:
_[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)_
_[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)_
_[http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk)_

Download, from each of them, the version that corresponds to your computer (amd64, i386, etc.), and save these files to a USB drive or something similar.

Also, download the WG111T's wireless drivers from here: _[http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp)_ and place them on your USB as well.

Then boot up Ubuntu 7.10. Plug in your USB drive and install the three .deb files for ndiswrapper and ndisgtk. (You'll need to install ndiswrapper-common, then ndiswrapper-utils, and finally ndisgtk.) You should be able to install them by simply double-clicking on them.

Get the wireless drivers from the USB, and place them on the desktop. (You will need every file in the wireless driver folder, except for the files from the folders "ndis5" and "Utility.") Go to System -> Administration -> Windows Wireless Drivers. Install the files "athfmwdl.inf" and "netwg11t.inf" (which should be placed on your desktop) from there. Close Windows Wireless Drivers, and plug in your wireless card. (You may need to unplug it first.) You should see the blue light flashing.

Go to System -> Administration -> Network, and change the properties of the wireless connection to those of your router. If you use WPA encryption, you will need to either find a way to install WPA Supplicant or something similar, or change your security settings to WEP or no security.


By the way, I managed to install Ubuntu by creating a partition for it in Windows Vista, and using the option "Guided - use largest continuous free space" when installing.

---

### Post by keepertoad on 2007-10-31
My Netgear wg111t is up and running fine in 7.10 using ndiswrapper.  Couple of things to remember.

   1.  If hardware is NOT present, you probably have the wrong driver.  I used the one off the windows install CD.

   2.  ndisgtk apparently does not write an alias to /etc/modules.  To get the interface to start on boot I did the following:   sudo gedit /etc/modules   Then add the following and save:  alias ndiswrapper

wlan0 then appears in System > Administration > network

Check configuration and watch Network Manager connect.

Cheers

---

### Post by jwwws on 2007-11-02
> **wirelessnoob said:**
> OK, here are some more detailed instructions:

Go to the following three sites:
_[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)_
_[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)_
_[http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk)_

Download, from each of them, the version that corresponds to your computer (amd64, i386, etc.), and save these files to a USB drive or something similar.

Also, download the WG111T's wireless drivers from here: _[http://kbserver.netgear.com/release_notes/d102626.asp](http://kbserver.netgear.com/release_notes/d102626.asp)_ and place them on your USB as well.

Then boot up Ubuntu 7.10. Plug in your USB drive and install the three .deb files for ndiswrapper and ndisgtk. (You'll need to install ndiswrapper-common, then ndiswrapper-utils, and finally ndisgtk.) You should be able to install them by simply double-clicking on them.

Get the wireless drivers from the USB, and place them on the desktop. (You will need every file in the wireless driver folder, except for the files from the folders "ndis5" and "Utility.") Go to System -> Administration -> Windows Wireless Drivers. Install the files "athfmwdl.inf" and "netwg11t.inf" (which should be placed on your desktop) from there. Close Windows Wireless Drivers, and plug in your wireless card. (You may need to unplug it first.) You should see the blue light flashing.

Go to System -> Administration -> Network, and change the properties of the wireless connection to those of your router. If you use WPA encryption, you will need to either find a way to install WPA Supplicant or something similar, or change your security settings to WEP or no security.


By the way, I managed to install Ubuntu by creating a partition for it in Windows Vista, and using the option "Guided - use largest continuous free space" when installing.

The above guide worked for me perfectly!  I used another computer to download the various files to an SD card (by the way, unzip the Netgear files and transfer those).  Placed the SD card on my desktop computer and everything worked great!  Thanks wirelessnoob!

---

### Post by jwwws on 2007-12-05
I'm still having problems after I reboot.  If I follow what wirelessnoob says, it works.  Until I reboot that is.

Rebooting puts me back to square one and the only work-around I have found is to go to System>Administration>Windows Wireless Devices and Uninstall Autorun.inf from the list of drivers and then immediately reinstall.

How do I get the system to just recognize and use the wireless device at startup?

---

### Post by hurrikam on 2007-12-13
Hi, I installed Ubuntu 7.10 x64 on an AMD64 dual core. I read all the posts related to how make a WG111T USB wireless adapter working on that system.

Trying all the possible way described around, it works to me except that the led in the adapter doesn't flash at end of all the installation steps and that no voices for wireless connections appear in the Admin->Network window.

My steps were these:

* I installed the three packages for the NDIS (I tried both installing the one already included in the ubuntu distro or taking them by the suggested web links).
* Under the new configuration page added in the programs menu by the NDIS package, I first installed 'athfmwdl.inf' taking it from the web link to the version 1.2 of the drivers, and then I installed 'netwg11t.inf' but taking it from the original drivers CD (I think v1.3). The version of the same file contained in the downloaded drivers package was not recognized.
* At that point both the two files were marked to be recognized in the current configuration page.
* I also checked the /etc/modules file to make sure the 'alias ndiswrapper' line was added.

After trying different combinations of plugging/unpluggin the pen at different times during the installation process, or rebooting the system, neither the adapter's led was flashing or any voice for wireless network was added under the network configuration page.

Please let me know if you would like to have more details about, any suggestion or just if you encountered problems like these.

Thanks.

---

### Post by mc6415 on 2008-01-04
OK I folowed everything from the first post exactly, the only problem came as it says athfmwdl.inf: device present but it says that wg11t.inf device is not presen, how do I fix this, this is the one thing stopping me from moveing over to linux full-time is that I dont have access to the internet on it yet.

---

### Post by frootloop on 2008-04-22
I have the same problem, with athfmwdl.inf: device present but wg11t.inf device is not present - anyone have any ideas?

---

### Post by frootloop on 2008-04-23
I upgraded to 2.1 of the windows drivers, that solved it! after reboot It stopped working again, but follow the setps here to solve it: 9I donr have the URL unfrtunately, I saved the pages a while back )

Step 1


Unplug USB Adapter.
Step 2

Put the Install CD back into drive and fire up synaptic package manager.
Step 3

Install ndisgtk package. (If you did not install from cd, then transfer the .deb files from packages.ubuntu.com (dependencies as well) and install.)
Step 4

Go to System -> Windows Wireless Drivers.
Step 5

Put in the WG111T Windows Install CD. Hit the Install Driver button.. Go to the CD, go into the ndis5 folder and install the netwg111t.inf file.

If you no longer have the CD then you can grab the drivers from the netgear website..
Step 6

Plug back in USB Drive.. And network-manager should do the rest..

For me WEP and WPA was working out of the box.
Step 7

Okay, when you restart you will be hit with a little issue.. The Stick now doesn't work..

The short term fix is to run..

Unplug Adapter..

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

Plug in adapter..

I am working on a better solution for this though.. :)

Thanks, Alex Latchford.

last edited 2008-03-21 17:53:45 by AlexLatchford

---

