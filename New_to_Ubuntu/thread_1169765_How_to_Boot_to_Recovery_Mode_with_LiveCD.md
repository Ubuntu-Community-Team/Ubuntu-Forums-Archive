---
title: "How to Boot to Recovery Mode with LiveCD"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by biggiemokey on 2009-05-25
How do I boot to Recovery Mode with the 9.04 LiveCD?  I can't get Ubuntu to boot up or install as it hangs on "Starting Bluetooth", and someone suggested a fix if I can get to a terminal, and said booting to recovery mode will let me boot up without the GUI.  So how do I get to it?  I found Safe Graphics Mode, but that doesn't boot up either, and my searching only found queries on how to disable recovery mode...please help

---

### Post by shifty_powers on 2009-05-25
press escape during boot, before the splash screen, to get to the grub menu.

(this is without the cd)

---

### Post by ladasky on 2009-05-25
This may or may not be helpful...
 
I just had an issue with a computer that I couldn't get to boot from CD.  It turned out that the order of the boot devices in my BIOS was backwards.  If the system failed to boot from my hard disk, it would never progress to the CD-ROM drive.  It would just hang.
 
Is it possible that, in your BIOS, the system is configured to do something with your Bluetooth device before you get to booting?  Perhaps if you go into your BIOS and disable that device, at least for now, the system will move on to subsequent tasks.

---

### Post by biggiemokey on 2009-07-10
So, how would I disable Bluetooth from BIOS?  I wasn't aware that I had it on my computer, I thought the install would hang because I don't have the proper bluetooth hardware.  There is nothing with bluetooth in the boot order, but I'm not sure how to disable it otherwise if that's what you meant.

And I realize that it's been a long time since I posted this thread, I kind of gave up on it, but I would really like to get back into it.  I got 9.04 installed by using the upgrade tool from 8.10, but now I can't boot into it!  Can't boot to recovery mode either.  I did find this script:
```
sudo mv/etc/init.d/bluetooth /etc/init.d/bluetooth_old
sudo update-rc.d bluetooth remove
sudo reboot
```

Seemed to work with other people, but I can't get to a terminal!

---

