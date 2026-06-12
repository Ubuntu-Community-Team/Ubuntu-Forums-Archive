---
title: "Partial connection with router"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Pixtu on 2008-11-08
I appear to only have partial connection with my router and hence no internet connection.

New install of 8.10 but NM shows 'no network devices available'

lsusb shows wireless adapter present

Went through a manual process to connect using interface wlan0.

lshw shows the wlan0 interface with associated driver
iconfig shows wlan0 present
iwconfig shows wlan0 present and seemingly connected to router
iwlist scan shows my router and neighbours

However if I try to ping my router it returns with 'Destination Host Unreachable'

And consequently I can't reach any other site on the web.

Any ideas?

---

### Post by gpsmikey on 2008-11-08
You didn't by chance connect to someone else's router did you ??
If you have a wired connection into the router from another machine, you might go in and look at the dhcp clients table to see if it did indeed pass out an address to your machine (assuming you are using dhcp and not a static address).  Just recently, I have noticed I have 3 nearby access points - the house on either side of us and one across the street .... they're everywhere !!!

mikey

---

### Post by Pixtu on 2008-11-08
No no connection to any othe router.

Although we are using DHCP our router is setup to reserve IP addresses for specific MAC addresses, but I couldn't get it to connect automatically, so manually entered the IP address (as if using Static IP).

The only thing that might be strange is that in the ifconfig listing I have an inet address equal to the one I entered, but I also have an inet6 address which to me seems corrupt:
fe00::230:bdff:fe63:4150/64 (followed on the same line with Scope:Link)

---

