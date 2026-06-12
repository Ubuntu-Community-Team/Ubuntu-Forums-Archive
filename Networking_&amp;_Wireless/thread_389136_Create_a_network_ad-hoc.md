---
title: "Create a network ad-hoc"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by romaluca on 2007-03-20
Is there any tutorial for create a netowork ad-hoc in ubuntu?
Thanks

---

### Post by uterrorista on 2007-03-20
need that info too...
some help will be appreciated.

---

### Post by sythem on 2007-03-20
I'm still new at this but I think this will work. Go into your command line and of course sudo bash to get root permissions. Ok, for example this is mine
```
iwconfig eth1 essid potato mode ad-hoc channel 9 key s:12347 ap any
```
You will have to insert the appropriate fields for yours.
```
 iwconfig device essid yournetworkname mode ad-hoc channel channelnumberhere ap any
```
If you have encryption you have to have this for ancii
```
key s:yourwepkey
```
or this for hex keys
```
key yourwepkey
```
Type this afterwards to ensure the device is enabled.
```
ifconfig device up
```
This will have your ad-hoc network setup. Now you should just have to configure dhcp [here.]("http://www.troubleshooters.com/linux/dhcp.htm")

---

