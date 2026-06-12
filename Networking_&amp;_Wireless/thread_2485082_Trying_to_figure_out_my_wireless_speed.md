---
title: "Trying to figure out my wireless speed"
date: 2023-03-19
forum: Networking &amp; Wireless
---

### Post by dorasmith24 on 2023-03-19
I just moved, and here the internet is ATT wireless.  My housemate has no idea what KIND of ATT wireless.   Now, in my old place, wired was 400 to 900 mbps download, 45 upload. 

   Same online tests here give me 23 to 28 mbps download, 5 mbps upload.  

I wonder if the problem is partly signal strength.   So I found a Ubuntu utility to check signal strength.

Using [COLOR=#232629][FONT=ui-monospace]watch -n1 iwconfig in command line, I get,[/FONT][/COLOR]
bit rate=520 Mb/s, Tx-Power=20 dBm, Link Qulality 32/70 to 53/70.   Signal level = -59 dBm.    

Why are the online tests giving me 23 mbps and the command line utility giving me nearly 400 mbps?

Which figure is the signal strength?

Thanks!

Yours,
Dora Smith

---

### Post by chili555 on 2023-03-20
> bit rate=520 Mb/s, Tx-Power=20 dBm, Link Qulality 32/70 to 53/70. Signal level = -59 dBm.

Bit rate is the theoretical maximum speed that is possible, probably in laboratory, clean room conditions. Most of us will, ideally get 60-70% of that.

Tx-Power is the power set in accordance with the reculations of your country. It is impermissable to operate a radio transmitter at high powers, say 10,000 watts (!) at just any frequency. This is so that the military, police, fire, aircraft, et al may safely communicate without interference from your wireless devices. You can increase this slightly, in many cases, by explicitly setting the regulatory domain.

Link quality is just that; on a scale of 1 to 70, how good is the link. Yours appears to be roaming from among the 2.4 gHz and 5 gHz segments of your router. If so, I recommend that you rename the 2.4 gHz and 5 gHz segments of your router; something like myrouter2.4 and myrouter5. Direct your computer to use the 5 gHz segment only.

Signal level is how strong the received signal is. For simple, low-throughput tasks like sending emails, browsing the web, or scanning barcodes, -70 dBm is a good signal strength. For higher-throughput applications like voice over IP or streaming video, -67 dBm is better, and some engineers recommend -65 dBm if you plan to support mobile devices like iPhones and Android tablets. Yours appears excellent!

> My housemate has no idea what KIND of ATT wireless.Does your roommate have administrative priveleges over the router?

---

### Post by scoob8000 on 2023-03-23
One is the connection speed of your wireless connection (theoretical)   What you are seeing online is likely the internet connection.

Can you plug directly into the router and run a speedtest that way?

Also worth noting speedtests can be all over the place depending on where they are hosted.   Ooklas speedtest.net is pretty good about chosing a local server for you.

---

### Post by him610 on 2023-03-25
I always use this site to test mine....
[https://www.speedtest.net/]("https://www.speedtest.net/")

---

### Post by TheFu on 2023-03-25
> **him610 said:**
> I always use this site to test mine....
[https://www.speedtest.net/]("https://www.speedtest.net/")

**Don't confuse local speed with internet connection speeds.**

Locally, I can get 25Gbps between some VM systems (using iperf3). 
Over wired ethernet, I'll see 920-940 Mbps (iperf3), but xfers of real data might be around 650Mbps - due to the speed limit of the storage and whatever xfer protocol is being used.  
Over wifi, I'm lucky to get 50 Mbps. Most of my wifi stuff is old and using a VPN (I don't trust wifi anywhere, even within my network).
My "speed test" for internet is usually about 30 Mbps down and 6 Mbps up.
```
Testing download speed...
Download: 29.60 Mbit/s
Testing upload speed.......
Upload: 5.97 Mbit/s
```

If you don't have a LAN and are directly connecting from the device to your ISP, then you get whatever they provide - best effort.  There are just too many other devices outside your location that impact those connections.  Neighbors, atmospheric conditions, toys, bluetooth devices, cordless phones, all interfere in the same frequencies. There's nothing that can be done besides having a good directional antenna and pointing it exactly at the wifi transmitter/receiver.  In theory, wifi can reach 500M, but in actual practice, people with good antennas have gotten 20km without using professional wifi equipment .... which can get to 150km if line-of-site is possible (think wifi on the top of a mountain).

---

### Post by him610 on 2023-03-25
@TheFu
> Don't confuse local speed with internet connection speeds.
Thanks, I needed that.
After re-reading the OP's initial post, I realized I should not even have posted anything.

---

