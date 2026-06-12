---
title: "Wifi slow on my HP-6135dx Pavillion laptop using Ubuntu 15.10"
date: 2016-12-04
forum: Networking &amp; Wireless
---

### Post by akash-u1 on 2016-12-04
I have been having issues with my wifi on my laptop for a while now, actually probably ever since I moved to Ubuntu 14.xx and versions upwards. It seems significantly slower on my laptop than on my phone with speeds of ~3MBps testing with speedtest.net when I get over ~35MBps on my phone at the same place close to the access point (~90% signal strength using WIcd n/w manager). I tried a bunch of things I saw on various forums, couldn't get them to improve my connection. Here's the link to my wireless info using Varun's script.

[http://pastebin.ubuntu.com/23581010/](http://pastebin.ubuntu.com/23581010/)

---

### Post by jeremy31 on 2016-12-04
*Thread moved to **Networking & Wireless**.*

I would suggest changing from Ubuntu 15.10 to a supported release which currently are 12.04 until next year, 14.04(2019 support), 16.04(2021), or 16.10(july 2017)

---

### Post by akash-u1 on 2016-12-04
Hey Jeremy, thanks for the reply. Yes, I should move to a LTS. But for the time being is there anything I can do to improve the wireless speeds? As I understand just upgrading to a LTE won't fix this possibly.

---

### Post by wildmanne39 on 2016-12-05
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here, please now that your system is at risk for security issues because no applications will receive updates at all.
Thanks

---

### Post by akash-u1 on 2016-12-06
Pretty much the same script I downloaded before I think, but the diagnostic info is here again: [http://pastebin.ubuntu.com/23586930/](http://pastebin.ubuntu.com/23586930/) Thanks!!

---

### Post by wildmanne39 on 2016-12-06
First let's turn off power management by running the following command.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
You have network manager and wicd installed, you need to remove one of them, I recommend wicd since it i not longer supported.

Go into your router and change the encryption to just WPA2 (CCMP) AES not TKIP, set channel to 1,6,or 11 instead of auto, then the save settings.

From the information the least traffic is on channel 11.

Let's set a driver parameter:
```
echo "options rt2800pci  nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Change your network settings in network manager in the top right of the screen to match the screenshots.
[ATTACH=CONFIG]272565[/ATTACH][ATTACH=CONFIG]272566[/ATTACH]

---

### Post by akash-u1 on 2016-12-06
Thanks for the tips. I did make the changes and I see a marginal improvement avg around ~5MBps or so on my laptop. Pasting the info from the script after the changes.
[http://pastebin.ubuntu.com/23591249/](http://pastebin.ubuntu.com/23591249/)

---

### Post by akash-u1 on 2016-12-07
I updated to 16.04 Ubuntu, seems to have sped up ~2.5x. Getting around ~13 MBps download and upload now, which is an improvement. Latest stats: [http://pastebin.ubuntu.com/23593540/](http://pastebin.ubuntu.com/23593540/) Any room for improvement?

---

### Post by wildmanne39 on 2016-12-07
Need to turn of power management again since the upgrade and see if that helps, there are a lot of networks in your area they are for sure causing interference.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by akash-u1 on 2016-12-07
Thanks again. Updated pastebin: [http://pastebin.ubuntu.com/23596797/](http://pastebin.ubuntu.com/23596797/) Since the upgrade to LTS and the steps you asked me to follow, it's definitely been better than when I posted originally, but still I get speeds between 10 and 20 MBps... Is there anything else I can possibly do?

---

### Post by jeremy31 on 2016-12-08
Can you move your wifi to channel 9?

Run the command suggested by wildmanne39 as this will disable wifi powersave ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
And if you are in the US, set the country code with
```

sudo iw reg set US
```
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```
Reboot

---

### Post by akash-u1 on 2016-12-08
Thanks again. Switched off power management for wifi and changed the country code. Pastebin: [http://pastebin.ubuntu.com/23601615/](http://pastebin.ubuntu.com/23601615/) There's definitely a significant increase. I am getting consistently between 20-26 MBps download speed now. Great, any thing more I can tune to make it faster :-)

---

### Post by jeremy31 on 2016-12-09
Disabling IPv6 in Network Manager settings might help some

---

### Post by akash-u1 on 2016-12-09
Seems it's ignored already

[[/etc/NetworkManager/system-connections/TP-LINK_047C]] (600 root)
[connection] id=TP-LINK_047C | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=TP-LINK_047C
[ipv4] method=auto
[ipv6] method=ignore

---

### Post by jeremy31 on 2016-12-09
There isn't anything I can think of to speed it up anymore then as it seems you have the nohwcrypt parameter set

---

### Post by akash-u1 on 2016-12-10
Could you explain what these changes are along with setting the right country code and how it helped me? Thanks.

> **wildmanne39 said:**
> First let's turn off power management by running the following command.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
You have network manager and wicd installed, you need to remove one of them, I recommend wicd since it i not longer supported.

Go into your router and change the encryption to just WPA2 (CCMP) AES not TKIP, set channel to 1,6,or 11 instead of auto, then the save settings.

From the information the least traffic is on channel 11.

Let's set a driver parameter:
```
echo "options rt2800pci  nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Change your network settings in network manager in the top right of the screen to match the screenshots.
[ATTACH=CONFIG]272565[/ATTACH][ATTACH=CONFIG]272566[/ATTACH]

---

### Post by jeremy31 on 2016-12-10
I actually think the first code did the most good as it disabled wifi powersave and I saw this problem before with the fail to flush queue with power management being on.

Setting the country code can help keep the computer and router wifi channels in agreement, sometimes the default setting works and other times it doesn't

Many off us have found that using WPA2 CCMP(AES) works better than WEP/TKIP or plain WPA in regards to connection and download speed

The driver parameter setting was used in the past to fix the fail to flush queue error

The screenshots was just adding the free google DNS to your connection and shouldn't hurt anything and could help some issues

---

