---
title: "Openvpn is leaking dns and using PIA service"
date: 2015-12-20
forum: Networking &amp; Wireless
---

### Post by pavelexpertov on 2015-12-20
Hello, I know there must be other people that faced other issues related to this, but I just I couldn't find one related to my issue.
I have been using privateinternetaccess service, which is great, and I had no issues using it on some places.
However, my parents changed their broadband to sky and got a new router and I checked for DNS leaks (using ipleak.com and dnsleaktest.com)
and I found that I see sky's DNS server. I checked against sky's website and the dns almost matched (first 2 (3-digit) numbers matched) and 
no matter where I tunneled to (i.e. New York and netherlands) I still could see sky's dns address poping up.
I have installed openvpn and its appropriate dependencies to work with the VPN and I would like to get some help if anyone knows regarding the issue and how
to test it as well as fix it.
Thank you and happy Xmas!!!!

---

### Post by sammiev on 2015-12-28
I no longer have 14.04 installed but the newer versions are leaking for a few of us using openvpn.

Not sure what package are causing the issues or if it's from something else.

Every test site I use shows that the dns is leaking. Some sites I can't even post do to the dns changing by the second.

---

### Post by dave205 on 2015-12-28
> **sammiev said:**
> I no longer have 14.04 installed but the newer versions are leaking for a few of us using openvpn.

Not sure what package are causing the issues or if it's from something else.

Every test site I use shows that the dns is leaking. Some sites I can't even post do to the dns changing by the second.

I replied earlier but I wanted to experiment some more.  At the moment I have discovered that I can set the VPN client as a setting on my Asus home router. This of course has nothing to do with Ubuntu and it does not really resolve the DNS leak Ubuntu issue. I did find on the PIA website that they suggest manually setting the DNS servers to their own instead of using the one that is assigned by your ISP.

The problem that I'm encountering is that even if I set the "additional DNS servers" in my pia configuration, Ubuntu still wants to use the DNS servers assigned to it from the home router (which ultimately gets its setting from the ISP).  So far, I cannot find how to manually set the DNS to only the ones I choose and still yet have DHCP assigning IPs.

edit to expand - I found that I can set the IPv4 to "automatic vpn addresses only" which changes the DNS entry window to "dns servers" as opposed to choosing "automatic vpn" which changes the entry window to "*additional* dns servers". 

One would expect that "dns servers" would mean ONLY those dns servers as opposed to the "additional dns servers" which I interpret as adding to the existing assigned dns server (which you would not want as that would defeat the purpose of a vpn.)

---

### Post by dave205 on 2015-12-30
Pavel, 
I was able to find a fix although at this time, I can only get it to work when running openvpn via the command line. I have not found how to configure the network manager to get the leak stopped. 

The fix you need is here - [http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html](http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html) 

The network manager battle I'm dealing with is here - [http://ubuntuforums.org/showthread.php?t=2307975&p=13414596#post13414596](http://ubuntuforums.org/showthread.php?t=2307975&p=13414596#post13414596) 

good luck to you & wish me luck!

---

