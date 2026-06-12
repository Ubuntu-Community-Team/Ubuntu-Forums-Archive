---
title: "Fresh install connects to wifi, but no internet"
date: 2014-09-19
forum: Networking &amp; Wireless
---

### Post by Jared_Swanson on 2014-09-19
Wifi signal is excellent, but I can't connect to the internet at all. Several other devices are connected with no problems whatsoever. [Here]("http://pastebin.ubuntu.com/8381051/") are the wireless_script results.

I was running Fedora 20 with pretty much the same issue. Decided to scrap it and switch to Ubuntu hoping that would solve the problem. Didn't happen. No internet whether I use onboard wifi adapter, USB wifi adapter, or ethernet (through plugable USB adapter). I would love to blame it on Comcast, but everything other device is running fine. Any ideas?

---

### Post by praseodym on 2014-09-19
Hi,

deactivate the N-mode of the internal card driver and the power management of both devices:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
sudo iwconfig wlan0 power off
sudo iwconfig wlan1 power off
```
Afterwards change to pure WPA2-AES (CCMP) encryption instead of mixed mode WPA/WPA2

Edit: If the stick doesn't work you could try to change the driver (if any connection is available):

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA
echo "blacklist rt2800usb" | sudo tee /etc/modprobe.d/blacklist-ralink.conf
```
and reboot.

---

### Post by Jared_Swanson on 2014-09-20
You are my hero! Your fix worked perfectly!

---

