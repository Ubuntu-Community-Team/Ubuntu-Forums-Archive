---
title: "connect to WPA2 wifi headless ubuntu"
date: 2019-01-17
forum: Networking &amp; Wireless
---

### Post by 1nstant on 2019-01-17
I have installed a fresh copy of ubuntu minimum. What is the best way to  connect to the HC2? When I google the answer there are so many differnet ways, some seem really old. I do not know which one to follow


 I currectly have it connect to the machine via router lan. 

The drivers I have installed is
sudo apt install rtl8812au-dkms

I can do a scan. 

So I dont mess up, what is the easiest way to get wifi to auto connect. It has WPA2 (AES) encryption.

For example sake, my wifi is called "weefee" and the password to conenct is "password234"

Here is 
lsusb
Bus 006 Device 002: ID 0bda:8153 Realtek Semiconductor Corp.
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:a811 Realtek Semiconductor Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Im running 18.04


so far the thing I have retired is:

Modify /etc/network/interfaces
> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid SSID_Name
wireless-key XXXXX

then I ran 
sudo dhclient wlan0

and it just hangs

so i tried


root@odroid:~# wpa_passphrase myssid >> /etc/wpa_supplicant.conf
thepassword
root@odroid:~# nano cat /etc/wpa_supplicant.conf
root@odroid:~# cat /etc/wpa_supplicant.conf
# reading passphrase from stdin
network={
        ssid="myssid"
        #psk="thepassword"
        psk=randomstuff
}
root@odroid:~# sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf      Successfully initialized wpa_supplicant
root@odroid:~# iw wlan0 link
Not connected.

---

### Post by chili555 on 2019-01-17
The answer depends entirely on your Ubuntu version. Please post:```
lsb_release -d
```Is there any improvement with:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```

---

