---
title: "Realtek 8139 driver installation and internet for Ubuntu 7.04"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by axavierraj on 2007-09-18
Dear Friends

I am newbie to Linux and Ubuntu.

I have a system with Windows XP SP2 in one of my hardrive (40 GB * 3 partitions) and Ubuntu 7.04(Live CD from Canonical) in another harddrive (8 GB).

I have two ports for Internet,

One is onboard VIA Rhine and it got repaired when one lightning occurs and i added another network card using PCI slot which is
Realtek 8139.

I found no difficulties in Windows for installing the driver for this network card. But i found difficulties in Ubuntu to install the driver for it.

Later i searched this post from web ( [http://ubuntuforums.org/showthread.php?p=3385014](http://ubuntuforums.org/showthread.php?p=3385014) ) and followed the steps to compile the source given in the URL [http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/) by chili555.

I installed the module and configured the IP address and DNS address, Gateway etc., for that 'eth1' 'Wired Connection'.

But my browser in Ubuntu has no access to web and i don't know why.

Can anyone give solution for my problem? If i need to post with any details kindly tell me the steps how to extract those details and from where to find those details (Since i am a newbie for Ubuntu)

Looking forward for helping hand.

With regards

Xavier Raj Antony Samy.

---

### Post by trooper666 on 2007-09-18
you don't need a special driver, the driver is built into the kernel check these threads for the most possible solution:

[http://ubuntuforums.org/showthread.php?t=545149](http://ubuntuforums.org/showthread.php?t=545149)

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by axavierraj on 2007-09-19
> **trooper666 said:**
> you don't need a special driver, the driver is built into the kernel check these threads for the most possible solution:

[http://ubuntuforums.org/showthread.php?t=545149](http://ubuntuforums.org/showthread.php?t=545149)

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)


Thanks trooper666!

But where to find the network driver in kernel and how to configure to my static IP given by my ISP, to start the internet via Ubuntu.

I tried to install the driver from the CD given by Realtek for general linux package and resulted in error while 'make' and later when i tried using the package given in the URL [http://gurukumara.googlepages.com/](http://gurukumara.googlepages.com/) i compiled and installed the driver, everything fine. but the internet is not working. Also when i tried to run the command lshw from terminal the system hang up and no response.

Pls tell me the steps how to find which are all the drivers were installed for network and Is they are working or not? etc.,

Regards

Xavier

---

