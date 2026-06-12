---
title: "Network cards on 15.04 not working - no internet access"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by sam135 on 2015-05-29
I decided to install Ubuntu for the first time on a new computer, and upon booting up the live session, the ethernet would not establish a connection. I still went through with the install and the same thing continued to happen after booting into the fresh install. Decided to go out and buy a wireless network card and I can detect my network with it, but when I try to connect it attempts to do so for a short time then tells me I am offline. So no internet access through Ethernet or WiFi. I am a noob, but am willing to do whatever it takes to fix this issue. Also Ethernet worked perfect on windows. My wireless card is "Ralink RT5390". Ethernet controller is "Realtek RT8111/8168/8411". I just would like one of these to work, Ethernet perferebly. Thanks in advance.

---

### Post by praseodym on 2015-05-30
Hi,

download these files and save them in "Downloads":

[http://media-cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/24/39/3005217-r8168-dkms-8.039.00.tar.gz)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu3_all.deb)

Installation:
```

cd ~/Downloads/
sudo tar xvf 3005217-r8168-dkms-8.039.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.039.00
sudo dkms build -m r8168-dkms -v 8.039.00
sudo dkms install -m r8168-dkms -v 8.039.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot. LAN should work. Now run the wireless-script from the sticky-thread and show the outputs.

---

