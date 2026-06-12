---
title: "Wifi can't get IP unless LAN plugged in first"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by nfox on 2008-03-03
Hi,

I've been setting up my laptops to work with my sexy WRT54G router and have had a time trying to get the IP addresses to assign.

The basics are covered, here's my specs:

Gutsy x86, Vostro 1500 sporting Intel® PRO/Wireless 3945 802.11a/g
Interfaces: eth0 and eth1 (wifi)

Using good 'ol Knetworkmanager, I have my ESSID, KEY, etc. all set up. My router has MAC filtering but allows my laptops. 


Here's the problem:

I cannot get an IP with wifi at all BUT when I plug the LAN in....
The wifi device grabs the IP as it's own and from there, I can unplug eth0 and remain online wirelessly.


How do I fix this?

---

### Post by schmildo on 2008-03-03
Bummer, doesn't look like a simple problem, but certainly interesting...

I've been thinking for a few minutes and i've decided that if it's a configuration error, the problem is with the router's configuration. (or there's some wierdo problem with ubuntu and the router)

Regardless...

The best thing you can do next is find out what's really happening.

I'm thinking that perhaps your wireless connection either isn't sending DHCP requests or the router isn't responding to them... You might find staticly defining your settings for the wireless connection may resolve the issue... but stick with DHCP for the moment.

Install and run 'wireshark' to listen to your eth1 connection (eth0 too if possible).

Post the output here and some clever so-and-so will be better able to help even if I cant.

They'll probably want to see the output of both 'ifconfig' and 'iwconfig' before and after on both interfaces also.

Good luck!

---

### Post by nfox on 2008-03-03
I figured it out. 

Not only was my firewall dropping pings silently causing a timeout with the connection, but somehow eth0 got set as the default gateway instead of eth1 so when the LAN was plugged in, it passed the address to the main interface-- which I had set to eth1 (wifi).



Now it's the next laptop but that's using, I believe, the same card. 
It's an Acer Aspire 5315 and the wifi is detected, ndiswrapper lists the driver and I have wlan0 as the interface. It gets to asking for an IP then timeouts.

Still, after having spent weeks toying with the Wii Wifi USB adapter I was able to trade in a gift with a coupon and got my router for $6.96 so I guess I can spend the extra time.


Anyone with an Acer Aspire 5315 who successfully got their wifi to work, please let me know. The tutorials I found all speak from the point of view that all is working.

---

