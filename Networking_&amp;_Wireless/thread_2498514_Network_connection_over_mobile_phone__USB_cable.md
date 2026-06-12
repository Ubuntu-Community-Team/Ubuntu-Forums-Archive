---
title: "Network connection over mobile phone / USB cable"
date: 2024-06-17
forum: Networking &amp; Wireless
---

### Post by huggatit on 2024-06-17
I just reinstalled Ubuntu on a NUC 10 and since it’s 3 years since I did it last I can’t remember how to set up internet access over USB cable to my mobile phone.

Clicking top right corner of menu bar it says USB Ethernet connected , menu under that says > set to Wired Connection .

under that I click settings > network , PCI Ethernet is set to off , USB Ethernet settings are ;
IPv4 169.254.123.103
IPv6 address fe80::e159:d566:d8a7: etc etc 
hardware address E2:e159 etc etc 
DNS blank 

The option box under IPv4 has options for automatic DHCP , Manual , Link local only which should I be using ???

connect automatically ticked.

VPN not set

network proxy - automatic 

If I open Mozilla and click on top right > Preferences > scroll to bottom > Network Settings > configure how Firefox connects to the internet > settings > I get options of ;

Configure proxy access to the internet.
No proxy
auto-detect proxy settings for this network.
use system proxy settings
manual proxy configuration

should anything be ticked in the above ?

at the bottom of that page is an option to tick of proxy DNS when using SOCKS v5

any pointers for me ?

:) Thankyou

---

### Post by currentshaft on 2024-06-17
Your phone should provide DHCP for tethering. If not, you'll have to specify a local IP address to connect with.

You don't need to worry about proxy settings in the browser for this.

What phone are you using? What operating system is it running?

---

### Post by huggatit on 2024-06-17
The phone is IPhone 12 with latest v17 ? OS

The phone connected perfectly well as an online service with the settings it has prior to reinstalling Ubuntu , I don&#8217;t recall using an IP address last time I set it up ...

---

