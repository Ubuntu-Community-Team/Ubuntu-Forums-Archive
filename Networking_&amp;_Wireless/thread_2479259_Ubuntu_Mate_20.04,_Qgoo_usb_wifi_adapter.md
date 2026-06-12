---
title: "Ubuntu Mate 20.04, Qgoo usb wifi adapter"
date: 2022-09-19
forum: Networking &amp; Wireless
---

### Post by SciGuy1872 on 2022-09-19
Hi. I bought a Qgoo 1200 usb wifi adapter and it was delivered today. However, the computer does not see it (see screenshot for terminal commands). I have another usb adapter that I am using to connect here, but the speed is terrible--it should be up to 50Mbps or 30 at least, but it registers at 1Mbps. I have an install.sh file, but after running in the terminal, I am asked for the root make password, I enter my sudo, but that does not complete the install process. Should I remove the usb I am using now in the future when trying to get the Qgoo installed--if I can leave them both in when installing the Qgoo, how do I choose which usb is used? I tried rebooting with just the Qgoo in.  I also tried removing the working usb and replacing with three Qgoo, but it was still not recognized.    Thanks.

---

### Post by chili555 on 2022-09-20
Please leave the working USB wireless attached and open a terminal and do:

```
sudo apt update
sudo apt install build-essential bc dkms git
git clone https://github.com/morrownr/88x2bu-20210702.git
cd 88x2bu-20210702
sudo ./install-driver.sh
```

Remove the working USB, insert the Qgoo and reboot.

You should be all set.

---

### Post by SciGuy1872 on 2022-09-20
Hi.  I have some errors when updating.  The last time this happened I was able to use the "Broken Packages" in the Software Boutique to fix the problem, but now Boutique and Welcome do not open.  The terminal screenshot I attached lists line 58  as malformed.  I have attached the Sources as a screenshot.

---

### Post by SciGuy1872 on 2022-09-20
Ok.  I fixed it by commenting out where there were errors.  Now to try to install the driver.

---

