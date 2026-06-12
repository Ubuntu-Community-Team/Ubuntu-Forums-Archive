---
title: "Bluetooth not staying connected Ubuntu 14.04 lts gnome"
date: 2014-07-12
forum: Networking &amp; Wireless
---

### Post by rubensaurus on 2014-07-12
I don't have a bluetooth icon enabled on my taskbar. When I search for bluetooth I can find devices, but when I try to connect to them it just disconnects immediately. I've removed them and started over but I get the same thing. I'm connecting to BT speakers. Any help?

---

### Post by patsev-anton on 2014-07-12
Try blueman
sudo apt-get install blueman

---

### Post by rubensaurus on 2014-07-12
I still get a  "Connection failed: stream setup failed"

---

### Post by rubensaurus on 2014-07-25
ive ran rfkill list to check if there were any blocks, nothing; i also ran rfkill unblock bluetooth and still nothing. 

I can "pair" the device, but when connecting it wont connect.

---

