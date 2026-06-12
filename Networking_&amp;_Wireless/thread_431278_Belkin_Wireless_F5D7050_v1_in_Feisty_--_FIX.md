---
title: "Belkin Wireless F5D7050 v1 in Feisty -- FIX"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by vwkess on 2007-05-02
Just upgraded from Edgy to Fiesty, my Belkin usb wireless dongle (F5D7050 v1) no longer worked. Worked right out of the box when I installed Edgy. Checked my syslog and was filled with:

```
May  2 19:17:58 P4DT kernel: [  878.132133] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
May  2 19:17:58 P4DT kernel: [  878.134128] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
May  2 19:17:58 P4DT kernel: [  878.136123] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
May  2 19:17:58 P4DT kernel: [  878.138119] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
May  2 19:17:58 P4DT kernel: [  878.140114] rt73usb->rt2x00_bbp_read: Error - PHY_CSR3 register busy. Read failed.
May  2 19:17:58 P4DT kernel: [  878.140218] rt73usb->rt73usb_init_bbp: Error - BBP register access failed, aborting.
```

This is what I did to fix it:

Open a terminal window and type:
```
sudo rmmod rt73usb
```

Then type:
```
gksu gedit /etc/modprobe.d/blacklist
```

Add this line to the bottom of the file:
```
blacklist rt73usb
```

Save and close the file, then reboot.

My wireless was enabled/working correctly after this. I did not have to install any other drivers, etc and never did have to do anything like that when I installed Edgy. Don't know if it will work on newer versions of the F5D7050, but it worked fine with mine which is the first version.

Good luck, hope this helps someone. :)

---

### Post by Iturbide on 2007-06-26
Thank you. Been banging my head against this for ages.

---

### Post by VernerVonTux on 2007-07-03
Well, this fix may work for older versions of the Belkin F5D7050 v1 ;however, if you are using the newest version like I am, blacklisting this driver, and rebooting with the device plugged into your usb drive will prevent your system from booting properly, and basically causes a crash because the system runs too slowly for the user to get any feedback from the system. How does one go about checking to see what version of the Belkin F5D7050 they have anyway?

---

### Post by vwkess on 2007-07-10
I don't know what other versions this would work on as I only have version 1. I still had my box, so I just looked on that to check the version number. :)

Should be able to probe the device, I'd imagine it would return the model chipset and the version.

---

