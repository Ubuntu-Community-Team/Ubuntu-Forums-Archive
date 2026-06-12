---
title: "nm-applet w/ bcm43xx 100% signal strength"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by teeljuice on 2007-02-07
I am successfully using my bcm43xx driver with no complaints. Network-manager is working great, iwconfig report normal signal strengths and link qualities. The problem is with the nm-applet. The tool tip report the right % value, however, when I open the applet all the wireless access points show 100% signal strength (or link qualities, not sure what the horizonal bars actually represent).

Any one else see this kind of thing?

Here is the iwconfig output
eth1   IEEE 802.11b/g  ESSID:"dd-wrt"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.457 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level=-60 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:8  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hush on 2007-02-07
mine does the exact same thing, how can we fix this? anyone know?

---

### Post by teeljuice on 2007-02-07
I have seen another post a while ago (I can't find it now) with a picture showing the broken nm-applet. Maybe there is some help there?

If there is, please link to this thread.

---

### Post by kurbacik on 2007-03-14
I'm using Dapper (AMD64) with gnome-network-manager and I have a similar problem. The wireless signal strength is always 100%, regardless. This doesn't respect the true strength of the signal, since sometimes even though the signal is 100% strong, no connection can be established. I have install gnome-network-manager just recently and the program work great except for the minor detail. Any suggestions?

---

### Post by teeljuice on 2007-03-14
No advice from me. I am still dealing with the issue.

---

### Post by kurbacik on 2007-03-15
So far with all the Google searches I've made I haven't been able to figure out a solution. I'm personally running on my HP ZV5000 laptop Dapper AMD64 version using ndiswrapper and a Broadcom 4306 wireless card+windows 64bit driver. Previously I was using wifi-radar but I have just recently switched to gnome-network-manager (version 0.6.2), which is working fine except for this signal strength problem, which makes it difficult to choose the strongest wireless signal. It could be related to the ndiswrapper+broadcom driver combination. I don't feel like changing the driver because besides this signal strength detail everything works perfectly, and even at work network manager works flawlessly (with wpa_supplicant). The connection has never dropped, I have noticed, even over a long period of time. Maybe it should be posted as a gnome-network-manager 0.6.2 bug. The most recent version appears to be 0.6.4, but it is not in the repositories for Dapper 64-bit version yet. I will try to look into this more.

---

