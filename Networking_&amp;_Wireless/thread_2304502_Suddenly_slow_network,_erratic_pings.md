---
title: "Suddenly slow network, erratic pings"
date: 2015-11-27
forum: Networking &amp; Wireless
---

### Post by Headcase_Fargone on 2015-11-27
Hi all, 

In the past week my media server has been acting strangely.  It's running a RAID5 on a gigabit LAN with a 100Mb (megabits) internet connection.  Normally I pull around ~100MBps (megabytes) from its array over the LAN, and Usenet downloads are typically 8-9MBps.

Just a few days ago that changed.  Now my downloads (Usenet, HTTP, FTP, anything) cap out at exactly 1.1MBps.  Stranger still, LAN transfers cap at 11.1MBps.  When this device is downloading from the internet, my entire network slows down.  Pinging Google.com on another wired machine will go from 12ms average to a 600ms average.  VNC sessions become unusable until that download is finished or stopped manually.

This is the only device on the network causing problems and the switch it's plugged into detects a gigabit connection.  Does this sound like a hardware or software issue?  Surely if the NIC was damaged it wouldn't be working at all, right?  It seems incredibly odd that it's slowing down to 10% of the connection type's speed.  10% of the 100Mb internet connection and even 10% of the 1000Mb LAN connection.

---

### Post by tgalati4 on 2015-11-27
Reseat your cables.  If a 1 Gbit/sec connection goes to 100 Mbit or 10 Mbit, then speeds will slow down.  Switches can fail in a less-graceful fashion.  Don't forget to check your power supply for the switch.  Find another one with the same ratings and swap it out.  Look through your log files in /var/log to see if anything shows up.

Then check the SMART status of your drives.  One bad drive in an array can cause issues as well.

---

### Post by Headcase_Fargone on 2015-11-27
I did some troubleshooting by unplugging all the drives and installing the latest Ubuntu Server on an empty SSD I had sitting around.  Downloads from the internet are normal at 9-10MBps and LAN transfers were speedy as well. Plug the old drives back in and I'm back down to 1/10th speed on everything.

All HDDs and the SSD are showing healthy in SMART status.  Downloads from the internet (that are capping out at 1.1MBps still) are downloading straight to the SSD that runs Ubuntu.  That shouldn't even be interacting with the array, right?

More information from further testing:
mdadm reports the array is clean.
A large file transferred from the array to the local SSD at only 8MBps.
Transfer from that SSD over gigabit LAN to SSD on another machine was exactly 11.1MBps, same as transferring from the array.

I'm thinking maybe the SSD the OS is on at this point.  How can I test that further if it's showing healthy in Disk Utility?

---

### Post by tgalati4 on 2015-11-27
Look through *dmesg* for interrupts.  If a piece of hardware is poking your CPU, then that can slow everything down.

```
dmesg | more
```

---

