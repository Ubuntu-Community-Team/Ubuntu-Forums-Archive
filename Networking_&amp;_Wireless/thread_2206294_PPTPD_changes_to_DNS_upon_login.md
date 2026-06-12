---
title: "PPTPD changes to DNS upon login"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by petermylward on 2014-02-18
Hi There,

I have a PPTPD VPN server set-up on my Ubuntu Server 13.10 box. I use this box as a media server / file store and general household server. I use the VPN for onward access to US based media sites (HULU, Netflix etc) to which I have a subscription. I have the VPN server set-up using the free ['TUNLR' ]("http://tunlr.net/")service DNS addresses.

This all works fantastically well, and I can switch all my local and remote devices (smartphones etc) onto US based access by connecting to my VPN - job done.

However, I have been thinking about taking advantage of the security benefits afforded by the encrypted VPN connection when out and about on roaming networks, but obviously, if I'm trying to be secure, I don't want to be connecting through 3rd party DNS which I do not trust with personal data.

So here is my question - if I have 2 logons to the VPN - 1 say ustvuser and one say secureuser, is there any event I can listen for which will let me kick off a script to change the DNS settings in /etc/ppp/pptpd-options so I can have less secure US DNS for watching US telly etc, and then a (more)secure ISP based DNS for mail/banking on the move etc, with the DNS addresses being dynamically changed based on login ?

At the moment, I am SSHing into my box before connecting to the VPN and editing the file there - but its not very elegant, and won't do if I get my wife on board with her smartphones etc for security.

Any help much appreciated.

---

