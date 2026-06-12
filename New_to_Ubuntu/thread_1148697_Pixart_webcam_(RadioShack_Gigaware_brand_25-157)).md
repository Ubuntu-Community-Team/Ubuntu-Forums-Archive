---
title: "Pixart webcam (RadioShack Gigaware brand 25-157))"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by egalvan on 2009-05-04
Radio Shack Gigaware brand webcam

Model # 25-157
"Webcam with Mic"

Plugged in and green LED lights up.

Nothing but static on "cheese";

"camorama" complains that:

```
Could not connect to video device (/dev/video0).
Please check connection
```

The following commands give these results...
What am I missing?
What am I doing wrong?


```

ernest@gx280:~$ **sudo lsusb**
 
Bus 005 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000
**Bus 003 Device 002: ID 093a:2620 Pixart Imaging, Inc. **
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 413c:2010 Dell Computer Corp. 
Bus 001 Device 007: ID 10d5:55a2 Uni Class Technology Co., Ltd 
Bus 001 Device 006: ID 03f0:0b0c Hewlett-Packard 
Bus 001 Device 005: ID 413c:1003 Dell Computer Corp. 
Bus 001 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000
```

```
ernest@gx280:~$  **dmesg | tail**

[ 2820.236446] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2820.238038] sd 4:0:0:0: [sdb] 195371568 512-byte hardware sectors (100030 MB)
[ 2820.239657] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2820.239664] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2820.240192]  sdb: sdb1
[ 2820.574979] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 2820.575053] sd 4:0:0:0: Attached scsi generic sg2 type 0
[b][ 8850.832208] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 8851.065067] usb 3-2: configuration #1 chosen from 1 choice
[ 8851.305952] usbcore: registered new interface driver snd-usb-audio[/b]
ernest@gx280:~$ 
```

```
ernest@gx280:~$ **lsmod | grep gspca**
ernest@gx280:~$ 
```


```

ernest@gx280:~$ **xawtv -c /dev/video0**

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-23-generic)
xinerama 0: 1680x1050+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
ernest@gx280:~$ 
```

---

### Post by cariboo on 2009-05-04
It looks like the driver for your webcam isn't being loaded. According to what I found, you need the gspca_pac7311 driver. Try to load it manually by opening a terminal and typing:

```
sudo modprobe gspca_pac7311
```

then check to see if a video device has been created:

```
ls /dev/vid*
```

---

### Post by egalvan on 2009-05-05
> **cariboo907 said:**
> the driver for webcam isn't being loaded.
 , you need the gspca_pac7311 driver.
 Try to load it manually by opening a terminal and typing:

```
sudo modprobe gspca_pac7311
```



This give the following:

```
~$ sudo modprobe gspca_pac7311
[sudo] password for ernest: 
FATAL: Module gspca_pac7311 not found.
~$ 

```

---

### Post by egalvan on 2009-05-07
downloaded 

**gspcav1-20071224.tar.gz**

but am having major troubles...

I've never installed via sources before.

---

### Post by egalvan on 2009-05-14
weekly bump

---

### Post by Alfred_McGee on 2009-05-22
Here's the most recent fix for this problem in Jaunty that I was able to find, but it involves building your own kernel -not always a great idea: [http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/](http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/)

Several bug watchers, as well as the guy who posted the kernel fix, say that full support for this webcam is already incorporated into the upcoming kernel version (2.6.29) and thus should soon be added through the routine Ubuntu system updates.

I took the easy way out, however, by getting a refund from Radio Shack and buying one of the webcams listed as working "out of the box" on this page:      [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

