---
title: "Just Updated; No networking"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by abeisgreat on 2009-01-30
I just updated, everything was working dandy, said I needed to restart, so I did. I turn on my machine and it says "you are now disconnected from the network" or something close, so I plugged in my hardwire, still nothing, it sits at the 2 green balls, and never goes any farther.

My wifi card is a Atheros so I had to do some weird config stuff to get it running, I suspect that some setting got reset, any ideas? anyone got similar issues?

Edit:
I just ran lspci | grep Atheros and got
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Edit:
Hmm when I right click on the network ( in the notification area ) I only have an option for hardwired network and as I said even that does not work.

FIXED:
Its something with 2.6.27-11, I booted into -9 and it worked swell, who knows, but Im happy in -9
I dont think this is a driver issue, I think its a config issue, but Im not sure what got messed up

Thanks,Abe

---

### Post by cmnorton on 2009-01-30
updated or upgraded? Did you upgrade from one Ubuntu version to another?

What's the content of /etc/network/interfaces ?

---

### Post by abeisgreat on 2009-01-30
> **cmnorton said:**
> updated or upgraded? Did you upgrade from one Ubuntu version to another?

What's the content of /etc/network/interfaces ?

Updated, and as I said I've fixed it by booting to an older kernel, 

But yea Ill post it anyway

auto lo
iface lo inet loopback

---

### Post by avtolle on 2009-01-30
I suspect the OP manually installed the driver for the Atheros card; the same will need to be done with the kernel update. 
Take a look at the following link: [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) for yet another way to get an Atheros wifi card working. I used this method last week to get mine up and going.

---

### Post by DougieFresh4U on 2009-01-30
> **abeisgreat said:**
> I just updated, everything was working dandy, said I needed to restart, so I did. I turn on my machine and it says "you are now disconnected from the network" or something close, so I plugged in my hardwire, still nothing, it sits at the 2 green balls, and never goes any farther.

My wifi card is a Atheros so I had to do some weird config stuff to get it running, I suspect that some setting got reset, any ideas? anyone got similar issues?

Edit:
I just ran lspci | grep Atheros and got
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Edit:
Hmm when I right click on the network ( in the notification area ) I only have an option for hardwired network and as I said even that does not work.

FIXED:
Its something with 2.6.27-11, I booted into -9 and it worked swell, who knows, but Im happy in -9
I dont think this is a driver issue, I think its a config issue, but Im not sure what got messed up

Thanks,Abe

Today was showing 7 update for my Intrepid install
```
[B]The following packages will be upgraded:
  foomatic-filters linux-doc-2.6.27 linux-headers-2.6.27-11 linux-headers-2.6.27-11-generic
  linux-image-2.6.27-11-generic linux-libc-dev linux-source-2.6.27
[/B]
```

Wondering which one caused the network issue. I didn't go through with update yet, until I check it all out.

---

### Post by avtolle on 2009-01-30
How did you install the driver for the wifi card? If manually, you will need to do it the same way once the kernel update is installed.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) gives yet another way to get an Atheros wi-fi card going with the latest linux drivers. It works well. I've also used the method outlined in the release notes to 8.10 involving installing the backport module; have installed the XP driver with ndiswrapper; and have used the madwifi driver method.

---

### Post by abeisgreat on 2009-01-30
But it wasnt just wifi, I couldnt get an IP through hardwired either.

---

### Post by avtolle on 2009-01-30
Missed that part. I will try to give that some thought. Have you searched the forum for anyone having similar problems?

---

### Post by abeisgreat on 2009-01-30
I did, and as I said, the only solution I found was to use an older kernel version

---

### Post by cmnorton on 2009-01-30
> **abeisgreat said:**
> Updated, and as I said I've fixed it by booting to an older kernel, 

But yea Ill post it anyway

auto lo
iface lo inet loopback

This sounds like it could be a bug. I'd ask a question, look for a similar bug, or post a new bug in Ubuntu launchpad.

---

### Post by Miljet on 2009-02-02
This problem seems to be across the board. I am running two computers on Hardy and one on Gutsy. The latest kernel updates broke internet on every one of them. Right now I am running older kernels while I research the problem.

---

### Post by lkraemer on 2009-02-03
See the following post under.....

Installing after a Kernel Upgrade:
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

I think this will fix your problem.

lkraemer

---

### Post by Miljet on 2009-02-16
The above site did nothing for me. I followed the instructions to the letter. 

dmesg gives the following results:

[  903.173242] ath_pci: Unknown symbol _ath_hal_attach
[  903.173411] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  903.174007] ath_pci: Unknown symbol ath_hal_computetxtime
[  903.174487] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  903.174676] ath_pci: Unknown symbol ath_hal_detach
[  903.175427] ath_pci: Unknown symbol ath_hal_probe
[  903.176385] ath_pci: Unknown symbol ath_hal_init_channels
[  903.176744] ath_pci: Unknown symbol ath_hal_getwirelessmodes

Running 
```
modprobe ath_pci
```

yields the following error
```
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-23-generic/madwifi/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

---

