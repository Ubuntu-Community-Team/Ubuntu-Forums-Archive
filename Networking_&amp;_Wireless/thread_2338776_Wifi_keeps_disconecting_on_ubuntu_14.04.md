---
title: "Wifi keeps disconecting on ubuntu 14.04"
date: 2016-10-01
forum: Networking &amp; Wireless
---

### Post by wasabishot on 2016-10-01
Hello dear friends.

I am using a Dell Inspiron laptop with ubuntu 14.04.
Recently I have moved to a new shared house and for some reason my computer keep disconnecting from the wifi network, showing me the "hardware disabled" icon every time it disconnects.
To reconnect I need to disable the hardware myself and then enable it again until the next time it disconnects, which happens very often.

It has not happened with any other network and I believe there is a compatibility issue with the wifi router.
Is there a way to solve the issue without changing the router itself?

Thanks in advance.

---

### Post by Hadaka on 2016-10-02
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**

From your directory please copy,paste and post the **wireless-info.txt**
thanks.

---

### Post by wasabishot on 2016-10-02
Thanks Hadaka.

File is attached.

---

### Post by Hadaka on 2016-10-02
Hi Please open a terminal ctrl/alt/t then Copy and paste..

```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi

echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```

*To **delete **the above should they not help please do.
```
sudo sed -i '/^"options iwlwifi 11n_disable=8"/ d' /etc/modprobe.d/iwlwifi.conf
sudo sed -i '/^"options mac80211 probe_wait_ms=1000"/ d' /etc/modprobe.d/mac80211.conf
```
Then do...  to set your **Country code. **correctly, it is currently not defined, this causes issues.
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
```
Finally you have your access point..router name as .. 'lil'what'  the quotes.. '  ' single or double " "
are not a good idea as linux sees that as a command..please consider changing it to...  lil_what or
something with no quotes.
thanks.

---

