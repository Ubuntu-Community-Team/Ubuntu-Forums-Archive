---
title: "Problem with connecting to wifi after reboot"
date: 2015-01-18
forum: Networking &amp; Wireless
---

### Post by leszek3 on 2015-01-18
Dear All,

I have the following problem.

Installed ubuntu 32 bit (14.04? LTS) on my laptop.
I can easilly connect to any wifi network for the first time (tested twice).

however after shutting down and rebooting, I cannot reconnect to the wifi network again.
There is no such a problem if I try to re-connect to a wifi network on my iphone.

Can someone please tell me why ubuntu has this issue and how to solve it?

I tried deleting the connection, and then adding it again.
I also tried this command
sudo killall wpa_supplicant

but it did not help.

many thanks

---

### Post by praseodym on 2015-01-18
Please run the wireless script from the sticky thread once working and not working and show the outputs

---

### Post by leszek3 on 2015-01-19
> **praseodym said:**
> Please run the wireless script from the sticky thread once working and not working and show the outputs


thanks for the tip - here it goes (as attachment because I had no Idea how to post it without the text being automatically converted to icons).

---

### Post by leszek3 on 2015-01-20
I'm also attaching txt versions

---

### Post by praseodym on 2015-01-20
Try changing the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```

Reboot.

---

### Post by leszek3 on 2015-01-27
Hi,
I tried what you suggested.

the packages were downloaded and installed.

However after reboot, I cannot connect to any network - even to my iphone, which previously worked.
anything else I could try?

best

---

### Post by praseodym on 2015-01-28
Please run the wireless script again

---

