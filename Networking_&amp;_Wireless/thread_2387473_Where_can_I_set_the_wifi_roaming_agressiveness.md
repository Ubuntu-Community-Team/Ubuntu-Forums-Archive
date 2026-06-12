---
title: "Where can I set the wifi roaming agressiveness?"
date: 2018-03-19
forum: Networking &amp; Wireless
---

### Post by doisyg on 2018-03-19
Hello,
I am looking for any parameters that could help me control wifi roaming on a wifi network where all the AP share the same SSID (Unifi AP AC LR). My card is too long too switch from one AP to another to the point where I have none or extremely slow connectivity.
I am on Ubuntu 16.04 and use Intel Corporation Wireless 8260 (rev 3a). 
All the drivers are up to date and my kernel is 4.13.0-37-generic

---

### Post by Hadaka on 2018-03-20
Hi,please open a terminal..crtl/alt/t then Copy and paste..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
```
cat wireless-info.txt | nc termbin.com 9999
```

This will have an output that looks this...
[http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

---

### Post by chili555 on 2018-03-20
I wonder if this may be helpful: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by doisyg on 2018-03-20
Here is the output of wireless info (could not get termbin to work with a text file for some reason)
[http://paste.ubuntu.com/p/zVdF5sbgFg/](http://paste.ubuntu.com/p/zVdF5sbgFg/)

---

### Post by doisyg on 2018-03-20
> **chili555 said:**
> I wonder if this may be helpful: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

I read this link, but I am looking for the opposite: being able to switch earlier (ie before the link quality becomes so bad that there is no working connection) from one AP to another. The device I am using is moving.

---

### Post by Hadaka on 2018-03-20
Hi, there is no "wifi agressiveness" function other than binding to the BSSID
with the best 'Quality' signal as Dr. chili555 suggested.
to view and find the best "Quality" signal.. please do..
```
sudo iwlist wlp1s0 scan | egrep -i 'cell|quality|essid'
```
Configure the network connection Wyca per the link Dr Chil555 provided..
then do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
and also set IPv6 to Ignore..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Wyca
systemctl restart network-manager.service
```
and set your country code..
```
sudo iw reg set FR
sudo sed -i 's/=.*/=FR/' /etc/default/crda
```
Thanks.

---

### Post by doisyg on 2018-11-29
After switching to ubuntu 18.04, still the same issue: the wifi card takes too long to switch from one AP to the other.
Hadaka, the method you provide is not a solution. I don't want to bind to one and only one AP, I want to switch faster from one AP to another (ie I want the switch to happen earlier, before the signal degrades too much).

---

### Post by sveterv on 2018-12-16
You can try to lower number of beacon losses to get disconnected from actual AP and try to switch to another by your WiFi card, edit /etc/modprobe.d/wifi-sensitivity.conf and add those lines:

options mac80211 beacon_loss_count=1 max_probe_tries=1

Reboot, and check if it makes your WiFi more sensitive to AP signal changes. If not, try add another parameter to the line above: probe_wait_ms=100

On really poor signal these setting may give you no WiFi connection at all, don't panic, just set those limit a little higher, you can use two strategies, keep probe_wait_ms higher (default is 500 but you can go higher) and keep other two options low or the opposite, the two other options higher and probe_wait_ms lower than default 500.

Oh, by the way you can change all those setting "live" without reboots in /sys/module/mac80211/parameters/... directory, for example:
echo 1 > /sys/module/mac80211/parameters/beacon_loss_count
You need to be root for doing this.

---

