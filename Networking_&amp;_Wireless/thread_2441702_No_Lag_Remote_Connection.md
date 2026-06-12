---
title: "No Lag Remote Connection"
date: 2020-04-26
forum: Networking &amp; Wireless
---

### Post by kellymonster25 on 2020-04-26
So im running Ubuntu 19.10 on a Dell Studio with 4GB ram and dual 2.8GHz with like 3 hard drives (basic, do it all server) then connects to google wifi router over powerline Ethernet. It runs a dummy monitor at 1360x768 and runs RealVNC. but then in my bedroom ive got a raspberry pi zero w with raspbian connected over wifi. I use RealVNC, but it tends to lag sometime, no audio, and video playback is basically non-existant. Does anyone have any suggestions? id rather find some software solution than a hard ware solution.

---

### Post by Skaperen on 2020-04-26
software can't improve much over hardware.  but getting the right drivers for the hardware you have is 2nd best after getting better hardware.  how far is the bedroom from the router?  what kind of ping rates are you getting with large packets (1280 or larger) between the machines and out to 8.8.8.8?

---

### Post by kellymonster25 on 2020-05-06
--- 192.168.86.36 ping statistics --- (server)
10 packets transmitted, 10 received, 0% packet loss, time 35ms
rtt min/avg/max/mdev = 29.797/225.643/1111.025/315.229 ms, pipe 2

--- 192.168.86.1 ping statistics --- (Google Wi-Fi router)
10 packets transmitted, 10 received, 0% packet loss, time 24ms
rtt min/avg/max/mdev = 7.169/18.773/57.614/14.453 ms

--- 8.8.8.8 ping statistics --- (only 64 bytes)
10 packets transmitted, 10 received, 0% packet loss, time 23ms
rtt min/avg/max/mdev = 33.547/53.162/75.443/13.997 ms

--- 1.1.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 15ms
rtt min/avg/max/mdev = 41.085/109.081/495.392/129.611 ms

And I tested all of them with 1288 bytes (except Google)
The router is about 50 feet away and with only one set of walls in-between the pi and the router.
But let it be noted that I ordered a rpi 4 w/2GB ram today.... (Might replace the pi zero)

---

