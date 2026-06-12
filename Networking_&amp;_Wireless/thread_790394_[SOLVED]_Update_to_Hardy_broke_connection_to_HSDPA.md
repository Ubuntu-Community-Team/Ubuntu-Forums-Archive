---
title: "[SOLVED] Update to Hardy broke connection to HSDPA modem"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Robhogg on 2008-05-11
Up to now, I have had my Huawei E220 HSDPA/G3 modem working fine under Gutsy (using huaweiAktBbo to switch the device from CD-ROM to modem mode, and wvdial to connect). I took the option of upgrading to Hardy today, and now cannot connect.

Under Gutsy, when the modem was first connected, it would be in mass-storage mode, and *ls /dev/ttyUSB** would show only */dev/ttyUSB0* until I ran *sudo huaweiAktBbo*. Now, when the device is connected, *ls -l /dev/ttyUSB** shows:

```
crw-rw---- 1 root dialout 188, 0 2008-05-11 15:24 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2008-05-11 15:24 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2008-05-11 15:24 /dev/ttyUSB2
```

This looks correct. However, trying to connect with *sudo wvdial* throws the following error:
```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
```

*file* is able to correctly identify the devices, but *cat* again throws a "No such file..." error.

Among the output of *dmesg | grep -i usb* is:
```

[ 1826.234950] usb 2-1: configuration #1 chosen from 1 choice
[ 1826.237053] usb 2-1: airprime converter now attached to ttyUSB0
[ 1826.237170] usb 2-1: airprime converter now attached to ttyUSB1
[ 1826.237284] usb 2-1: airprime converter now attached to ttyUSB2
[ 1865.722383] airprime ttyUSB0: airprime_open - failed submitting read urb 0 for port 0, error -2
[ 1875.577989] airprime ttyUSB0: airprime_open - failed submitting read urb 0 for port 0, error -2
[ 1875.578212] airprime ttyUSB0: airprime_open - failed submitting read urb 0 for port 0, error -2
...
```

Googling around suggests that *airprime converter* is possibly a driver for the Verizon AirPrime 5220 wireless card (which I don't have).

Any suggestions? Or anyone else have this problem?
Thanks,
Rob

[color=red]UPDATE:[/color] I now have it connected. I blacklisted airprime, with the result that the only USB0 was shown when first connected. However, the switching utility (huaweiAktBbo) no longer worked until I rebooted with the previous kernel (2.6.22) instead of the new one installed with Hardy (2.6.24). It now works fine, and I've updated grub's config accordingly.

It looks like support for the card has been broken, or left out, with the latest kernel build. Feature or oversight?

---

### Post by Robhogg on 2008-05-11
I'd like to report this as a bug, but would appreciate advice on how to go about this. I've registered with bugs.launchpad.net (which I understand is the appropriate place to report it), but the first thing it asks me for is the package name.

I suspect the problem might be with the kernel itself, though this isn't listed as an installed package in Synaptic, and I don't know how to go about verifying that it really is the kernel at fault.

---

### Post by Robhogg on 2008-05-17
Well, I've got it sorted without using huaweiAktBbo. A friend gave me copies of a shell script and udev rules downloaded from [this website]("http://oozie.fm.interia.pl/pro/huawei-e220/") - just a matter of copying the script into a directory in $PATH, and copying the rules into /etc/udev/rules.d (the two files in the *files* directory of the tarball on that site). The device is now recognised when its plugged in, and connects fine with *wvdial*.

The thing is, according to the site, these files should not be needed on kernels later than 2.6.20.

---

### Post by paddyboy on 2008-05-21
Robhogg,
         I upgraded from Feisty to Hardy and have been having this problem too. I don't have the huaweiAktBo thingy so your solution looks attractive. I'm a bit of a noob, so any chance of a simple talk through ? When you say put in $PATH would /home/bin be OK ? Also that bit about putting the rules in /etc/udev/rules.d... is that file already there ? Also can I download this 'tarball' via WINDOWS ?

I'm a bit stuck here since the only access I have to the net is through WINDOWS so I can't really do a normal download.

Any help would be much appreciated.

pb

---

