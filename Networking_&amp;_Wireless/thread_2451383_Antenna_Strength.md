---
title: "Antenna Strength"
date: 2020-10-03
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2020-10-03
There are some commands and utilities that show Access Point signal strength and quality,

```
sudo iwlist scan
sudo iwconfig
```
 and some GUI apps but not sure how one can assess the quality of antenna in WiFi receivers.

Phones, netpads and laptops have antenna built in to motherboard but some USB devices have a nice aerial attached to a USB connector.

Some access points have replaceable aerial offering more gain or directional.

Is there any way of seeing or measuring the quality of the wifi device antenna?

Geoff

---

### Post by hk42 on 2020-10-03
For antenna the simple rule is the bigger the better.
On the receive side the position of antenna far away from interference sources is important.
And a computer is a big source of interference.
One simple test is to compare performance between incorporated Wi-Fi and a good USB dongle
with a long USB cable.

---

### Post by Geoff_Lane on 2020-10-05
On a mobile if you use WiFi Analyzer you can walk around an area and see how the signal changes but that is in relation to Access Points.  I'm guessing clients must have a measurable signal strength too.  Maybe nowadays there are too many clients to make that practical.

Geoff

---

### Post by TygerTung on 2020-10-06
I think a general rule of radio is to have the antennae at 90 degrees to the signal is good, like when you are talking into a walkie talkie to have it going straight up and down. Philosophically, it should be the same for the wifi.

---

### Post by TheFu on 2020-10-06
People get PhDs in antenna design for just 1 frequency.  There are always trade-offs.  Wifi has many different frequencies, so to support those is always a compromise.  Only local testing matters. Design as much as you like, but the local situation and other wifi transmitters at the time matter too.  Sometimes those other wifi transmitters matter just a little and sometimes they matter more than anything else.

Every antenna has a different coverage bubble. Some are omni-directional, bidirectional, or unidirectional.  Just depends on what the vendor decided was best for the expected deployments.  I know that some Ubiquiti APs are omni-directional, so the direction doesn't matter.  Wall, floor or ceiling mount didn't matter. We did a ceiling (via attic) mount because it was the easiest for those locations.  With all-in-one router+wifi devices, we seldom get to place the router in the best location, which is really too bad.

If the connection problem/speed is really that bad, seek a non-wifi solution like powerline ethernet or MoCA Adapters. These non-wifi solutions provide stable bandwidth, unlike bad wifi.  Computers handle stable 60 Mbps better than they handle 300 - 20 - 150 - 10 - 200 Mbps fluctuations.

Around 2005, I did thousands of wifi deployments. What I learned?  Avoid wifi, unless there isn't any other choice. I use powerline ethernet to connect between different floors at home.  1-side connects to the main network switch and the other side connects to a small switch on that level. Wifi is for guest devices and connects to the internet outside my router/firewall. My wifi-only devices either have a USB3-to-GigE ethernet connection or they have to use a VPN to connect into the secured LAN.

With AC and later protocols, wifi performance and the ability to connect more devices has much improved. It really is too bad that the wifi standards group decides on standards before getting some white-hat hackers involved. All the planned standards have security failures. Some are similar to the security failures in the current AC, N, G, A and B standards before. Really too bad that we need a VPN to actually have security over wifi.

---

### Post by Geoff_Lane on 2020-10-30
> **TheFu said:**
>  Only local testing matters. Design as much as you like, but the local situation and other wifi transmitters at the time matter too.  Sometimes those other wifi transmitters matter just a little and sometimes they matter more than anything else.

Every antenna has a different coverage bubble. 

You are so right.  I used a Raspberry Pi recently to create a WiFi router, ethernet connected to powerline adapter and the on board wifi becomes an AP on a different subnet.  My main wifi router is a TP-Link TD-W9970 with pretty large antenna.

Using a laptop in same room as TP-Link wifi if I then do iwlist scan on laptop to get Pi signal strength then on Pi to get TP-Link signal strength strangely the Pi has a better reading, not by much but better.

Probably a lot wrong with the comparison but interesting nevertheless.

Geoff

---

