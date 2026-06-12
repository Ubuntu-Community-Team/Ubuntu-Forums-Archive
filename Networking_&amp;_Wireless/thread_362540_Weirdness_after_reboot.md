---
title: "Weirdness after reboot"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by wej1971 on 2007-02-15
Ok, I got a weird one here. It's probably due to my lack of knowledge, but it's still confusing me...

After days trying to get my Belkin USB dongle working, I finally managed it via ndiswrapper and added the following lines to be /etc/network/interfaces: -

iface wlan0 inet dhcp
wireless-essid conexant
wireless-ap 00:0A:E9:02:1F:A6
wireless-freq 2.437G

The last two lines may seem irrelevant, but it never connected to the router using 'ap auto' and  the frequency on the router is 2.437 but the USB dongle seemed to default to 2.412.

Anyway, on restart nothing was working again, so I checked the device and got this: -

wlan0     IEEE 802.11g  ESSID:"conexant"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0A:E9:02:1F:A6   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off

Everything as I left it - I then checked that ndiswrapper was loaded and still set up, and that was fine. I tried everything to get it working again but to no avail, until I started cycling back through the terminal commands history to find out what did it last time. The last two commands I executed before it started working were: -

sudo iwlist wlan0 scan
sudo iwconfig wlan0 ap 00:0A:E9:02:1F:A6

I appreciate that the first simply confirmed that my wireless device could see the router, but why would reconfiguring using the access point address work when this information was already present? Is there another command I could have used to do the same thing (disable and enable perhaps)? Can I put anything in /etc/network/interfaces to do this?

Oh, and I'm assuming that my /etc/modules should look like this, with the ndiswrapper added to the end: -

lp
sbp2
ndiswrapper

A bit of insight/confirmation would be appreciated as I feel I'm going mad!

---

### Post by Floppyjoe on 2007-02-15
> **wej1971 said:**
> Ok, I got a weird one here. It's probably due to my lack of knowledge, but it's still confusing me...

After days trying to get my Belkin USB dongle working, I finally managed it via ndiswrapper and added the following lines to be /etc/network/interfaces: -

iface wlan0 inet dhcp
wireless-essid conexant
wireless-ap 00:0A:E9:02:1F:A6
wireless-freq 2.437G

The last two lines may seem irrelevant, but it never connected to the router using 'ap auto' and  the frequency on the router is 2.437 but the USB dongle seemed to default to 2.412.

Anyway, on restart nothing was working again, so I checked the device and got this: -

wlan0     IEEE 802.11g  ESSID:"conexant"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0A:E9:02:1F:A6   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off

Everything as I left it - I then checked that ndiswrapper was loaded and still set up, and that was fine. I tried everything to get it working again but to no avail, until I started cycling back through the terminal commands history to find out what did it last time. The last two commands I executed before it started working were: -

sudo iwlist wlan0 scan
sudo iwconfig wlan0 ap 00:0A:E9:02:1F:A6

I appreciate that the first simply confirmed that my wireless device could see the router, but why would reconfiguring using the access point address work when this information was already present? Is there another command I could have used to do the same thing (disable and enable perhaps)? Can I put anything in /etc/network/interfaces to do this?

Oh, and I'm assuming that my /etc/modules should look like this, with the ndiswrapper added to the end: -

lp
sbp2
ndiswrapper

A bit of insight/confirmation would be appreciated as I feel I'm going mad!

It should say auto wlan0 before this part:in /etc/network/interfaces
```
iface wlan0 inet dhcp
wireless-essid conexant
wireless-ap 00:0A:E9:02:1F:A6
wireless-freq 2.437G
```

---

