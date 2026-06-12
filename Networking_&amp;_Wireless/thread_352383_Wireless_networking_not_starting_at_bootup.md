---
title: "Wireless networking not starting at bootup"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by IcarusR on 2007-02-03
Hi
I have Edgy installed om my Toshiba Equium A100 laptop. Laptop has Intel PRO/Wireless 3945ABG wireless interface. I have installed the restricted modules & gnome network manager. 
When I boot the Laptop wireless networking does not start. If I left click on NM icon & click on my essid then eventually after 30 + seconds it will connect wirelessly.  
If I boot without network cable connected wireless network will not connect. If I then connect cable & connect over wires, them use NM to connect wirelessly it will connect. 
If I stop NM applet & connect by terminal using 
```
sudo iwconfig eth1 essid <ESSID> channel <CHANNEL>
sudo dhclient eth1
```
Then wireless works perfectly.

How do I get wireless networking to work at boot if network cable is unplugged ?

Thanks

---

### Post by malfist on 2007-02-03
is it set to auto wlan0?

---

### Post by IcarusR on 2007-02-03
I asume you mean in interfaces ? which has auto entries for lo & eth0.

Do I add auto wlan0 to interfaces?

---

### Post by IcarusR on 2007-02-03
Tried adding auto wlan0 to interfaces but when I restart networking I get the following error
```
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

---

