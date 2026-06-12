---
title: "Upgrade knocked off wireless"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by J A Smith on 2008-06-04
Hi everyone, 

I've been using wireless on my Atheros 802.11 wireless card using this method:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Last night I installed some upgrades from update manager and its stop working.
 
I am now using a pre-upgrade version of Ubuntu, listed under GRUB.

How do I fix this?

Thanks.

---

### Post by chili555 on 2008-06-04
When you compiled the module, it was only for the kernel running at the moment. If your update was a new kernel, 2.6.24-17-generic, perhaps, no new ath_pci module is in it until you create it. While you are booted into the latest kernel, repeat these steps:> 4. Get inside the unpacked directory:
cd madwifi-ng-r2756+ar5007

6. Now you can build your madwifi and install the modules:
make
sudo make install
sudo modprobe ath_pci
sudo modprobe wlan_scan_staYou will build the correct module for your newer kernel. Whenever an update includes a newer kernel, repeat the process.

---

### Post by J A Smith on 2008-06-04
Thanks Chilli555.

I take it I do that in the terminal? How do you I access the madwifi folder in the terminal? Sorry for being slow.

---

### Post by chili555 on 2008-06-04
In a terminal, correct. If you followed the HOWTO in the link you provided, then you downloaded a .tar.gz file and extracted it to get this folder. It may be in your/home/smitty directory or on your desktop. If it's in your user directory you can change directory, or cd:```
cd madwifi-ng-r2756+ar5007
```If you downloaded and extracted it to your desktop, then it's:```
cd Desktop/madwifi-ng-r2756+ar5007
```I hope you did not Trash the file and it's folder, although, with memory sticks, etc., that is recoverable.

Post back if you need more help.

---

### Post by ennika on 2008-06-04
I have the same problem. Tried to create the module, but am getting error messages on the last two steps (Invalid module format). Any idea what I'm doing wrong?

---

### Post by chili555 on 2008-06-04
> **ennika said:**
> I have the same problem. Tried to create the module, but am getting error messages on the last two steps (Invalid module format). Any idea what I'm doing wrong?The 'make and 'sudo make install' went well? No errors?

---

### Post by ennika on 2008-06-04
(warning: I'm a bloody noob to ubuntu/linux)
'make' didn't work ('Permission denied' on almost every line), in my clueless innocence I went for 'sudo make' instead (is that the same?) which looks as if it works, can't see any errors in 'sudo make install' as well (at least not those that usually shout ERROR or FATAL at me)

---

### Post by chili555 on 2008-06-04
> **ennika said:**
> (warning: I'm a bloody noob to ubuntu/linux)
'make' didn't work ('Permission denied' on almost every line), in my clueless innocence I went for 'sudo make' instead (is that the same?) which looks as if it works, can't see any errors in 'sudo make install' as well (at least not those that usually shout ERROR or FATAL at me)Sounds OK so far; now as you take the remaining steps, what, if anything fails?

---

### Post by ennika on 2008-06-04
on 'sudo modprobe ath_pci' all I get is:
WARNING: Error inserting ath_hal (/lib/.../ath.hal.ko): Invalid module format.
WARNING: Error inserting wlan (..../wlan.ko): Invalid module format.
FATAL: Error inserting ath_pci (.../ath.pci.ko): Invalid module format.

(same for everything under 'sudo modprobe wlan_scan_sta')

---

### Post by J A Smith on 2008-06-04
Thanks Chilli555, all sorted.

I followed your instructions and its back up and running.

Good luck ennika!

---

### Post by chili555 on 2008-06-04
@ennika-

I assume you are using the HOWTO referenced above. If you have *build-essential* and *linux-headers-generic* installed, it should 'make' with no warnings and no errors. I just did it, although I do not have this card. Of course I will not install.

Please check in System-Admin-Synaptic and be sure you have these two installed. Install as needed and re-run 'make.'

'sudo make' scares me.

---

