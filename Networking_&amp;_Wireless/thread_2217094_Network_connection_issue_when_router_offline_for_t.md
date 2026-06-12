---
title: "Network connection issue when router offline for too long"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by Jason_Goss on 2014-04-15
Hey all,

New to the forums here and relatively new to Ubuntu.  I have a seemingly simple issue, but I am having a hard time figuring out a way to fix it.

My network is comprised of a lot of components that are running Ubuntu 13.04.  Recently one of the buildings experienced a power outage.  The individual components all came back on when the power came back, but the router did not.  Once the router came back online, only about half of the units got an IP address and started working properly.

My fear is that the networking service attempted to request an IP address for a certain amount of time and then gave up.  

I use /etc/network/interfaces to control my network set up:

```
auto lo
iface lo inet loopback
# The primary network interfaces
auto eth0
iface eth0 inet dhcp
# Example to keep MAC address between reboots
# hwaddress ether DE:AD:BE:EF:CA:FE
hwaddress ether e0:b9:a5:96:20:D1
# WiFi Example
#auto wlan0
#iface wlan0 inet dhcp
#    wpa-ssid "essid"
#    wpa-psk  "password"
# Ethernet/RNDIS gadget (g_ether)
# ... or on host side, usbnet and random hwaddr
iface usb0 inet static
  address 192.168.7.2
  netmask 255.255.255.0
  network 192.168.7.0
  gateway 192.168.7.1



```

Is there a way I can set up script to make the network constantly try to get an IP?  Would I be better off setting the STATIC IP in the device itself instead of using DHCP?

EDIT: Spelling.

---

### Post by SeijiSensei on 2014-04-15
Did the clients not get an address if you rebooted them after the router came back online? 

Is this router a Linux box, or a commercial router?

---

### Post by Jason_Goss on 2014-04-15
After rebooting the devices they got in IP properly. 

It is a commercial router.

---

### Post by SeijiSensei on 2014-04-15
That's pretty much the standard behavior.  Clients try to negotiate with the DHCP server when the network interface comes up, but they give up if they fail to connect.  It's possible that using long leases, say 1-6 months might help alleviate this problem, but you'd need to do some testing to see.

Was the router connected to an uninterrupted power supply?  A single router on a decent UPS will probably stay up for at least an hour and probably a lot longer.  Solid-state routers consume very low amounts of power, certainly compared to full-fledged servers.  My Dell server here can stay up for about half-an-hour on my [APC UPS]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101381") as long as the monitor is not switched on.  A router would remain operative much longer than that.

---

### Post by Jason_Goss on 2014-04-16
That was pretty much the issue. We had a scheduled outage and the UPS was supposed to keep the router (and a lot of other important equipment) up for about 12 hours. It actually lasted about 12 minutes. Then when power was restored the UPS didn't come back on properly. It's a configuration issue there, but I want to avoid having to go to each remote unit to cycle power.

---

### Post by SeijiSensei on 2014-04-16
Twelve hours?  I've never heard of a UPS that comes anywhere close to that. Even the [most expensive products at NewEgg]("http://www.newegg.com/UPS/SubCategory/ID-72?Order=PRICED") report battery durations of under an hour.

I once consulted to an insurance company that built their own UPS with about four dozen car batteries. Maybe that would have lasted a few hours.

---

### Post by Jason_Goss on 2014-04-18
[http://powerquality.eaton.com/Products-services/Backup-Power-UPS/9170.aspx](http://powerquality.eaton.com/Products-services/Backup-Power-UPS/9170.aspx)
Imagine this, with a second tower of just batteries.

---

