---
title: "Unable to boot ubuntu 10.10 after installing from another computer"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by sigui.dmor on 2010-12-25
Hello everybody,

I am very new to ubuntu and to computers in general. 

I installed Ubuntu Desktop Edition 10.10 yesterday in a laptop computer (a Macbook 2,1-2GB RAM @ 667MHz, a 60 GB SATA HDD and an Intel Core 2 Duo processor @ 1.83GHz) alongside Mac OS X 10.6.5 and it's working great but then I wanted to install the same ubuntu on another laptop (a VSONIC GREEN320-one single module of 256MB DDR266 @ 133MHz and a VIA C3 Processor, I guess it's a national brand for I cannot find any site regarding to the product).

Since the machine won't allow me to boot via USB flash drive (and neither let me get into the BIOS for more than a second to set it to boot from the USB flash drive) and also shuts down as long as I close the loaded CD tray I am unable to install the operating system from any external bootable mean.

I decided to use the ubuntu CD I already had, run it on the working computer and install the operating system from there into the second computer's HDD connected via an IDE/ATA to USB cable unsuccessfully: it turns on but after the BIOS screen disappears there is  a blinking "_" and then it goes no further. 

Any recommendations will be more than appreciated and if this is not specific to ubuntu please let me know and point me in the right direction.

Thanks to you all in advance :)

Regards, Francisco Mendoza R.

P.S. Merry Christmas

---

### Post by cariboo on 2010-12-26
It looks like you din't install grub to the mbr of the harddrive for the vsonic system, probably the simplest way to fix the problem, would be to connect the hard drive to the mac book, then boot from the Live cd. Once at the desktop, Open an Applications->Accessories->Terminal and type:

[LIST=1]
[*]sudo mount /dev/sda /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Once at the chroot prompt, type the following command:

```
grub-install /dev/sda
```

Once the above command has run successfully, type:

```
update-grub
```

Then press Ctrl-D twice, and reboot, rebooting will allow you to make sure that grub has been installed successfully and the system can boot from the hard drive. Once you have made sure you can boot from the hard drive, you can move it to the other laptop.

Just as an aside, the specs on the vsonic system, are pretty low-end, Ubuntu will probably not run very well on it. You may want to look at something lighter for that system.

---

### Post by sigui.dmor on 2010-12-26
Hello again,

I connected the hard drive to the mac book and booted from the ubuntu Live cd, then copied the first command down to the terminal but I got "mount: /dev/sda/ already mounted or /mnt busy and thus with the next one: "mount: mount point /mnt/ dev does not exist" and so on until sudo chroot /mnt which gave me:
chroot: failed to run command `/bin/bash': No such file or directory.

I ultimately assumed that I had to add the number and name that was assigned to the device as it appeared on the "Allocate drive space" window of the ubuntu installer because typing the commands verbatim as above wouldn't work. This time grub was installed and updated. I pressed Ctrl and D keys at the same time twice and rebooted but now I get the following at start up: "error: no such device - "Hex string"
"grub rescue>"

I still think that was my error at some point (may be I typed something wrong or changing the first command with .../sdb2/... was not correct, which is probably the cause).

Thank you anyway cariboo907 and yes, indeed the specs of that computer are not recommended on the page for running ubuntu. I will pick out another version once I have this one running.

All the best, Francisco Mendoza R.

---

### Post by sigui.dmor on 2010-12-29
Hi all,

I was able to mend my own error and I want to share the thread I read to solve it: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I think the solution left by cariboo907 is the most reliable for my main problem and I will try it again later but this time making sure what is the linux partition called on my HDD.

Cheers, Francisco Mendoza R.

---

### Post by sigui.dmor on 2010-12-30
Finally I was able to install grub on the VSONIC's Hard Drive (which by the way is a 20GB ATA one) following the above instructions, however the computer shuts down a few seconds after I press enter to the first option "Ubuntu, with Linux 2.6 35-22-generic" (there appear more options like Mac OS X 32/64-bit, a duplicated "Ubuntu, with Linux", and their respective recovery mode options but of course none of these work). If I don't do anything nothing happens.

This is in fact the reason why I tried to make an installation of linux: the same thing happened to Windows XP and I thought that would change when I formatted the HDD but now this might be more a motherboard-related issue, rather than an OS-related one.

Thank you very much for your input.

---

### Post by sigui.dmor on 2011-01-10
Hello,

Well I've got Ubuntu 10.10 running. The last thing I did was get into the ubuntu's recovery mode, then update grub from there and that did the trick. Although due to the specifications of the machine (as cariboo907 mentioned above) ubuntu won't run pretty nice even when setting all visual effects to the minimum. Yet I am happy with it and I will be looking for a more suitable version of the OS that will fit perfect to my computer.

P.S. The "shutting down" issue was being caused by a defective AC adapter; it will be replaced as soon as possible.

---

