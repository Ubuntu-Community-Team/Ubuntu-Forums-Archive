---
title: "going crazy - need to know how to choose WPA"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by expza on 2008-11-13
I'm currently in an area riddled with WPA networks of which I have the passwords too. My house, my work, my PC, everything is WPA. Ubuntu 8.10 Desktop Ed has no problem picking them up but wont let me choose WPA as an option to access the network. It's killing me softly inside. When I change my networks to WEP it works 110%

I've googled to no avail. PLEASE can someone help.

---

### Post by Steve1961 on 2008-11-13
> **expza said:**
> I'm currently in an area riddled with WPA networks of which I have the passwords too. My house, my work, my PC, everything is WPA. Ubuntu 8.10 Desktop Ed has no problem picking them up but wont let me choose WPA as an option to access the network. It's killing me softly inside. When I change my networks to WEP it works 110%

I've googled to no avail. PLEASE can someone help.

This happened with me once too.  My solution was to right-click network-manager, select edit connections, then the wireless tab.  I then deleted the networks shown in the menu and pressed add to manually add the networks I wanted to connect to.

---

### Post by expza on 2008-11-13
Tried doing that, Steve, but it just doesnt connect. It sees the network but doesn't even bother to try connect to it.

---

### Post by Steve1961 on 2008-11-13
> **expza said:**
> Tried doing that, Steve, but it just doesnt connect. It sees the network but doesn't even bother to try connect to it.

Weird, try rebooting your router to see if that helps :confused:

---

### Post by expza on 2008-11-13
Done, no luck.
I don't understand why you simply can't choose WPA when it asks for your network key? :confused::confused:

---

### Post by expza on 2008-11-13
Anyone?

---

### Post by alanqqqq on 2008-11-13
If you have installed wicd as your network manager 

Click on the triangle to the left of the displayed SSID
Chose  Advanced Settings
Check Use Encryption
Chose encryption method from drop-down list and enter key
Click OK

---

