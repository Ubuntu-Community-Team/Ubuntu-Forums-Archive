---
title: "Linux Intel I218-V on ASUS Rampage V Extreme not functioning..."
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by KoSoVaR on 2016-03-13
Hello,

I've installed Ubuntu Server 15.10 and selected openssh-server as well as build-essentials through the manual package selection.  I tried the drivers bundled (modprobe e1000e) and lshw -C net shows 3.2.5 I believe and if I run an ethtool eno1 (my interface name) it shows it's connected, twisted pair, 1Gbps ... but no dice.  No DHCP, and when setting a static IP address I still can't connect to the network.

I'm sort of confused.. so then I tried to download the latest drivers from here [https://downloadcenter.intel.com/download/15817](https://downloadcenter.intel.com/download/15817), make install them, run update-initramfs -u, reboot, and still the same behavior.  But just to validate, lshw -C net did show 3.3.3...

Anyone have experience with getting the I218-V on the Rampage V Extreme working?

Edit:  Quite odd, this is my issue:  [http://ubuntuforums.org/showthread.php?t=2297046&highlight=I218-V](http://ubuntuforums.org/showthread.php?t=2297046&highlight=I218-V)  - I do know that GRUB installed on the same EFI partition as Windows (I didn't expect this to happen.. but it did) .. so I'm going to try and fully shutdown and see what happens.

---

### Post by KoSoVaR on 2016-03-14
Just to confirm, if I completely shut down the machine after having Windows up and reboot in to Ubuntu, the NIC will work.  I find this to be very odd behavior.  I'm unsure if this has to do with Secure Boot being enabled or not.. or something else.  Essentially my experience sums it up as, the NIC is locked somehow after a soft reboot and choosing Ubuntu as a boot option.  To get the NIC to work, I must shut down completely, even removing power, to get the NIC to work in Ubuntu.

---

