---
title: "wireless security?"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by rax_m on 2007-06-13
Hi 

I've been wondering this for sometime about whether I'm secure enough at home.. 

I have a home wireless network that I've setup that only accepts wireless connections from my MAC address. Do I still need to setup some sort of wireless security like WPA ? 
My feeling is that I don't as the router will ensure that no one else can connect (wirelessly at least). Obviously it's a small pain if someone i know wants to use my wireless connection but I can live with that. 

Anyone have any thoughts?

Thanks
Rax

---

### Post by tgoose on 2007-06-13
It's possible to spoof MAC adresses, and probably to find them by sniffing network traffic. I'd certainly suggest using at least WEP (although of course that's breakable as well.)

WPA would be nice, but I don't consider it essential for home networks, at least while there are so many households with completely unsecured networks. If someone's just looking for free internet, one with both WEP and MAC filtering is not going to be his or her first target. If you can get your wireless card to access a WPA router, turn it on. If not, WEP is passable. But MAC filtering alone is not very secure!

---

### Post by cthesoup on 2007-06-13
MAC address filtering will keep honest people honest, but that's about it.   Changing a MAC address on an interface is trivial.

Here's how I'd mess with you:

I'd use something like Kismet, I am able to see what the MAC address of your laptop is.  I'd wait until you weren't connected some day, and change my wireless adapter's MAC to match yours.  I'd access your WLAN and use your connection to continue to launch attacks against someone else, or maybe just use your bandwidth.

Because you aren't using encryption.. maybe I'd also sniff your network traffic too, and grab the username/password combinations of your router, email accounts etc.  Once in your router, I could add other MAC addresses to give myself further access via an alternate MAC so I could also use something like Nessus to scan your computer for weaknesses.  If I found something, maybe I'd use Metasploit exploit your system.  Maybe you saved your H&R Block tax return on your system and I get enough information to steal your identity.  Maybe I'm just a jerk, and rm -rf from /.  

Use WPA.  Create a strong passphrase.  You own the feature - be responsible and use it.

---

### Post by rax_m on 2007-06-13
Thanks for the replies guys !! 

I'm glad I asked :) 

Will be setting up the WPA first thing tomorrow..  Guess I'll be reading one of the guides soon.

Cheers
Rax

---

