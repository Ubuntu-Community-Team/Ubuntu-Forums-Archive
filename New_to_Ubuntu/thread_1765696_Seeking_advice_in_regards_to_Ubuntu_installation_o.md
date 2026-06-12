---
title: "Seeking advice in regards to Ubuntu installation on a netbook"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Jeremywilms on 2011-05-23
I have two cores each clocked at 1.6GHz and roughly 1GB of ram. I'm thinking I should get the netbook edition of Ubuntu, given I can still use the Eclipse IDE w\ Java & C++. My machine lacks a CD Drive, and I really don't want to be bothered to track down my old USB Drive. I was thinking of possibly doing a network boot with memdisk but I'm unsure if this would work w\ ubuntu.

I'm trying to figure out how I can get this installed on my netbook. I've googled and hit some tutorials yet they all require either a USB or they contain out-dated links.

If someone could please point me in the right direction, it would be greatly appreciated.

Thanks.

---

### Post by crispy_420 on 2011-05-23
There is always the option of taking out the drive and installing on a different machine. Then reinstalling the drive. Or you could just track down a flash drive and use [unetbootin]("http://unetbootin.sourceforge.net/") to install the distro of your choice.

Thought they dropped netbook edition for 11.04?

---

### Post by snowpine on 2011-05-23
The best instructions for installing Ubuntu are here:

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

CD-ROM or Live USB are the recommended install methods. Alternately, if the netbook has Windows installed, you can use WUBI.

---

### Post by Jeremywilms on 2011-05-23
> **snowpine said:**
> The best instructions for installing Ubuntu are here:

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

CD-ROM or Live USB are the recommended install methods. Alternately, if the netbook has Windows installed, you can use WUBI.

I'm not too worried if My netbook version of ubuntu is a little out of date. Also, if it helps I found an SD Memory card I can use, but I'm not sure if they're bootable.

I thought WUBI installed ubuntu into a VM? Maybe I'm mistaken though. I'd rather avoid the VM becuase on a netbook ubuntu and windows aren't going to run well simultaneously.

---

### Post by mikewhatever on 2011-05-23
Here is a good howto:
[https://help.ubuntu.com/community/Installation/QuickNetboot](https://help.ubuntu.com/community/Installation/QuickNetboot)

The only link to replace there is the one to netboot.tar.gz in step 2.
For Ubuntu 11.04:
[http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/natty/main/installer-i386/current/images/netboot/netboot.tar.gz)
For Ubuntu 10.04:
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/netboot.tar.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/netboot.tar.gz)

---

### Post by snowpine on 2011-05-23
> **Jeremywilms said:**
> I'm not too worried if My netbook version of ubuntu is a little out of date. Also, if it helps I found an SD Memory card I can use, but I'm not sure if they're bootable.

I thought WUBI installed ubuntu into a VM? Maybe I'm mistaken though. I'd rather avoid the VM becuase on a netbook ubuntu and windows aren't going to run well simultaneously.

I haven't used WUBI personally, just throwing it out there as an option.

Why would you choose to use an older version, just curious?

Some netbooks can boot from SD card, some can't--it depends on the BIOS.

---

### Post by Jeremywilms on 2011-05-23
> **snowpine said:**
> I haven't used WUBI personally, just throwing it out there as an option.

Why would you choose to use an older version, just curious?

Some netbooks can boot from SD card, some can't--it depends on the BIOS.

I never really seems to be impacted significantly by the Ubuntu OS Updates. I'm not a server admin or anything, I just use my netbook as something to program on while I'm away from my primary pc.

Anyway, I'll give the net boot a shot. Thanks.

---

### Post by eltonw on 2011-05-23
> **Jeremywilms said:**
> I have two cores each clocked at 1.6GHz and roughly 1GB of ram. I'm thinking I should get the netbook edition of Ubuntu, given I can still use the Eclipse IDE w\ Java & C++. My machine lacks a CD Drive, and I really don't want to be bothered to track down my old USB Drive. I was thinking of possibly doing a network boot with memdisk but I'm unsure if this would work w\ ubuntu.

I'm trying to figure out how I can get this installed on my netbook. I've googled and hit some tutorials yet they all require either a USB or they contain out-dated links.

If someone could please point me in the right direction, it would be greatly appreciated.

Thanks.

It would help if you stated the exact brand / model netbook. :confused:

I have an Asus EEE 1000 PC, and I no longer use my portable DVD drive to install:!: I simply download the ISO image, and use **UNetbootin** to create on an SD card or USB stick. ... then boot my machine from that. Run as "live" if you wish to preview, or install from the SD / or USB. 

For instructions on burning to SD or USB stck SEE section 2:[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")8-)

Surely your machine has usb ports, if not an SD slot?

HTH.

---

### Post by Jeremywilms on 2011-05-23
Sorry, I should've been more clear. I already got the Linux installation to work via a netboot. I'm only keeping it from being marked as solve because I may encounter problems during the installation process.

Just making sure, the installation will ask which partition to install on, right?

---

### Post by Jeremywilms on 2011-05-23
Alright, so I just go to the point where I select the partition I am to install ubuntu on, however whenenver I try to resize a partition, I get: "An error occured while writing the changes to the sorage devices. The resize operation has been aborted."

---

### Post by eltonw on 2011-05-23
> **Jeremywilms said:**
> Alright, so I just go to the point where I select the partition I am to install ubuntu on, however whenenver I try to resize a partition, I get: "An error occured while writing the changes to the sorage devices. The resize operation has been aborted."
This _sounds like you are trying to resize a partition that is IN USE_, i.e. the partition on which you are currently writing data. 

I have never installed via netboot, as I find downloading and burning the ISO to USB or SD to be more convenient. 
(My reason: if my internet connection slows down or is flaky, I can still do the complete install. Once the system is in place, you can then [re-] connect to the internet to do your updates.

Again: you would get better help if you were more specific on your hardware info: make / model computer (I'm **not** insisting: It's just "a word to the wise"...):-\"

---

### Post by Jeremywilms on 2011-05-23
> **eltonw said:**
> This _sounds like you are trying to resize a partition that is IN USE_, i.e. the partition on which you are currently writing data. 

I have never installed via netboot, as I find downloading and burning the ISO to USB or SD to be more convenient. 
(My reason: if my internet connection slows down or is flaky, I can still do the complete install. Once the system is in place, you can then [re-] connect to the internet to do your updates.

Again: you would get better help if you were more specific on your hardware info: make / model computer (I'm **not** insisting: It's just "a word to the wise"...):-\"


I'm using an Acer Aspire One netbook; I may be able to get more information regarding the hardware in a momment.

---

### Post by mikewhatever on 2011-05-23
@eltonw
Don't think the installer is supposed to write data to the hdd before the root partition has been designated. Ramdisk, perhaps.

@Jeremywilms
I am pretty sure there is a way to resize the Windows partition from Windows. Just hope you don't already have four primary partitions.

---

