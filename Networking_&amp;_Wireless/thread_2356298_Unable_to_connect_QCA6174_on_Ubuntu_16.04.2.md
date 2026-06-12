---
title: "Unable to connect: QCA6174 on Ubuntu 16.04.2"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by litu-litu on 2017-03-22
Hi,

I'm having trouble connecting to WiFi on an Acer with a Qualcomm QCA6174. I had issues before, with the connection dropping randomly. I moved out and made a clean ubuntu install and the wireless stopped working completely.
 If I leave the network without a password, it connects but I have no Internet. If I enable WPA-PSK, I get the prompt "Authentication required for wireless network" even though I wrote the correct password.[URL="http://pastebin.com/T40wtp29"]

Here's[/URL] the output of the wireless script. 


Thanks!

---

### Post by litu-litu on 2017-03-23
Bump!

---

### Post by jeremy31 on 2017-03-24
You will need to change the wifi router encryption to WPA2-AES, WPA2-PSK or WPA2 only as the results show it doesn't like the mixed mode encryption you are currently using

---

### Post by litu-litu on 2017-03-24
> **jeremy31 said:**
> You will need to change the wifi router encryption to WPA2-AES, WPA2-PSK or WPA2 only as the results show it doesn't like the mixed mode encryption you are currently using

Hi jeremy31, I've already tried changing the encryption method to no avail. Even with the network open I can't get through the internet.

[Here's]("http://pastebin.com/kYx1VrsU") the output of the wireless script with an open network ("no tocar"). It's worth to mention that ethernet works properly in my system and both wireless and wired connections work perfectly under windows.

I saw there's another thread going with the same network adapter and similar problems. Could this be a bug? 

Thanks!!

---

### Post by jeremy31 on 2017-03-24
It could be a bug as I know some people have bought new routers and had no issues.  Are there any settings in the router for WMM/QoS?

```
[   35.567798] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[   35.567800] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
```

---

### Post by litu-litu on 2017-03-24
> **jeremy31 said:**
> It could be a bug as I know some people have bought new routers and had no issues.  Are there any settings in the router for WMM/QoS?

```
[   35.567798] ath10k_pci 0000:07:00.0 wlp7s0: disabling HT as WMM/QoS is not supported by the AP
[   35.567800] ath10k_pci 0000:07:00.0 wlp7s0: disabling VHT as WMM/QoS is not supported by the AP
```


It's an old router indeed (d-link DI-524) and I'm afraid I can't change the WMM/QoS settings.

---

### Post by jeremy31 on 2017-03-24
It probably isn't going to work well with that router as it seems some of them aren't even Wireless-N capable

---

### Post by litu-litu on 2017-03-24
> **jeremy31 said:**
> It probably isn't going to work well with that router as it seems some of them aren't even Wireless-N capable

So the only way to get this working is changing the router for a N capable? Is there not going to be a fix for G routers?

Thanks again!

---

### Post by jeremy31 on 2017-03-24
Either a different router or buy a USB wifi device and disable the Atheros internal device.  A Tp-Link TL-WN722N 150 Mbps that I use should work for you on that older router and it is cheaper

I am sure you could file a bug against package linux [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078) has some info about filing reports

[https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities](https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities) says ath10k drivers only work in AC mode

The card I reccomended uses the ath9k_htc and it works with B/G/N

---

### Post by litu-litu on 2017-03-24
> **jeremy31 said:**
> 
[https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities](https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities) says ath10k drivers only work in AC mode

Weird, since I have a dual boot with Windows and it works just fine there.

---

### Post by jeremy31 on 2017-03-24
You could find the ath10k linux mailing list and ask them

---

