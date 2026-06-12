---
title: "Wireless won't connect"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by Powerade492 on 2010-12-08
I am having trouble connecting my laptop to a wirless netowrk. i have Ubuntu 10.10 Laptop Remix. 

Toshiba Satellite L655

Network Adaptor-Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC
                Microsoft Virtual WIFI Miniport Adapter
Processor-Quad-Core AMD Phenom(tm) 2 P940


Please all help is appreciated. Also i'm not good with commands. So i guess noob explanation would be good.

---

### Post by Amente on 2010-12-08
The reason,that you can't connect to a wireless network is because the driver for the network card is not installed.Some wireless drivers in Ubuntu are not installed by default because they are proprietary. If you can connect your PC to the Internet using a wired network or any other means,here is what you can do Go to System-->Administration-->Additional Drivers(Hardware Drivers).It will automaticaly search drivers for your hardware and helps you install them.Let me know if you can't connect your PC to the Internet.

---

### Post by canucked on 2010-12-09
Powerade492: I replied to your question about getting your wireless working in the other thread you began.

This is what worked for the Toshiba L655 I configured:

In terminal, run:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```

This post further explains issues with that Toshiba laptop:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

---

### Post by lisati on 2010-12-10
Thread closed: see [http://ubuntuforums.org/showthread.php?t=1640945](http://ubuntuforums.org/showthread.php?t=1640945)

---

