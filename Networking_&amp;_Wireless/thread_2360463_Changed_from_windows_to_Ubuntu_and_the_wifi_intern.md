---
title: "Changed from windows to Ubuntu and the wifi internet is noticably slower. Please help"
date: 2017-05-05
forum: Networking &amp; Wireless
---

### Post by con1993 on 2017-05-05
I know terminal exists but have no idea how to use it really. I am sorry for my ignorance, please help.

(Internet was working okay on windows.)

---

### Post by Bucky Ball on 2017-05-05
Welcome. Well, open that terminal and paste this in (control+shift+v to copy in a terminal).

```
sudo lshw -C network
```

That command will ask for your user password. It will be invisible when you type. This is normal. Just type it and hit enter.

Post the output of that command back here between [code] tags. There is a green link on how to use them in my signature, bottom of my post.

Also, check 'Additional Drivers'. Is there anything in there that pertains to wireless? Don't enable it just yet, please just let us know.

---

### Post by con1993 on 2017-05-05
Thanks for the quick response.

```


  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 10
       serial: 20:89:84:68:de:e5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:9fb00000-9fb007ff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 2c:d0:5a:69:ee:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.8.0-36-generic firmware=N/A ip=192.168.1.35 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:b3500000-b357ffff memory:b3580000-b358ffff


```

Does that help?

---

### Post by Bucky Ball on 2017-05-05
Yes. Seems you have the correct driver for your wireless card. Now give us this, please.

```
rfkill list all
```

---

### Post by con1993 on 2017-05-06
Thanks.

```


rfkill list all


```

---

### Post by mörgæs on 2017-05-06
My guess is that Bucky Ball wanted you to post the results from running the command, not the command itself.

---

### Post by con1993 on 2017-05-06
oops haha my fault, forgot to copy the results.

```


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by wildmanne39 on 2017-05-06
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

Then go into network manager and set your settings to match the screenshots.
Reboot

---

### Post by con1993 on 2017-05-06
Thank you. I did as you instructed however I am getting the same results on [http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by wildmanne39 on 2017-05-06
How slow is the connection and do you have your ethernet unplugged?

---

### Post by con1993 on 2017-05-06
download rate: 26mbps
upload rate: 6.35mbps

I am on a laptop that is connecting to a wifi box which has everything plugged into the back of it.

---

### Post by wildmanne39 on 2017-05-06
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

How fast is your connection?

I am off for the night, it is time to get some sleep.

---

### Post by con1993 on 2017-05-06
Thanks for staying awake as long as you did.

[http://paste.ubuntu.com/24521855/](http://paste.ubuntu.com/24521855/) that's the result of the instructions in your "wireless script" thread.

---

### Post by wildmanne39 on 2017-05-06
I have never seen this before like that in this file:
> [/etc/modprobe.d/ath9k.conf]
sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
Did you open the file up and paste that into it? You were supposed to run the commands one line at a time in the terminal.

Please do:
```
sudo rm /etc/modprobe.d/ath9k.conf
```
Then:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Just copy and paste one line at a time into the terminal. 

First, check the settings in the router. WPA2-AES (CCMP) is preferred; not WPA and WPA2 mixed mode and avoid TKIP it will make your connection slower. 

Second, if your router is capable of N speeds, A channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz usually works better. 

Most people have better luck with a fixed channel, either 1, 6 or 11, and not automatic channel selection. After making these changes, reboot the router.

Let's set your country code:
```
sudo iw reg set TH
```
```
sudo sed -i 's/^REG.*=$/&TH/' /etc/default/crda
```
Reboot

---

