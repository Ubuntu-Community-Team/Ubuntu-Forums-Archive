---
title: "Static IP for Wireless Machine on More than one Network"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by hnaamyilkemku on 2007-07-29
(Also posted in the beginner's forum, since I'm  still a beginner :))
Hello,

I want to set up a static IP on my laptop so I can use domains for file sharing between this computer and a windows machine at home. At the same time, I use my laptop on other networks (primarily at work), so I don't want my computer to demand a static IP address from those networks. How can I set this up? As far as I understand, I can edit /etc/network/interfaces to make the wlan static with the address I want, but I don't know if this implies that my computer will always want a static ip for the wireless connection. All insight appreciated!

---

### Post by spd106 on 2007-07-30
Is there any particular reason for wanting a static address?

Usually the way to solve this is by using DHCP both at home and at work. As long as your laptop can get an IP address on both networks you can resolve it by hostname for most networking applications.

There might be a way that you can do this via wpa_supplicant as it allows multiple network settings in the .conf file. It's mainly used for configuring encryption, but I think it could be used to set addresses too. The wpa supplicant website has more details, also see the Wireless security WPA etc. sticky.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

### Post by jediborger on 2007-07-30
You can solve this problem by creating a separate profile for your Network setup. Goto System-Administration-Network. Set up your settings for Home, then click the save icon in the upper right hand corner, call it Home. Then change the settings and save it as Office. Now you'll have two locations in the drop-down menu. Select one and click the green arrow to the right of the box. That should solve your problem.

---

