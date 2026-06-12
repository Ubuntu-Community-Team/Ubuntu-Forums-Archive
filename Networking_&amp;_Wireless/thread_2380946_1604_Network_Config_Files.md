---
title: "16:04 Network Config Files"
date: 2017-12-24
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2017-12-24
Folks,

I've had ongoing problems with WiFi (realtek rtl8821ae) but seem to have found some reliabilty by fixing the IP. Now appears to be working fine.

Am using the default Network-Manager to set up but am puzzled; my wpa_supplicant.conf file shows just one wifi entry and it is not the wifi I connect to.

The entry shown in wpa_supplicant is my access point but network manager actually connects to another access point (not repeater) on my system.

Cannot find which configuration file is used by the system.

Geffers

---

### Post by chili555 on 2017-12-24
I am not sure I see a problem that you are trying to solve here. Perhaps you are asking the question because, like me, you are techno-curious. 

In fact, files are scattered all over the place. In a desktop installation running Network Manager, you are probably most interested in /etc/NetworkManager/system-connections.

There is a lot of automation built into NM based on the assumption that 98% of all users simply connect to a wireless access point and surf the internet. The other 2% who want something more exotic will bypass NM altogether and use /etc/network/interfaces or, most recently, netplan.

---

### Post by Geoff_Lane on 2017-12-24
> **chili555 said:**
> I am not sure I see a problem that you are trying to solve here. Perhaps you are asking the question because, like me, you are techno-curious. 

In fact, files are scattered all over the place. In a desktop installation running Network Manager, you are probably most interested in /etc/NetworkManager/system-connections.

. 

Thanks for prompt reply, techno-curious :P

I've set up numerous Raspberry Pi devices using file interfaces and wpa_supplicant.conf but neither of these make sense with what I am actually connected to.

So, if I set up intefaces and wpa_supplicant.conf will those settings override Network-Manager?

I'm reluctant to fiddle too much as only just got wifi working after about a year of unreliability and relying on ethernet. At the moment if I change an access point on Network manager it disconnects and wifi disappears as an option. Sometimes restarting Network-Manager resolves it, sometimes I have to reload rtl8821ae module, sometimes I have to reboot.

Geffers

---

### Post by chili555 on 2017-12-24
Your default NetworkManager.conf file includes:```
[ifupdown]
managed=false

```Meaning, in a slightly puzzling way, that NM does *not* manage any interfaces that are declared in /etc/network/interfaces. Therefore, if you set up, for example, wlan0 in /etc/network/interfaces, NM will ignore it completely. You will no longer see any indication of available networks or any sign that wlan0 exists. This is sometimes confusing to some new users. 

If you desire, it is perfectly acceptable to use /etc/network/interfaces; just don't expect NM to recognize it afterwards. In other words, use NM *OR* use /etc/network/interfaces but you really can't use both.

If you expect to change access points regularly, manual configuring  /etc/network/interfaces is a pain.

---

