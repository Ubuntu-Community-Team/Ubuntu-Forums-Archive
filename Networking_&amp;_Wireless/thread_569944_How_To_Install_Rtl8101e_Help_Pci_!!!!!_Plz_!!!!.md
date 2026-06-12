---
title: "How To Install Rtl8101e Help Pci !!!!! Plz !!!!"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by kp4xzor_! on 2007-10-07
i just got a new laptop, i'm going nuts trying to find out how 2 do it, i got a TOSHIBA SATELLITE, AMD 64 X 2 i'm trying to stop using Vista but is my only way to connect to the internet, plz help !!!!

Wireless card bouilt in into laptop : REALTEK, RTL8101E !!! PLZ !! HELP !!

PS: i got UBUNTU  7.04





                                      :confused:

---

### Post by kevdog on 2007-10-07
What version of Ubuntu (32 vs 64) are you using and what drivers do you have available for your card.  Vista drivers will not work!

---

### Post by kp4xzor_! on 2007-10-07
ubuntu-7.04-desktop-i386

that's the one i installed

---

### Post by noob12 on 2007-10-07
Not sure what specific 8101E device you have but if you have the one with device id 10ec:8136 it should be covered by the r8169 driver.

Check these things.  What device id does 
```

lspci -nn

```
show for the device?  Is it 10ec:8136 ?

Does the device show up as UNCLAIMED in 
```

sudo lshw -C network

```
or is it showing up with a configuration line that shows the r8169 driver.

If it shows up and the driver has claimed it, then check if it says link="no" in the configuration line or if **sudo ethtool eth0** shows "Link Detected: no".  In that case you may have the common problem solved in this thread:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

If not, you have to find a USB drive to get text output off the box where you can post it and start by posting the output of those diagnostics above.

---

