---
title: "wifi - Unstable incomming traffic"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by potato4 on 2015-12-21
Hey there,

I've got a little problem with my wifi connection: On the one hand my Ubuntu Client has no problems connecting to the internet (e.g. open a website, ping a device, ...), but on the other hand I can't access it from another PC properly (e.g. connect using SSH, Samba, ...). In some cases (around 60%) I'm able to access it for a limited amount of time, in others I don't even get a ping-response. It seems that it's particularly bad if the Ubuntu Client is in idle.

Some quick information:
```
Ubuntu 15.10 (GNU/Linux 4.2.0-18-generic x86_64)  
    Subsystem: Intel Corporation Wireless-N 7260
    Kernel driver in use: iwlwifi
```
I've also tried an older Version of Ubuntu: There was the same problem

```
$ iwconfig       
     IEEE 802.11bgn 
      [...]       
     Power Management:off
```


Thank you!

---

### Post by praseodym on 2015-12-22
Try deactivating the queue:
```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by potato4 on 2015-12-27
I've tried it over the past three days and sadly it doesn't help at all.

---

### Post by praseodym on 2015-12-28
Please run the wireless-script from the sticky thread and show the outputs.

---

### Post by potato4 on 2016-01-02
Okay, i thought it isn't necessary. Anyway, there it is.

---

### Post by praseodym on 2016-01-02
There are 2 networks with the same ESSID on two different channels, one of them WPA/WPA2, the other one with WPA2 encryption. Are you using a repeater? Choose the MAC-address of the strongest AP and add it as BSSID in the network settings. Choose WPA2 only in your router.

---

### Post by potato4 on 2016-01-16
Yes, there is a repeater and I reconfigured the repeater and my network settings. Now it seems to work fine.

Thank you very much!

---

