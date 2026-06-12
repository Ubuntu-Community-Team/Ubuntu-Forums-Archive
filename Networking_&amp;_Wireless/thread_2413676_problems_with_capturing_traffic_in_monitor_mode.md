---
title: "problems with capturing traffic in monitor mode"
date: 2019-02-28
forum: Networking &amp; Wireless
---

### Post by alphasneaky on 2019-02-28
I'm running Ubuntu 14.04 LTS (Also, tried with Ubuntu 16.04 and problem repeats). Here is what I want to do:

Put the wireless card on my laptop in monitor mode and capture traffic of other devices in my network. I control the wireless router (access point) to which my and other devices are connected and also these other devices. 

I use the following process to capture traffic in monitor mode:

```
 
sudo airmon-ng start wlan0 (This shows: monitor mode enabled on **mon0**)
sudo tcpdump -ni mon0 -w /var/tmp/wlan.pcap
wireshark -nr /var/tmp/wlan.pcap

```

However, I only see traffic originating from my laptop. Also, that traffic is encrypted. 

I want to know:

1. How do I capture traffic from other devices as well?
2. How to decrypt the traffic: I want to view everything upto the transport layer (TCP sequence numbers, ACK numbers, etc.)

I believe that since I control all the devices in the network (router and other wireless devices) and other devices also have Ubuntu installed on them, there should be some way.

---

