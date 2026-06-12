---
title: "How do you change the wireless MAC address"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-02-25
Ok, I have 3 questions I need help with;
1) need to change the MAC(hardware address) on my wireless connection(wlan0) im usint a Netgear wg311v3 with ndiswrapper. I can change it fine on the eth0 connection. i did it by running this;
```
ifconfig eth0 down
```

then;

```
ifconfig eth0 hw ether xx:xx:xx:xx:xx
```

then;

```
ifconfig up
```

This worked fine with eth0 connectin. I tried using wlan0 in place of eht0 in the above commands but it still didn't change. any Ideas?

2) My wireless connection is set to not broadcast the SSID . I cant seem to connect when it is set to not broadcast. the connection name is "linksys" I try to connect by running;
```
iwconfig wlan0 essid linksys
```

This works fine when it is set the router to broadcast the SSID any ideas?

3) and also someone said that if you use ndiswrapper, then yopu cant set your card to monitor mode.Is it possible to use monitor mode in windoze if I boot into it? 

please help, Thanks. :)

---

### Post by Mithrilhall on 2008-02-25
Have you tried this? [http://www.alobbs.com/macchanger/](http://www.alobbs.com/macchanger/)

---

### Post by Dwiman89 on 2008-02-25
Coool Ill give that a shot. Do you know if i can pick what MAC i want to use? it looks like thet app provides them. thanks. :)
anyone know about question 2 and 3? thanks

---

### Post by spd106 on 2008-02-25
1. FYI macchanger is in the Universe repo. I've found it quite reliable, though not perfect and it doesn't work with Atheros based cards (see madwifi.org).

2. It's a known issue with many cards/drivers, unfortunately there isn't much you can do. There's no real security benefit anyway and the broadcast signal actually speeds up re-connections.

3. No monitor mode for ndiswrapper yet and it's rather unlikely ever to unless the Windows driver interface starts to provide the facility. I haven't tried monitor mode on Windows, though I have heard that winpcap is needed at some stage. Some kind of driver support will probably be needed too.

---

### Post by Dwiman89 on 2008-02-26
SO im having to use wifi-radar to connect. and I cant et any signal strength or connection information from the network manager in the taskbar. any ideas?
And I figgured out how to kinda use macchanger from terminal but isnt there a way to get this in GUI instead of CLI? I installed the GTK+ one too.

---

