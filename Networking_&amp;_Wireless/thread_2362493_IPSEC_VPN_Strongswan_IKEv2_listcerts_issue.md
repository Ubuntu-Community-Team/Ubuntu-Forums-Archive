---
title: "IPSEC VPN Strongswan IKEv2 listcerts issue"
date: 2017-05-29
forum: Networking &amp; Wireless
---

### Post by zer010 on 2017-05-29
I'm finally getting around to making a roadwarrior style vpn for when I'm out and about with my android phone and such. 
I found this [tutorial]("https://raymii.org/s/tutorials/IPSEC_vpn_with_Ubuntu_16.04.html#Certificates") as pointed to from [Ubuntu's Community documentation.]("https://help.ubuntu.com/community/L2TPServer") 
I installed Ubuntu Server 16.04 on some old laptop I have sitting around, ssh'd into it and got to work.
Everything seems to go smoothly, output checks look like examples, until I get to the last part of 5.0, Certificates, just before Client Certificate.
The last command given is to check if StrongSwan has the private key available with the ipsec listcerts command.
Lo and behold, I don't get the expected output and just get the prompt ready for another command. 
I've pretty much just copy/pasted commands up to this point with the exception of adding the local IP address twice as told to do so.
I've even went and started from the beginning, after strongswan install, and did it all over again, trying to make sure I wasn't missing anything.
Well, I have to assume that I am missing something. Perhaps I'm not pointing to the cert in /etc/ipsec.secrets?
Where should this cert be? 
I've tried looking at another tutorial and while it is similar, I don't see where I might have went astray.
Any help is much appreciated. In this day and age of mobile devices and public wifi, it's weird that something like setting up a home vpn is as "difficult" as it is. 
Privacy and security should be easily available to everyone.
I appreciate any help, tips, tricks or just a lead in the right direction.

---

### Post by zer010 on 2017-06-01
Has anyone been able to check over the guide? Is it the guide that's an issue or am I just not getting it?
I'd really like to move on to the next step or if nothing else, move on to a different solution.

---

### Post by zer010 on 2017-06-05
Nothing yet? I've been thinking that maybe I should just try to tunnel my traffic via ssh. I guess having a vpn at home might afford a few more features, not really sure.

---

### Post by floydwilde on 2017-06-24
I was following the same guide and noticed the same thing.  But after you setup the /etc/ipsec.conf file, as indicated later in the guide with some extra settings (not just defaults), you will see the ipsec listcerts command shows the output you are expecting.

---

### Post by zer010 on 2017-06-25
Ah, that must be what I was missing! Thanks, floyd! I think I could manage from there. 
I eventually just gave up with this method and uninstalled strongswan.
After asking else where, someone called me retarded and kindly linked me 
to this script to install openvpn: [https://github.com/Nyr/openvpn-install ]("https://github.com/Nyr/openvpn-install")
After answering some basic questions and transferring the cert to my phone with openvpn, it all works great. 
Perhaps I'll try the strongswan way again. Maybe it'd be possible to make a similar install/config script.

---

