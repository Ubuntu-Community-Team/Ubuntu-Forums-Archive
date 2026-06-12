---
title: "Netgear WDNA4100 Usb adapter firmware issues (I think)"
date: 2020-12-28
forum: Networking &amp; Wireless
---

### Post by bigmeme2 on 2020-12-28
Since updating, I have been unable to connect to the internet on my desktop. Before the update everything was working fine, but after the update, my adapter's light will not come on, even though my system has detected it and can tell me exactly what it is. When I plug in the usb adapter, the WiFi on/off option comes on in network manager, however there are no connections to select anymore. After realizing that my adapter wasn't working, I peeked in dmesg, and there were a few lines of error outputs from the rt2800 module. My WiFi dongle uses the Ralink 3573 chipset, which is supposed to be supported by the rt2800usb module. I have been searching for solutions on my own, but to no avail. I have booted with an older kernel, but I still experience the same issues. The only conclusions I can draw, are that I am dealing with a corrupted blob (most likely rt2870.bin), or the update changed a WiFi power management config, which may explain why it is unable to grab any signals. I have given the pastebin to the output of the "wireless-info" script: [https://pastebin.com/u4Via01S](https://pastebin.com/u4Via01S). I cannot get a wired connection for my desktop right now, so whatever outputs you need me to grab may take a while.

_**Edit:**_ After changing the value of wifi.powersave via "sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf" I was able to establish a partial connection with the WiFi, but the connection only lasts for about a minute before giving out, then I am back to the same symptoms until I reconnect the adapter a few times or reboot. Also, it now thinks that my chipset is rt3593, however it is rt3573, which is odd, as rt3593 is a pcie chipset, not a USB chipset.

---

### Post by bigmeme2 on 2020-12-31
I would really appreciate some help here.

---

### Post by ActionParsnip on 2020-12-31
If you reboot your router does it help?
Right after the connection drops, open a terminal and run:
```

dmesg | tail

```
What is the output?

---

### Post by bigmeme2 on 2020-12-31
I have been unable to gain a connection again. However, I looked through my package history and saw an update for the linux-firmware package. Could this be the culprit? Should I just downgrade the package and see what happens?

---

### Post by bigmeme2 on 2021-01-01
Rebooting my router does not help either. I hooked up a windows hard drive, and the adapter works just fine on windows. I have only had a similar problem a year and a half ago, when I was using Linux Mint. However, I was able to fix the problem by blacklisting the module and then removing it from the blacklist. I tried to downgrade the firmware on the machine today, and it changed nothing. I think the root cause of this is that the driver is detecting the incorrect chipset, and therefore cannot communicate correctly with my usb adapter. How would I fix this?

---

### Post by bigmeme2 on 2021-01-01
> **ActionParsnip said:**
> If you reboot your router does it help?
Right after the connection drops, open a terminal and run:
```

dmesg | tail

```
What is the output?


Rebooting my router does not help either. I hooked up a windows hard drive, and the adapter works just fine on windows. I have only had a similar problem a year and a half ago, when I was using Linux Mint. However, I was able to fix the problem by blacklisting the module and then removing it from the blacklist. I tried to downgrade the firmware on the machine today, and it changed nothing. I think the root cause of this is that the driver is detecting the incorrect chipset, and therefore cannot communicate correctly with my usb adapter. How would I fix this?

Also, I forgot to quote you in the last reply, sorry.

---

