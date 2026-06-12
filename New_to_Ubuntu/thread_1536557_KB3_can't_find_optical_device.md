---
title: "KB3 can't find optical device"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Omanski on 2010-07-22
I downloaded OS image file, tried to burn it to a CD-R using Brasero.  No joy.  

Explored several help threads and found that Brasero doesn't work for many users.  Most recommended KB3 to burn CDs.  

I downloaded & installed KB3.  When I tried to use KB3 to burn the image to disk I got an error message (see attached) saying KB3 could not find the optical device.  

Other applications on my system can find the optical device, so maybe KB3 has to be shown where the device is?  I looked for preferences in KB3 but can't find any.  I reviewed the forums and can't find a reference to this.  

I'm running Ubuntu 8.04.  I'm an absolute beginner.

---

### Post by Michael Dooley on 2010-07-22
Take a look at this page:

[http://userbase.kde.org/K3b](http://userbase.kde.org/K3b)

Scroll down to the pre-setup section.

---

### Post by Omanski on 2010-07-22
My setup options don't look the same (attachment).  KB3 sees the optical disk hardware as read-only.  When I attempted to add the device to Writer Drives I got the error message "Could not find additional device at /dev/scd0"

---

### Post by Eisenwinter on 2010-07-22
What happens if you try to run k3b as root, and detect drives?

Does it detect them all successfully?

---

### Post by Omanski on 2010-07-22
> **Eisenwinter said:**
> What happens if you try to run k3b as root, and detect drives?

Does it detect them all successfully?
Sorry, I'm an absolute newbie.  What command does that and how do I use it?

---

### Post by Eisenwinter on 2010-07-23
Sorry for the late reply, I have been busy and couldn't come here.

Open up a terminal, and type the following command:

```
sudo k3b
```

You will be asked to input your username password, do so.

Now, try to scan for devices again.

If it finds anything, and says everything is alright, then all you have is a permissions problem (not being "allowed" to access a device on your system).

If it still gives you errors, or warnings which you cannot comprehend, paste them here, or upload a screenshot of what's going on.

---

### Post by Omanski on 2010-07-23
I'm trying to post the error message but the editor is turning some of the code to smilies.  How do I turn the smilies off?

[never mind, I found it]

---

### Post by Omanski on 2010-07-23
> **Eisenwinter said:**
> Sorry for the late reply, I have been busy and couldn't come here.

Open up a terminal, and type the following command:

```
sudo k3b
```You will be asked to input your username password, do so.

Now, try to scan for devices again.

If it finds anything, and says everything is alright, then all you have is a permissions problem (not being "allowed" to access a device on your system).

If it still gives you errors, or warnings which you cannot comprehend, paste them here, or upload a screenshot of what's going on.

I ran the command you suggested and received the following in return:

dave@dave-desktop:/$ sudo k3b
[sudo] password for dave: 
kbuildsycoca running...
Error: "/var/tmp/kdecache-dave" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-dave" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-dave" is owned by uid 1000 instead of uid 0.
dave@dave-desktop:/$ kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_iHDS118___4 to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
/dev/scd0 seems to be cdrom
bus: 2, id: 0, lun: 0
(K3bDevice::Device) /dev/scd0: init()
(K3bDevice::Device) /dev/scd0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/scd0 feature: DVD+R
(K3bDevice::Device) /dev/scd0 feature: DVD+RW
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.
(K3bDevice::Device) /dev/scd0: modeSense 0x05 failed!
(K3bDevice::Device) /dev/scd0: Cannot check write modes.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE length det failed.
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SENSE (5a)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        24
                           ascq:       0
(K3bDevice::Device) /dev/scd0: MODE SENSE with real length 65535 failed.
/dev/scd0 resolved to /dev/scd0
(K3bDevice::DeviceManager) dev /dev/scd0 already found
(K3bDevice::DeviceManager) found config entry for devicetype: ATAPI iHDS118   4
Devices:
------------------------------
Blockdevice:    /dev/scd0
Generic device: 
Vendor:         ATAPI
Description:    iHDS118   4
Version:        FL04
Write speed:    0
Profiles:       DVD-ROM, CD-ROM
Read Cap:       DVD-ROM, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM
Write Cap:      Error
Writing modes:  None
Reader aliases: /dev/scd0
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
Error: "/var/tmp/kdecache-dave" is owned by uid 1000 instead of uid 0.


It appears to recognize the device but still returns errors.  Maybe this is the problem with permissions you suggested?

---

