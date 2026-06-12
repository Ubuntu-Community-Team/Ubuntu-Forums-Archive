---
title: "Activation: failed for connection. WIFI not connecting"
date: 2021-01-18
forum: Networking &amp; Wireless
---

### Post by sunilraikar on 2021-01-18
Hi,

Whenever i try to connect to wifi network it fails with "Cannot Connect : Activation failure " error message.

Attaching the log as well from the below command:

"sudo tail -f /var/log/syslog"

---

### Post by praseodym on 2021-01-19
Please run the wireless script from the sticky thread and show the ouput

---

### Post by sunilraikar on 2021-01-20
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the ouput

Hi,
Am new to ubuntu and to forum. I could not understand what is "sticky thread" .
Can you please guide me with the steps?.

---

### Post by deadflowr on 2021-01-20
> **sunilraikar said:**
> Hi,
Am new to ubuntu and to forum. I could not understand what is "sticky thread" .
Can you please guide me with the steps?.

I presume this is the sticky thread referred: [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
It's listed at the top of the Networking sub-forum thread posts.
Sticky threads are always on top of the listings for easy to find access.

---

### Post by sunilraikar on 2021-01-22
Please find the attachment containing the output from the sticky thread command

"wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info"

---

### Post by praseodym on 2021-01-22
> ```
wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
The card is turned off. Any button, switch, key or key combo?

---

### Post by sunilraikar on 2021-01-27
> **praseodym said:**
> The card is turned off. Any button, switch, key or key combo?


The normal way to switch on wifi is Fn+F2(in windows) . No other key/switch other than this

Attaching the result and some screen shots again

> 
wlp3s0    IEEE 802.11  ESSID : off/any  
          Mode : Managed  Access Point : Not-Associated   Tx-Power=14 dBm   
          Retry short limit : 7   RTS thr : off   Fragment thr : off
          Power Management : off


---

