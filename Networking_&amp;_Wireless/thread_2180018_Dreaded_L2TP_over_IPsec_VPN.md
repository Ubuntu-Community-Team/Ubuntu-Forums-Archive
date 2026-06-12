---
title: "Dreaded L2TP over IPsec VPN"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by alphaamanitin on 2013-10-11
I have not been able to get the VPN connection for my university to work, at all.  It has directions for Windows and OS X, but unfortunately, my university, in its grand wisdom, does not officially support any non-windows/mac OS.  [Here are the directions for connection using OS X.]("http://www.clarku.edu/offices/its/kb/vpn/clarkvpn_mac10.5.pdf")  If that doesn't work:

It give me the IP address to put in, tells me to use username with domain for my user ID, so domain\username, and of course us L2TP over IPsec for protocols.  Then it gives me the shared secret to use.  I did ```
sudo apt-get install network-manager-vpnc
``` as well was some crappy L2TP over IPsec software and that was just crap.  I have no idea where to put things in in the network manager.  It asks for a group ID and group ID password, what is this? Should this be my domain (the same before my username as previously described) and the group pass the shared secret?  It also asks for a gateway which I am assuming is the IP address mentioned in the mac connection directions.  

I would really like some help.  I need to do this so I can connect to the keyserver on campus and use licensed version of some software that require connection to a keyserver for the full features to be used.  Would it just be easier for me to set up an unauthorized proxy type program on my work computer at school (I am a graduate student and have a computer there) to connect to and get the license that way?

Thanks,

AlphaA

---

