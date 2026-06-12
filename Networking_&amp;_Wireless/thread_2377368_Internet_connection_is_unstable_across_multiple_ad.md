---
title: "Internet connection is unstable across multiple adapters, only for this computer"
date: 2017-11-12
forum: Networking &amp; Wireless
---

### Post by howeishotweb on 2017-11-12
Hello

I have regrettably moved into a dorm that only provides a common Wifi connection. My desktop, running Ubuntu Gnome 16.04, is having a really hard time keeping an internet connection. I would say it is gone 80% of the time, with Chromium giving the "DNS_PROBE_FINISHED_NO_INTERNET" error.

From what I can understand from pinging various devices, the network connection to the Wifi AP itself is fine, but the main router stops responding to the computer (connection to the Wifi access points is still running fine). While the desktop is reporting "Host unreachable" for the router, my other devices are working fine.

I have tried with three network adaptors:
[FONT=&amp]USB: Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter[/FONT][/COLOR]
[FONT=&amp]Pci-E: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)[/FONT][/COLOR]
[FONT=&amp]Wired (plugged into a Wifi Extender that is placed closer to the APs): Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
Another USB adapter

They all provide the same performance, though switching from one to another can sometimes revive the internet for a short while.

My (currently Manjaro powered, previously Mint) laptop, another Win7 desktop, and three Android devices does not have this problem, so it's something with my desktop/Ubuntu. There was also no problems at my old dorm, where I had an ethernet cable directly to the 100/100 fiber internet LAN.[/FONT][/COLOR]

---

### Post by praseodym on 2017-11-12
Please run the wireless script from the sticky thread and show the outputs

---

### Post by howeishotweb on 2017-11-12
Sorry bout that [http://paste.ubuntu.com/25949710/](http://paste.ubuntu.com/25949710/)

Also forgot to mention that I've tried changing DNS to OpenDNS and Google's, since both Chromium and apt gives DNS related errors (apt says "could not resolve '[mirror]'", but with no effect.

---

### Post by praseodym on 2017-11-12
For the Atheros card:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
For the Realtek-Stick, change the driver
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist-realtek.conf   
```
For the LAN card, change it also

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.044.02-1_all.deb
sudo dpkg -i r8168-dkms_8.044.02-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot and change the encryption mode for wireless in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by howeishotweb on 2017-11-13
Thank you very much, I have yet to see the connection drop again since following your advice. I wonder why Ubuntu doesn't distribute what I assume are these updates drivers by default, if they are so much better.

---

### Post by howeishotweb on 2018-01-13
Hello again

After some updates that arrived around a week after New Year's, the network connection has degraded again, and it seems like my computer can now only recognize one of my many network cards. Do I have to install something again to get everything back to normal?

New paste from the wireless script: [https://paste.ubuntu.com/26378428/](https://paste.ubuntu.com/26378428/)

---

### Post by praseodym on 2018-01-13
Can you change the encryption mode in your router to WPA2-AES (CCMP) instead of mixed mode WPA/WPA2?

---

### Post by howeishotweb on 2018-01-13
As it is the dorm's Wifi I would very much not change any settings, the board here is already tired enough of me.
Thankfully it seems like my complaints have helped and they are finally going to install fiber into our rooms, but until then it would be nice to get a better Wifi connection.

---

### Post by howeishotweb on 2018-01-17
"lshw -C network" only lists the Atheros PCI-e wifi card (along with ethernet), while "lsusb" can see my Edimax Realtek USB adaptor... but it's not available as a network card, what's going on I wonder

---

