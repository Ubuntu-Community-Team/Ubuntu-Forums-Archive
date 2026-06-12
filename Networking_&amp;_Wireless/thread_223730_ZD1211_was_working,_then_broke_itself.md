---
title: "ZD1211 was working, then broke itself"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by Cheeto on 2006-07-26
I have an Airlink 3026 USB adapter and had it working under Dapper until I did an update.  I have downloaded the driver at [http://zd1211.ath.cx](http://zd1211.ath.cx) (currently version 83), then the kernel headers, ran a make clean, then make, then make install.  It worked fine until I let Ubuntu do a software update.  Now while it says that it's activated and shows the proper configuration settings, it won't select wlan0 as the default interface (discards the change whenever I click okay) and hangs on boot and shutdown if I have the adapter plugged in.

I know Ubuntu updated the kernel to a new version, but even the old kernel version won't work anymore.

Would it be easier and more reliable to use ndiswrapper and the Windows driver?

---

### Post by Cheeto on 2006-07-28
Does anyone have any suggestions?

---

### Post by Cheeto on 2006-08-01
Okay, I've tried recompiling under the new kernel, again under the old kernel, and different drivers.  It still does not work.  Is anyone interested in helping, please?

---

### Post by az on 2006-08-01
I have a similar device and the version 83 drivers works for a stock 386 kernel from the live cd and the most recent kernel in Ubuntu for me.

Did you change your configuration?

unplug the device, reboot and then run

tail -f /var/log/messages

and plug in the device.  Post the output.

---

### Post by Bezmotivnik on 2006-08-02
Just a thought -- the AirLink101 AWLL3026 (at least currently) uses a 1211b chip, not the 1211 chip.  I believe there is a difference in the way the configuration goes with these, or a driver difference, but unfortunately I do not remember the details.  I read it on the driver site a few months back. 

I do know that this device will not quite work *properly* under XP with the ZD1211 driver.

If nothing else works, you might take a look at that.

---

### Post by az on 2006-08-02
> **Bezmotivnik said:**
> uses a 1211b chip, not the 1211 chip.  I believe there is a difference in the way the configuration goes with these, or a driver difference, but unfortunately I do not remember the details.  I read it on the driver site a few months back. 

You need to edit the makefile:

# set to 1 for zd1211b
ZD1211REV_B=1

The rewritten version (which is currently part of the 2.6.18 kernel tree - no need to get it seperately!) does not include a b version, but the driver can work with both types.  So you will soon (Edgy?) not have to worry about that.

---

