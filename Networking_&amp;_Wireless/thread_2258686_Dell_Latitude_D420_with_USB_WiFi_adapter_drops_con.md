---
title: "Dell Latitude D420 with USB WiFi adapter drops connection every ~5-10 minutes"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by Ryan_Learn on 2014-12-29
Hey guys,

I was hoping you guys could help me with a wifi issue on my laptop. It's running Ubuntu 14.10, connecting to my wifi network[ via this USB-adapter ]("http://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1"). It is able to start the connection just fine, but after a short period, the connection encounters a problem. The network manager still shows my being connected to the local WiFi, but pinging domain names or trying to access websites via the browser fails. I've tried this on multiple networks so I know it's not an issue specific to my router. 

I've gone ahead and attached the output of the wireless diagnostic script on provide in the forums.

Any insight that anyone can offer would be greatly appreciated.

---

### Post by praseodym on 2014-12-29
Change the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

What about the internal card? Install the missing firmware via:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by Ryan_Learn on 2014-12-29
Not only did the first troubleshooting technique work, but so did the second. Guess I can toss the USB stick back into the drawer. 

Thanks a ton.

---

### Post by praseodym on 2014-12-29
Glad it worked. Please mark the thread "solved" using thread tools. Thanks.

---

