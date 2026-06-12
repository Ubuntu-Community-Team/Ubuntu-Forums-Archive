---
title: "Realtek RTL8723 WPA2/Enterprise wifi connectivity and visibility problems."
date: 2018-01-30
forum: Networking &amp; Wireless
---

### Post by eli-rangel on 2018-01-30
I am having trouble connecting to the internet at my university. They use WPA2/Enterprise and require you to register your device through your account to connect. I have registered my device and still cannot see the network while on campus unless I plug in an external USB card. My wired connection is being funky as well but onto the specifics of what is happening and what I'm running:

I have ubuntu 16.04 on notebook with a realtek RTL8723BE PCI wireless adapter. I have been unable to see the networks around my university, however lower security connections (i.e. my home network) are easily able to connect. I have tried manually entering the specifications for the wifi and connecting but it does not seem to work. My next step was to use a command line network manager however I was also unable to find instructions that seemed reliable enough to trust. As of right now my external medialink wifi card will allow me to connect if i am close to a router and still disconnects at Random.

I found the RTL8723BE driver and card were supported with some modprobe modifications in ubuntu 15.04. 

Attached is the script output:
[ATTACH]278379[/ATTACH]

If there is any other information that would be helpful please let me know.
Thank you for any time spent considering this problem.

---

### Post by praseodym on 2018-01-30
There are several APs with the same ESSID. Chose the strongest AP and add that MAC address into the BSSID field in the network-manager profile. Also try deactivating IPv6

---

### Post by Hadaka on 2018-01-30
Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then do..
```
echo options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=2 | sudo tee /etc/modprobe.d/rtl8723be.conf
echo -e [device]nwifi.scan-rand-mac-address=0| sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/AndroidAP/StuWireless
systemctl restart network-manager.service 
```
And..
```
sudo modprobe -rf rtl8723be
sudo modprobe -v rtl8723be
```
Remove wired connection and any usb dongles ...boot and test wireless
Thanks.

---

