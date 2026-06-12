---
title: "Brother DCP-7030 scanner drivers"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by shivanshu on 2011-07-06
Hi, I am unable to install the Brother DCP-7030 scanner drivers onto my laptop. I could successfully install the printer drivers though. Its an HP laptop with a core 2 duo processor. please help.

---

### Post by jtarin on 2011-07-06
In the terminal issue the command ```
lsusb
``` and post the results here.

---

### Post by walt.smith1960 on 2011-07-06
> **shivanshu said:**
> Hi, I am unable to install the Brother DCP-7030 scanner drivers onto my laptop. I could successfully install the printer drivers though. Its an HP laptop with a core 2 duo processor. please help.

Hi

Did you see this page?  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

I had to do this in order for Ubuntu to see my scanner with a USB connection.
**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.[B]
2.[/B]Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
  
  The lines to be added---------------------------
 # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"        [B]

3.[/B] Restart the OS.

The instructions mention Ubuntu 9.10 and 10.04 but I think it applies to newer Ubuntu releases as well.  Good luck.

---

### Post by shivanshu on 2011-07-08
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by shivanshu on 2011-07-08
@walt.smith1960:
i tried doing that, and restarted the OS, but the scanner still doesnt work. please help me make it work.!!!

---

### Post by jonathon6017 on 2011-07-08
> **shivanshu said:**
> Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

You DID have it plugged up when you ran this command right?

---

