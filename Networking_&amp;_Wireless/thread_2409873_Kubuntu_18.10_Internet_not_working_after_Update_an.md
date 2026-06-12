---
title: "Kubuntu 18.10: Internet not working after Update and Reboot"
date: 2019-01-07
forum: Networking &amp; Wireless
---

### Post by athelbrim on 2019-01-07
Hello all,
I've recently installed Kubuntu 18.10 on my HP Laptop.

This particular HP Laptop (which is temporary for now) uses the Realtek RTL8723DE, which doesn't have official support yet out of the box - so after I installed, I had to compile an open-source third party driver ([https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/td-p/6477307](https://h30434.www3.hp.com/t5/Notebook-Wireless-and-Networking/Realtek-8723DE-wifi-module-amp-Bluetooth-Linux-driver/td-p/6477307)) to get it to work - after manually downloading from Ubuntu Packages gcc and make, as well as all of the necessary dependencies and moving the packages from my Windows HD to my Linux HD (which was a pain), I logged out, logged back in, and was able to connect to my WiFi no problem.

I decided to install some software and update my system, and now, Wi-Fi seems to be broken, as when I access my computer, my computer doesn't detect any networks and acts as if there was no driver on the computer.

I've tried various commands based on older forum posts to restart the networking service, but the various commands can't find a networking service, and I've tried uninstalling via "sudo make uninstall" and reinstalling, but to no avail, still not working. I've even restarted and went on Windows to see if it's a problem with the hardware which could have died, but Windows is working normally, so there's something wrong on Kubuntu.

Any suggestions or ideas to try would be useful.

Thanks.

---

### Post by praseodym on 2019-01-08
Please run the wireless script from the sticky thread and show the outputs

---

### Post by chili555 on 2019-01-08
Please run and post:```
sudo dkms status
```Thanks.

---

