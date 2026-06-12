---
title: "phy0 -&gt; rt2x00usb_vendor_request: Error-Vendor Request 0x07 failed for offset 0x7010"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by Ashrael on 2014-04-07
I keep having serious connection problems with EVERY usb wifi-stick I try, BUMMER! 

This is the eroor I get with the WUSB600N V2: phy0 -> rt2xc00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x07010 with error -71.  The stick works for awhile, different timespan every time, then it crashes with the error...

Anyone have a clue how to fix this? Why would it send the request in the first place, because before it asks this, it just works???

I have bought 3 different usb-wifi sticks and NONE of them work! ALL of them are on the HCL! <snip> This is a showstopper for me! It cost me heaps of money and I get no working hardware.... I have been using Ubuntu since 2004, but now I am willing to ditch it all together! Not only because of the hardware issues, but also because off all the <snip> they started putting in Ubuntu the last few years, which I must remove every time I install. Is there a distro which supports hardware and privacy better? Please tell me.

TIA!

---

### Post by chili555 on 2014-04-07
Is this a request for help with wireless or a troll for an Ubuntu trashing flame war? If the latter, you are in the wrong forum. If you actually want help with rt2800usb, then I suggest you compile the 3.13 kernel version driver. With a temporary wired ethernet connection:```
sudo apt-get install linux-headers-generic build-essential

```Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.xz) Right-click it and select 'Extract Here.' Back to the terminal:```
cd ~/Desktop/backports-3.13.2-1
make defconfig-wifi
make
sudo make install
```The process takes a few minutes; please be patient.

Reboot and let us have your report.

---

