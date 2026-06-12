---
title: "Purchased wireless router, could use help configuring it..."
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2007-08-21
I purchased a Netgear wireless router, and it came in the mail today.

Anywhoo, I am hoping to eventually get a wireless network set up with wpa2 encryption, but after reading the sticky in this forum, I've realized I have a lot of learning to do.

So, for now, I'd simply like to go for a very simple configuration, just to make sure the router works.

But, I've never owned a router before, and I have no idea how to even begin configuring the router...

I can download some software from netgear and configure it in windows, but I would prefer to do it directly from Ubuntu.

If anyone can point me in the right direction, an ignorant noob like myself would really appreciate it. 

Thanks!

---

### Post by spd106 on 2007-08-22
You shouldn't need any extra software installed, if you are capable of installing Ubuntu then you are not it's target audience.

All router admin work should really be done using a cable connection, but you might be able to use wireless instead. Make sure your interface is set to DHCP (roaming mode), then once the connection comes up open a Javascript capable web browser (e.g. Firefox) and enter the router's IP address into the address bar, it's usually 192.168.0.1 on a netgear router. If that doesn't work check the manual as it could also be 192.168.1.1 or 192.168.2.1.

The admin pages are quite straight forward, there is usually a wizard to help you. I recommend that you leave ssid/network name broadcast enabled. There should be a glossary to explain the complex terms and acronyms. If in doubt just use the default options to begin with, then research the others later. The two most important things to change, except for the ADSL/Cable settings, are the SSID and the encryption. The SSID should be a unique identifier/name for your network. There's nothing worse than being surrounded by 5+ networks all with the default SSID, 
"... erm, which belkin54g is yours?".

Before you use WPA2 (AES/CCMP) check that your network card and driver support it. Most do these days, but there are some exceptions. Typically you won't need to go through editing the /etc/network/interfaces file, network manager is quite good at WPA. The problems arise when you want to have more advanced set ups with for example two phase authentication or if your connection frequently drops out.

---

### Post by bg1256 on 2007-08-22
Thanks for your help.

I seem to have problems once I attempt to confiure the router via firefox.  I spent a good hour and a half last night trying to get the settings right, but no luck.

The old linksys router that's here is set DHCP, and everything works fine, both wired and wirelessly.

Hoewver, the new netgear shows there is a connection, and I can log into it via firefox (and IE in 'doze), but I cannot get wired or wired connections  to the internet.  

I'm not sure what to try...

---

### Post by spd106 on 2007-08-23
So you are saying there is a problem on the Internet side? Do you have a separate modem or is it built into the router?

---

