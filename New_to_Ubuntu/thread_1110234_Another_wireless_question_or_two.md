---
title: "Another wireless question or two"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by WoollyW on 2009-03-29
I've got a Sony Vaio VGN-NR10/E/S running with Ubuntu 8.10. Loving the look and feel and how it works... but I have wireless issues....

Internal card (Atheros 802.11) appeared dead before the change (a common problem with this model I'm told) but have nonetheless installed drivers for it.

Also have Conceptronic Express Lan card (C300EXC/, drivers also installed. My USB adapter is a Konig variety (CMP-WNUSB20) but have lost the disc with the drivers so no installation. All drivers installed from System/Administration/Windows Wireless Drivers.

The Konig adapter is the only one that comes close to working - views but doesn't connect, otherwise others appear dead. Have tried running the 'sudo dhclient' in an effort to manually configure but got the same response with all 3 - 'no working leases in persistent databse - sleeping'. No luck with pinging from Network Tools.

Sorry for another wireless question! Before joining & posting I did read *a lot* but can't work out what I need to do next... surely one of my adapaters should work ;) Any advice out there?

Cheers

---

### Post by lkraemer on 2009-03-29
Google search for "HOWTO: & AR242x"

You will find a good howto guide for the driver install.

Post the output of:
```

lshw -C network 
ndiswrapper -l

```
ndiswrapper probably isn't loaded, so you can ignore the error.

[http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG)

You may have to do:
sudo gedit /etc/modprobe.d/blacklist

#blacklist the Hardware Drivers (Restricted)
blacklist ath_hal
blacklist ath_pci

Be aware you WILL have to follow the instructions for a rebuild when
a Kernel update comes along.  No problem though, just boot a previous
version to be up and running from the grub menu.

lkraemer

---

### Post by WoollyW on 2009-03-31
Brilliant! Followed your advice and Googled - followed the steps for installing the drivers and now my internal card is working for the first time in ages! Honestly though that was dead, Sony weren't much help there.

Is it a good idea to still blacklist the other drivers?

And by rebuild, do you mean go through all the steps I've just done? If so that's not a problem - will make a written note of all the steps so I can do it if I can't get online.

Thanks so much for your help :)

---

### Post by lkraemer on 2009-03-31
Well, if it is working I wouldn't blacklist the drivers.

That previous link states:

Installing again after a kernel upgrade
------------------------------------------------------------------------
If your kernel is upgraded, you'll have to install again. The following code will install the compile and install the new driver (kernel module):
```
 
cd ~/madwifi-*
sudo make clean
make
sudo make install
sudo modprobe ath_pci


```
So, when Ubuntu pushes a Kernel update, your wifi will not work.
Just open a Terminal window and to the steps noted above and your Wifi
should be back fully functional......assuming that you have the proper
subdirectories to do the make & make install.

I always make a doc file on what to do so I don't have to be "ONLINE"
to read how to re-work my steps.  (If you need to get online just select
a previous Kernel from the grub boot menu and get your information, then
reboot to the latest kernel and follow your printed instructions.)

lkraemer

---

