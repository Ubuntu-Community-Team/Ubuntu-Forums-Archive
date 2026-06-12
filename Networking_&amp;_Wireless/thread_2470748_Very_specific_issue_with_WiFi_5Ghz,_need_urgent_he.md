---
title: "Very specific issue with WiFi 5Ghz, need urgent help."
date: 2022-01-09
forum: Networking &amp; Wireless
---

### Post by shinoq on 2022-01-09
Hello everyone, 
I run Linux 5.11.0-44-generic/Ubuntu 20.04.3 LTS, today I moved my motherboard from inside ASUS PN50 into Akasa Turing A50 MKII (used also akasa pigtails and antennas for WiFi).
Followed manual and double checked on youtube just to be sure not to make any mistakes. Basically all is in order except one thing. I can no longer connect to 5Ghz WiFi (still can see it though). Tried everything I could find on the web, no luck. I've even removed antennas and was able to connect to 5Gz but on super low signal and bitrate what resulted in no internet at all. If one of the pigtails would not be connected properly there would be no WiFi at all as I understand? I'm desperate for help, below I've pasted details about my wireless card, is it normal  that IEEE standard is not specified? SHows only 802.11
Any help on that matter is greatly appreciated, thanks.

```
lshw -C network
*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 0e
       serial: f0:2f:74:c3:8d:78
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-44-generic latency=0 link=no multicast=yes port=twisted pair
       resources: irq:37 ioport:fc00(size=256) memory:fe918000-fe918fff memory:fe910000-fe913fff
  *-network
       description: Wireless interface
       product: Wi-Fi 6 AX200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 1a
       serial: b0:a4:60:6e:b8:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.11.0-44-generic firmware=59.601f3a66.0 cc-a0-59.ucode ip=192.168.1.132 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:91 memory:fe800000-fe803fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

```
iwconfig:
lo        no wireless extensions.


enp2s0f0  no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"XXXXXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 44:FE:3B:48:13:19   
          Bit Rate=52 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:40   Missed beacon:0
```

---

### Post by TheFu on 2022-01-09
Was the same MB + wifi used in the old whatever?  Is that a new case? I have no clue what "ASUS PN50" into "Akasa Turing A50 MKII" are.  If cases, are they made of the same metal?

5 Ghz doesn't go though walls. Basically, it needs line of sight to connect. Use 2.4Ghz if there is anything between the antennas.  OR better, use wired ethernet which is always better.

Always strive for wired connections whenever possible, even if you need powerline or MoCA 2.5Gbps networking. Connections are just so much better. I connect between 2 floors in the house using an old powerline system. If I were doing it again, I'd use a MoCA 2.5Gbps so that 3+ GigE devices can share the link without any real slowdown.  Plus, wifi has security issues, even the newest standards have security problems, so definitely ensure all the device firmware and drivers are patched for everything wifi.

---

### Post by shinoq on 2022-01-10
Thanks for the reply,
modem is in the same room and in PN50 case it connected to 5Ghz with no problem. Now it started to connect sometimes but bandwidth is severely reduced, to 5Mb/s and keeps reconnecting.

PN50 is a mini form of a PC by asus here is the link:
[https://www.amazon.co.uk/gp/product/B08BLGZZV4/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B08BLGZZV4/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
and Akasa Turing is dedicated case for that mobo to keep temps low as in stock case these can reach 100C+, link to the case below:
[https://www.amazon.co.uk/gp/product/B097B9X67Y/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&th=1](https://www.amazon.co.uk/gp/product/B097B9X67Y/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&th=1)

Thanks for any insight.

---

### Post by hk42 on 2022-01-10
WIFI aerials inside a metal box can give very poor and unreliable results.
If you want to use WIFI I highly recommend using a USB stick at the end of a
USB cable.
Thus it can be moved and you can find a spot with maximum signal from
 the access point and minimum interference from the PC.

---

### Post by TheFu on 2022-01-10
Being in the same room doesn't say whether it has line-of-sight between the 2 antennas or if there are any signal blockers (metal shelving, case, or similar) between the 2 antennas.

---

### Post by shinoq on 2022-01-10
The weirdest part is I had zero issues with stock case, without external antennas :/ What is even more bizzare, when I unscrew antennas, and leave it running only on the pigtail cables, it is connecting and stable but on low signal. These antennas are brand new..,.

Quick update,
just noticed it is working when I will screw in only ONE antenna of two. Is it possible they are interfering each other? how?

---

### Post by jeremy31 on 2022-01-10
Try this, it will disable wifi power management
```
sudo iwconfig wlp3s0 power off
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by TheFu on 2022-01-10
Antennas are a black art.  There is modeling software which gets close for the virtual environment, but then the real world gets involved and screws all that up. There are so many aspects for determining an issue with wifi that are outside our control and nearly impossible to guess through forum posts.  For about 2 yrs, I did over 1200 wifi deployments for an enterprise. We had 3 basic setups but fewer than 20 of those 1200 locations actually worked like we expected.  There was almost always something special in every location that made the wifi less than ideal.  

Initially, I proposed wired connections for all the systems, but the client didn't want the expense. Upper management had this magical idea that as laptops arrived in each location it would magically connect, exchange data, automatically patch, and the end-users wouldn't even know it had happened.  Reality was very different.  They wasted at least a hour a week per employee (25K employees used this) because of wifi, vpn, 2FA, stuff.  The wired infrastructure would have cost them about $10K, 1 time, per location and the employees would have spent 30 seconds a week dealing with their docking ports.  Run the numbers  for 1 yr - which was actually cheaper?  It wasn't their fantasy land.

Wired networking saves frustration, provides better performance, and reduces outside impacts to your network.  To avoid wifi, I have a powerline setup that connects 2 floors of my home. It always works with the expected performance (not the performance on the powerline box, but a solid, expected, amount of bandwidth).

---

