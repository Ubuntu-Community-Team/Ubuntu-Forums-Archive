---
title: "Issues with RTL8723BE PCIe Wireless Network Adapter on xubuntu 16.04"
date: 2017-07-01
forum: Networking &amp; Wireless
---

### Post by jackharding on 2017-07-01
Hi there. I just switched to xubuntu this morning from Windows 10. After the switch, my WiFi connection was extremely weak, or would disconnect if I wasn't right next to the router.

I found [this thread from two years ago]("https://ubuntuforums.org/showthread.php?t=2261702") from a guy that had a similar problem. I followed chili555's instructions:

sudo apt-get install linux-headers-generic build-essential git
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install
sudo reboot
After the reboot, I can't even pick up my network anymore. Could anyone please help me out?

---

### Post by jeremy31 on 2017-07-01
If this is an HP computer, we can test some antenna parameters
```
iwlist scan | egrep -i 'ssid|quality'
```
These results will show the SSID and signal strength with the default parameter, then we will unload the wifi module and load with one of the antenna settings and check results


```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```

Any better or the same?  Then we can try with the antenna 2 setting


```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```


If ant_sel=1 was the best then do
```
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

If ant_sel=2 was better
```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf
```

It will work after reboots.  The Ubuntu 16.04 kernel has the same parameter available so you may not need to install the module from github after a kernel update but you may need to see if the antenna parameter needs to be changed

---

