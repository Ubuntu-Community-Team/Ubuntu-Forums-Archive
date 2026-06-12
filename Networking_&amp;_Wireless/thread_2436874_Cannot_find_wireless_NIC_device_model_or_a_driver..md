---
title: "Cannot find wireless NIC device model or a driver."
date: 2020-02-14
forum: Networking &amp; Wireless
---

### Post by shaii on 2020-02-14
Hello. 
I cannot find a device name for my wireless NIC installed in my HP laptop, as there is no driver installed and I wished to locate one. 
It is a fresh install of Kubuntu and the wireless NIC has never worked. Kubuntu 18.04LTS is of the latest version and I have generated a wireless-info.txt utilizing the script in the pinned post, and am willing to supply more information if needed. 
I will attempt to respond as promptly as possible to any replies. 
[http://paste.ubuntu.com/p/dcm4HbBGG9/](http://paste.ubuntu.com/p/dcm4HbBGG9/) (wireless-info.txt)
Thank you.

---

### Post by jeremy31 on 2020-02-14
First step, disable Secure Boot in BIOS/UEFI
Then in terminal do ```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

