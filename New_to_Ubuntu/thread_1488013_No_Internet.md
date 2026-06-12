---
title: "No Internet"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by Tremlett on 2010-05-19
Two nights ago I lost power AND internet, probably due to windy weather. Once the power and DSL was restored, everyone in the house can access the internet but me, who uses Ubuntu 10.4. Everything else works fine, but upon opening Firefox or opera, it's first in offline mode, and after going to online mode, I still can't load any pages.

Resetting the machine and modem/wireless router (which I have hard wired to my box) is to no avail. There's not much to getting the internet to work, so I ran out of ideas quickly.
Ideas?

---

### Post by -Jeremy- on 2010-05-19
Have you checked if you get an IP address? If not, try manually changing your network interface to up and do a dhcp request. If you do have an IP address can you ping any websites?

---

### Post by I8NY on 2010-05-19
well you can try booting off a live cd and test to see if you get internet working that way.  If that doesn't work try wireless and wire connection if you can.  It is possible that the network card/chip died.

---

### Post by gandaran on 2010-05-19
have you checked the network manager icon on the panel (right click it or left click) if network is enabled? 
sometimes simple thinks like this are the cause.

---

### Post by Tremlett on 2010-05-19
Not getting an IP address. Not sure which interface you mean. Under Network Tools>Devices>Network Device? Under that, Loopback Interface is checked.

---

### Post by -humanaut- on 2010-05-19
Try sudo ifconfig eth0 ifup

---

### Post by lkraemer on 2010-05-19
What do you get if you open a Terminal Window and do:
```

iwconfig

```
Post that output

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

So, if my Wifi was wlan0 and my essid was Airlink I would use:
sudo iwconfig wlan0 essid "Airlink"

lk

---

### Post by sandyd on 2010-05-19
Restart the router, ive had it happen a few times (crappy netgear router FTW!)

---

### Post by Tremlett on 2010-05-19
iwconfig gets
lo    no wireless connection
eth0  no wireless connections

ifconfig gets
lo    Link encap:Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU 16436 Metric:1

---

### Post by -Jeremy- on 2010-05-20
If you are on a wire (which I believe you said you are) try doing this:

'sudo ifconfig eth0 up'
'sudo dhclient eth0'  

This should get you an IP address.

---

