---
title: "Wireless card not working anymore...."
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by aznboi on 2005-11-22
darn.... so i tried to connect to my wireless network using my laptop using this thing i got from Add Applications called WiFi Radar, and it has worked before, but now it wont work. I click connect, and it jsut says please wait... and keeps saying that. Could it be becuz of this i entered in b4 and if so how do i undo this?
```
sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99
```

---

### Post by mlomker on 2005-11-23
I doubt that it is related.  Those commands would just cause networking to start later in the bootup process.

---

### Post by aznboi on 2005-11-23
i did becuz when i didnt have an ethernet cable plugged in, on boot up it would stall at Configuring network interfaces.... so i removed it... but about my wifi problem i htink it was just wifi-radar cuz when i used gtkwifi it works, but thnx anyway...:D

---

### Post by mlomker on 2005-11-23
[QUOTE=aznboi]i did becuz when i didnt have an ethernet cable plugged in, on boot up it would stall at Configuring network interfaces.... so i removed it... but about my wifi problem i htink it was just wifi-radar cuz when i used gtkwifi it works, but thnx anyway...:D[/QUOTE]

A more elegant solution is to use **ifplugd**, but if that's working for you then :cool:

---

### Post by aznboi on 2005-11-23
what is it? i did apt-get install ifplugd and it installed. What is it and what do i do with it? thnx

---

### Post by mlomker on 2005-11-24
It detects when an ethernet cable is plugged in and only brings the interface up if it is.  I had a [little write-up]("http://www.ubuntuforums.org/showpost.php?p=368604&postcount=4") for Hoary.  The only difference now is that you need to **sudo update-rc.d -f hotplug-net remove** instead of chmod-ing net.ifup.

It's the best solution for KDE users...gnome users have network-manager which does the same thing and then some.

---

### Post by aznboi on 2005-11-24
ok thnx for the info!

---

