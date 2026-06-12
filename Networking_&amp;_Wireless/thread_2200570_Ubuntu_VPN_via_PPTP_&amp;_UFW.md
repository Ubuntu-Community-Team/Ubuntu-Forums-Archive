---
title: "Ubuntu VPN via PPTP &amp; UFW"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by david140 on 2014-01-20
Hi all, 

Hope you are well :) 

I am still quite new to Ubuntu and learning new things everyday :) - I have now set-up a VPN server via PPTP but would also like to secure this via UFW.

Would someone be able to help me with the commands required in order to set-this up just for use as a VPN server to allow the traffic in and out?  To my understanding I need Ports 1723 for the VPN Connections itself and also the GRE Protocol (47)?  I would also like to disable PING.

Anything else that I have missed, I would be grateful for any assistance. 

I am even willing to give a small donation for anyones advice that can help me out here...

---

### Post by Lars Noodén on 2014-01-20
UFW a can open or close ports and restrict to or from a specific ip.  So either a port is open or not, on that and on that port there is a service listening there or not.  

If the service is a VPN then you have to have a port open to use it.  If the VPN is PPTP, then it cannot be made secure no matter what you might try.  There was a good article explaining the details from Sept 2012, [i]A death blow for PPTP:
CloudCracker self-experimentation[/i] by Jürgen Schmidt, but you'll have to hunt in an article database to get it or dig it out from Google's cache.  

What you might want instead is [OpenVPN](https://help.ubuntu.com/community/OpenVPN).  It is quite secure and has clients for the platforms you are likely to  be running.   The Server Guide also has [instructions for setting up OpenVPN](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

---

### Post by david140 on 2014-01-20
Thank you, I shall look into this :)

---

