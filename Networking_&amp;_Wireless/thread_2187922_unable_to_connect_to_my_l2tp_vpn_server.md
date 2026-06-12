---
title: "unable to connect to my l2tp vpn server"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by sylvandacunha on 2013-11-14
Dear All,

I do apologize for this post if its off topic but guess there will be someone to help me out as i was trying to get some help and advice googling or in other forums but nothing yet.

we have a corporate network and right now i have a pptp linux server and our users access our local network private ip servers from home through internet and its working perfectly with no issues.

but due to the severe security issues with pptp protocol i tried to a secure one choices being openvpn,openswan, strongswan etc.

I want a clientless vpn so i decided to use openswan.

I did setup openswan but has been just struggling to get it working perfectly.

1) i would like to know if i can use openswan in this case .. i do presume i can

2) the issue i am facing for almost a week is that

after setting up openswan i tried from my office win7 pc having a private ip and I could connect to the openswan vpn server and everything was working fine.
the openswan vpn server has a public ip and is not natted 
the vpn server and my office pc is on different Vlans.

now i tried to test it from my home pc and i could never connect .
googgled around and changed the conf files as per different examples but still no luck.

my home pc has a private ip and is natted on my dsl router to my ISP public ip

now i would like to know where i could be wrong 
if also some one could help me with a link. and also if someone can point to me where i need to troubleshoot that is
the ipsec level , or xl2tp or ppp level. i think the firewall should not have issues
cause most links have config examples where the vpn server has a private natted ip
i can post the config and error messages if required 

really would apprecite your kind help and please appreciate and let me know if you would like more details


regards

simon

---

### Post by r1ckh on 2014-02-09
Hi Simon, I know this is a very late reply and maybe a stab in the dark (hopefully this may help someone else). 
However, it might be worth checking the firewall settings on your home router as - depending on the make/model - a lot have default policies that block VPN packets. For instance I have seen a Netgear where you have to allow (separately) PPTP pass-through, IPSec pass-through depending on what type of VPN you are using.

Regards,

Rick

---

