---
title: "Need help with U.S. Robotics wireless usb adapter"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by koo-koo on 2006-10-27
I'm having problems getting my wireless internet to work.  I've tried both Ubuntu 6.06 and Kubuntu 6.10 with roughly the same results.  I use ndiswrapper 1.18 and according to the 'list' on it's wiki, my US Robotics 5422 wireless usb adapter is supported.  Here are the steps I've managed to take so far:

*Install ndiswrapper
*unzip driver for usb adapter (listed in ndis' wiki)
*install the driver (ndiswrapper -i rsc4usb.inf)
*associate with device (ndiswrapper -d 0baf:0118 rsc4usb)
*check if the driver's listed (says "driver present, hardware present")
*use 'depmod' with no error (depmod -a)
*use 'modprobe' with no error (modprobe ndiswrapper)
*use 'iwconfig' which shows "eth0" (ubuntu) or "eth1" (kubuntu)
*use 'iwconfig eth1 essid ESSID' (is "ESSID" my access point's name?)
*use 'iwlist eth1 scan' (says that nothing's available)

This is as far as I get before getting lost or confused.  The light on my adapter never blinks or goes off while plugged in, so I think that may be part of the problem, as if the radio is not working.  Also, I currently do not have security enabled, so I shouldn't have to worry about setting a key.  If ndiswrapper must have security enabled to work, then I prefer WEP since WPA messed up my signal once until I had to do a hard reset on the router.  I also find WEP easier.

I do not have an ethernet port on my computer, so directly connecting from the modem (located in another room) to the system is out of the question.  My system is a Dell Dimension 8100 and has a P4 1.3Ghz, 384 MB rdram, GeForce4, 20GB linux HD and a separate 40GB windows HD, 2 cd-rw drives (1 also can read dvd's), 5 pci slots, and 4 usb ports.

**Noting what I listed above in the steps taken, what do I have to do before my wireless adapter will work? ** 

P.S.  It'll be difficult to print any 'dmesg' info or other log/error reports since I dualboot on this system and for some odd reason, the floppy drive does not work in Kubuntu 6.10.  If I have to reinstall Ubuntu 6.06 to restore the floppy, it'll be a bit longer before I can check this thread, but I'd also be able to copy any needed system log info.

---

### Post by koo-koo on 2006-10-28
Just an update on a few things:

*My floppy drive works now.  I did add 'fd0' somewhere near the end of the fstab file where it was only '/dev/', but I guess I had to restart before it took effect.  Now I'll be able to record certain system log info if needed (though I only know of the *dmesg* command at this time).

*Looking in the ndiswrapper FAQ, it said to use *iwconfig eth1 ndis_reset* to reset the device.  However, the terminal says that ndis_reset is some kind of unexpected command/argument.  It's the same with *iwpriv eth1 ndis_reset*.

*I transferred NetworkManager to Kubuntu 6.10 through the floppy, so if I can get that to compile, I may try it in addition to iwconfig, iw****, and wpa_supplicant (which I currently have no idea how to operate).

*If either WEP or WPA-PSK is needed, I'll set up a password for my Access Point in another few hours.  I suppose the "Promiscuous Mode" that the ndiswrapper FAQ refers to is an Access Point that needs no password to be connected to.

--EDITS
*I'm much closer now.  By setting some mode or other to 'Managed' (it's in ndiswrapper's FAQ), my MAC address showed up and in KDE's wifi tool, my network name appeared with a 5-star signal strength.  However, when attempting to connect, it fails to.  Also, the light on the USB adapter still fails to blink, though this may be less of an issue.

*I copied HTML files of the ndiswrapper FAQ, install, and uninstall pages.  Unfortunately, my floppy seems to have some bad sectors and my USB flash drive can't be read, so I'll try a different floppy.

---

### Post by koo-koo on 2006-10-29
I've found a solution.  According to ndiswrapper's list of supported devices, my device was tested under ubuntu 5.10 with the 2.6.12 kernel.  So I installed ubuntu 5.10, using both the driver given in the list and the version of ndiswrapper included within the installation.

The light on the device blinks, and I only needed to load the ndiswrapper module.  From there, going to System>Administration>Networking takes care of the rest as far as activating the interface and connecting to an access point.  I'll see if updating from 5.10 to 6.10 either breaks the system (meaning that for now, stick with 5.10), or keeps it working (meaning 5.10 has to be installed as the base).

---

### Post by koo-koo on 2006-11-04
I wonder why no one has responded to my posts, unless there isn't anyone who knows what to do...

Anyway, here's what I've found out over the past week (if anybody cares):

*As of now, Ubuntu 5.10 is the only version I've tested that works.  Upgrading to 6.06 from 5.10 breaks my wireless connectivity somehow.  Installing 6.06 as base breaks connectivity.  I suspect it's something to do with the kernel version and if so, I wonder if it's possible to use the 5.10 kernel within 6.06 after the upgrade?

*Freespire 1.0 allows me to use wireless, even on the live cd (I have 2 cd drives to set up my wireless driver & ndiswrapper).  However, eventually it freezes the system while on the internet.  When I installed it, my system still locked up, and on subsequent restarts, my internet connectivity was broken.

*I haven't installed Ubuntu 6.10 yet, only Kubuntu 6.10.  I don't know if there's enough under-the-hood differences between the two to justify getting the Ubuntu 6.10 ISO image and burning it to a CD to try it.

---

### Post by ftomika on 2006-11-08
Hi Koo-Koo!

I have the same card (and same problem:) that you have. I use Kubuntu 6.06, and I tried everything, but my card isn't working:( I'm sad that it works only with an older version. Maybe I download it, and use that one, but I don't really like this idea.
Can anybody request us something?

---

### Post by koo-koo on 2006-11-26
An issue that I just discovered today is that using Ubuntu 5.10, if you install 'NetworkManager' in Synaptic Package Manager, it will also install 'bind9' and 'dhcbdb'.  When I installed NetworkManager, my internet connection immediately died and the light on my USB adapter stayed on just like in 6.06 and 6.10.

I had to uninstall all three packages and restart before I got my internet connectivity back working again.  Maybe versions later than 5.10 have something to do with these three packages although when I checked the Live CDs, none of them were installed.

---

### Post by poets1977 on 2006-12-23
Look [here]("http://ubuntuforums.org/showthread.php?t=227291&highlight=805422") .
Bye

---

### Post by koo-koo on 2006-12-25
Thanks for the link.  With those instructions, I've gotten the adapter to work in Ubuntu 6.10, although for some reason, the device is still listed as eth0.  Also, something seems to be eating away at my CPU since it spends several minutes at a time in the 95%-100% range and the HDD light on my system constantly flashes when this happens.

---

### Post by poets1977 on 2007-03-29
Hi koo-koo try to download the latest drivers from the usr website or from [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#U").

Rename the .exe to .zip, extract all the files and rename all of them to lower-case.

After that you have to unload your actual rsc4usb.inf driver from ndiswrapper and load the new rsc4usb.inf.

My problem with the old driver was veeeeryyy big: total pc freeze with only one solution...reboot. ](*,)

Hope this will help you too.

---

