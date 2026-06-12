---
title: "Wifi upload extremely slow: Dell Vostro 3580 / Qualcomm Atheros QCA9377"
date: 2019-11-12
forum: Networking &amp; Wireless
---

### Post by yaakov-belch2 on 2019-11-12
On a fresh install of **Ubuntu 16.04** (and also on the pre-installation-test 18.04 image), my Dell Vostro has **extremely low Wifi upload speeds:**
[URL="https://www.speedtest.net/"]
https://www.speedtest.net[/URL] reports: 14ms ping, 26.66Mbps download and **0.00Mbps upload.** However, there is *some* upload connectivity, it's just extremely slow.
By contrast, a different laptop on the same Wifi network reports: 15ms ping, 50.00Mbps download and 3.50Mbps upload.

Here is the **result of the wireless info script:** [http://paste.ubuntu.com/p/gzB9kZSCyF/](http://paste.ubuntu.com/p/gzB9kZSCyF/) 

My computer is a **Dell Vostro 3580 that came with Ubuntu pre-installed.**  I hoped that it would be Ubuntu-compatible out-of-the-box, but later I found out that it may require special vendor fixes (see: [https://certification.ubuntu.com/hardware/201810-26532](https://certification.ubuntu.com/hardware/201810-26532): "The Dell Vostro 3580 laptop with the components described below has been awarded the status of **certified pre-install for Ubuntu**.... Standard images of Ubuntu may not work at all on the system or may not work well." (Except for wireless upload, it seems to work well for me).

This laptop uses the **Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)** network adapter.

I tried all the tips described at [https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/](https://itsfoss.com/speed-up-slow-wifi-connection-ubuntu/) but none helps.

What can I do to fix this problem?  Is there any information that I can add to make this easier to analyze?

---

### Post by praseodym on 2019-11-15
Try updating the firmware
```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```

and reboot. Please run the wireless script again afterwards

---

### Post by yaakov-belch2 on 2019-11-19
This problem was solved by replacing the WiFi router.  The ISP explained that the old router provided less channels than the new computer expects.  With the new router, everything works well.

---

