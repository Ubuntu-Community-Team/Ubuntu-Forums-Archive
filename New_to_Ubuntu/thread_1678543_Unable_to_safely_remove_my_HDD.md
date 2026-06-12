---
title: "Unable to safely remove my HDD"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Tuxdroid on 2011-01-30
Hi i've been trying ubuntu for a couple of hours now but i bumbed on a major bug for people who dont want to wast their backups 
I inserted my Lacie Minimus(USB 3.0), and it mounted in a second, so far no problems, installed some files and then i want to remove my disk safely, but it wont and give me this message

Unable to stop drive
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

if u press OK, the drive is still there, unmounted but still accessible.
My iomega-drive doesnt have the problem but that is a 2.0 drive :KS

So any idea how to solve this, and is their some applet that i can add so i dont have to go to nautilus for every safely remove.

Best regards 

Tuxdroid

---

### Post by davidmohammed on 2011-01-30
there is an open [bug]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575") for this.

current recommended workaround is

sudo eject /dev/sdb

---

### Post by Tuxdroid on 2011-01-31
tx didnt see that, but eject command doesnt work, unmount does

---

