---
title: "USB 2.0 to SATA/IDE"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by novice_ubuntee on 2010-11-13
Hello,

I'm a complete beginner so please be gentle.

I'm trying to connect the hard drive rescued from my sister's conked out laptop (which was running Windows) to my laptop (which is running Ubuntu 10.04LTS) via a USB 2.0 to SATA/IDE cable.

When I connect the hard drive to the laptop through the cable, the hard drive starts whirring as though it's working, but I can't find it anywhere on my system.

I've done a number of internet searches trying to find the solution to the problem and have tried 'sudo fdisk -l'. I get the following output:
----------
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       37598   253176367+  83  Linux
/dev/sda3           37599       38913    10562737+   5  Extended
/dev/sda5           37599       38913    10562706   82  Linux swap / Solaris
-----------

however the terminal prompt does not return. I have to kill the terminal window to end the process. Without the hard drive cable connected, the terminal prompt returns as expected.

I get a similar issue when trying to run Gparted. With the hard drive connected, Gparted says "scanning all devices" but never completes. If I pull out the cable connecting the hard drive, Gparted returns immediately with the results of the scan.

I have read online that using this cable on Windows works without any problems, however I have recently switched the last computer in the house from Windows to Ubuntu which does not seem to deal with this well.

Any help would be greatly appreciated.

---

### Post by Matt__ on 2010-11-13
I know this isnt much help, but I have an externally powered USB to IDE/sata adapter and it works fine --- drive mounts to desktop, though it sometimes needs the drive to spin up and run for 10/15 seconds before you plug in the usb.

Is the purpose of connecting this drive to reclaim data? or to use it as external backup?

If its the first option can you not just swap the drive out with your own and use a live disk until you figure out how to get the USB cable to run?
That way you could recover any data/repair master boot/remove virusses/format.

can you connect it and terminal lsusb, see if it shows up

---

### Post by mcduck on 2010-11-13
My guess would be that the drive isn't getting enough power.

Not all USB ports are capable of powering even a 2,5" laptop drive, and quite often and additional power cable (or second USB cable for power) is required. Also some USB cables and especially extension cables, hubs and such can cause problems.

So if the adapter you are using allows it, try adding a power cable. Otherwise try different USB ports on your computer, for example with desktop machines it's quite common that the USB connectors directly on the motherboard will give you more power than the ones on the case. 

Other than that, you can always run "tail -f /var/log/dmesg" in a terminal and then plug in the drive to catch any log messages about how the drive is detected. Works great for troubleshooting any other removable devices as well... ;)

(edit: if you can't connect an additional power cable with the adapter you have now, pretty much all 2,5" drive cases have both data and power connections, usually come with both cables included and hardly cost anything at all... If you find one that doesn't require any tools for changing the drive, that would be a great alternative for a simple adapter cable.)

---

### Post by novice_ubuntee on 2010-11-13
Thank you for your responses.

Matt__ I'm doing this just to retrieve data that was on the hard disk. I'm currently trying to get this working on my laptop so wouldn't be confident at all in opening it up to swap the hard disk. There is a desktop computer in the house which will be decommissioned in the next couple of days though so once that's done, I will try your suggestion of swapping out the disk and using a LiveCD if all else has failed up to then (will a laptop hard disk work on a desktop computer?).

mcduck, I think you've got a good point. The cable did come with an adaptor to plug it in to the power supply but there isn't a connection for it on the laptop hard disk. I've connected the cable with the USB at the end to the disk I'm trying to retrieve from. The USB is plugged in to a port linked directly on to the motherboard, I also connected the red SATA cable to the motherboard of my desktop computer at the same time and that made no difference.

Running "tail -f /var/log/dmesg" didn't produce any new output at all when I connected it as above (again supporting your suggestion that sufficient power might be the problem).
You mentioned a drive case. Is this the kind of thing you have in mind? [http://www.amazon.co.uk/LUPO-Inch-SATA-Hard-Drive/dp/B0030Y58LY/ref=sr_1_2?ie=UTF8&qid=1289687297&sr=8-2](http://www.amazon.co.uk/LUPO-Inch-SATA-Hard-Drive/dp/B0030Y58LY/ref=sr_1_2?ie=UTF8&qid=1289687297&sr=8-2)

---

### Post by mcduck on 2010-11-13
I don't see a power connector on that case, of course it might come with one of those split cables (one connector on the enclosure end, two USB connectors to the computer) which works just fine but it's not mentioned in the description so you might want to make sure the cable is included before you make an order.

Here's another one, which at least based on the pictures does have the cable included: [http://www.amazon.co.uk/SATA-HARD-DRIVE-CADDY-ENCLOSURE/dp/B002UZO07C/ref=sr_1_77?s=computers&ie=UTF8&qid=1289690732&sr=1-77]("http://www.amazon.co.uk/SATA-HARD-DRIVE-CADDY-ENCLOSURE/dp/B002UZO07C/ref=sr_1_77?s=computers&ie=UTF8&qid=1289690732&sr=1-77")

In the end you can just pick any case you like, just as long as you make sure it has some way to provide more power than you get from only one USB port.

---

### Post by lkraemer on 2010-11-14
novice_ubuntee,
[B]DO NOT USE ANY ADDITIONAL POWER ADAPTORS IN YOUR ATTEMPT TO READ THE DRIVE!
YOU WILL BLOW THE USB PORT IF YOU DO.[/B]

The only thing that is acceptable would be a USB cable with an dual end,
for power from another port, but I've never needed one of those for a
Laptop Drive.

Since Gparted, and Ubuntu won't find the drive, it's likely trashed.
About the only thing you can do is try using Testdisk to recover the
information.  But, before trying that you need some experience using Testdisk,
and you need another external Drive to store the data on.

lk

---

### Post by mattman85 on 2010-12-03
I'm having similar issues, where I plug in a 2.5" IDE drive to my USB adapter and it spins up, but doesn't mount.

I know it gets enough power, because when I used it in Windows 7, it saw the drive fine. Is there a way to see why Ubuntu isn't mounting it as USB mass storage, like it should be? Is that where "tail -f /var/log/dmesg" would come into play?

---

