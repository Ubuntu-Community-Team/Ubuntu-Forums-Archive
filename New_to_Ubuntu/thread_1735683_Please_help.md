---
title: "Please help"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by northwestern on 2011-04-21
I have been running Ubuntu on my HP laptop (Windows 7 32 bit) using wubi.Can I dual boot my laptop with Ubuntu using a buffalo mini station hard drive for the Ubuntu download.I seem to get mixed messages from the forums I have read.
 
Regard 
Northwestern

---

### Post by LinXNut on 2011-04-21
Is what your saying burn the ISO onto a portable disk drive? Than yes, when you run the Ubuntu set-up, save it onto the drive of your choice.
I am not sure if this is what you needed?

---

### Post by northwestern on 2011-04-21
Thank you for you reply, I have got the CD ready to download, what I am asking is instead of partitioning my laptops drive, can i load Ubuntu on to my seperate hard drive and still have the dual boot options.
 
Many Thanks

---

### Post by rosencrantz on 2011-04-21
It depends on what you want to do.
If your laptop is able to boot from USB, follow this howto
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
If you want to transfer your Wubi install, it might get a bit trickier.

---

### Post by rosencrantz on 2011-04-21
Dual booting should be possible
Install Grub to the external disk's boot sector, set it up to chainload Windows 7 from the Grub OS selection menu (it's probably done that way automatically), and configure your BIOS to boot from USB first.
This should give you dual boot options with the external drive plugged in and direct Windows booting when it's not.

---

### Post by northwestern on 2011-04-21
Thank you Rosencrantz
 
I do not want to use wubi. I am a complete novice with Ubuntu (and not very computer savvy). Is there anywhere I can find what you suggest in simple laymans terms.
Regards
Northwestern

---

### Post by rosencrantz on 2011-04-21
OK, some further information required...
Does you computer have a CD drive?
In that case, burn a live Ubuntu, boot it with the external HD up and running and follow the instructions here
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

If you have no CD drive, but 2 USB ports and an additional thumb drive, you can do a variant of the above by booting a live Linux from the thumb drive and installing it to the hard disk.

If you have just the external disk, we'll have to worry about extra partitions, but there are HowTos for it.

---

### Post by northwestern on 2011-04-23
Thank you for your reply.
I do have an internal CD drive along with the appropiate Ubuntu 10.10 installation CD.
Unfortunately the web page you directed me to is slightly out of date (2008),I could not find partitions manager in the Systems - Administration section.
I decided to go ahead with the on screen instructions downloading the software on to my Buffalo hard drive.Install went OK, but no matter how I changed the start up sequence in the BIOS I was left with a black screen and a flashing cursor.
Any more ideas please?.
Regards
northwestern

---

### Post by rosencrantz on 2011-04-23
Sorry about the dated instructions - the partitioner should be in System->Administration->Disk Utility. However, you might not even need to format and partition, the Ubuntu installer should do that for you.
I hope you only get the blinking cursor when trying to boot from the external disk, your laptop's hard disk shouldn't have been modified.
Thinking about what went wrong ... 
Do you know which hard disk you installed the boot loader to? It should have been the external one, as detailed in the HowTo.
Did you read the part about changing grub's menu.lst file? This is rather important, as the boot order of the hard disk is probably switched, but I just noticed the instructions seem to be for grub legacy and not grub2. If your Ubuntu is more recent than 9.04, we need to adapt them.
Can you boot the live CD, see whether there is an Ubuntu filesystem on the external disk and post the contents of the file /etc/default/grub here?

---

