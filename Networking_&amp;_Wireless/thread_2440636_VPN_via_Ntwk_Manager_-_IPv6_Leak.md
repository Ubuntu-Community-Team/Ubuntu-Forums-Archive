---
title: "VPN via Ntwk Manager - IPv6 Leak"
date: 2020-04-13
forum: Networking &amp; Wireless
---

### Post by sgn-gnu on 2020-04-13
Hello there,


Good day to all, I'm new to the forum and mainly newbie to ubuntu, except to shell basic knowledge.

I'm running ubuntu version 19.10. 

Here is the "issue". I use NordVPN through the Network manager and I've been looking around on a lot of forums to find a way to install both a killswitch for VPN, force DNS to NordVPN ones & define a fixed  IPv4 adress.

So I've download some config files from openvpn-nordvpn files, the TCP ones, and added them on the network manager. It worked fine. I also added a fixed IPv4 adress onto the network connection parameters, so as Nordvpn's DNS server. All of it worked fine (I'm having suspens climax here)
Then I followed those advice : [https://github.com/OrangeReaper/abStartupManager/wiki/Some-notes-on-Ubuntu-Desktop-Security](https://github.com/OrangeReaper/abStartupManager/wiki/Some-notes-on-Ubuntu-Desktop-Security) and run the little script then verified the rules.v4 & v6 were set accordingly (by the way I recommend using it it work awesomely). Again no problem, IPv4 well rooted through VPN, killswitch work and so on 

BUT, no way I can have my IPv6 running through the VPN, It always stays the router one, giving the internet world my location & other infos. 
The way I have it temporarily resolved is to deactivate IPv6 services in my router but I'm not quite satisfied,

I'm looking for a way to correct the IPv6 routing to have it through VPN (NordVPN actually support IPv6)


Any idea will be welcome!
Thank you very much for your help :D



Regards & peace,
Solal

edit : adding iptables files screenshot 
[ATTACH=CONFIG]285506[/ATTACH][ATTACH=CONFIG]285507[/ATTACH]

---

### Post by EuclideanCoffee on 2020-04-13
**Note, this is only referenced for security concerns, as this was  moved. Feel free to disregard for the sake of discussion. Thank you.**

This appears to require some support from the vendor. Deactivating ipv6 is the correct way.

Why would you want to use IPv6 anyways? It's less private because it's unique.

Check this out. It says ipv6 is blocked.

[https://www.vpnuniversity.com/learn/should-your-vpn-support-ipv6](https://www.vpnuniversity.com/learn/should-your-vpn-support-ipv6)

---

### Post by The Cog on 2020-04-13
Welcome to the forums, sgn-gnu.

Can you post the output of these two commands:
```
ip -6 rule list
ip -6 route list table all
``` 
Feel free to mangle or redact the actual public IP addresses, it's the rules and routes/metrics I'm looking for.

---

### Post by EuclideanCoffee on 2020-04-13
**Note, this is only referenced for security concerns, as this was moved. Feel free to disregard for the sake of discussion. Thank you.**

Below is what the website says about Nord VPN.

Even if you route IPv6 to bridge IPv4, this will likely cause IPv6 leaks, resulting in a difficult IPv6 configuration that you cannot be sure if it's secure or not (the goal of this forum is to be more secure, please see networking for networking discussions: [https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)).

Bypassing the vendor configurations may result poorly, especially without proper testing.

> 
**NordVPN (Blocks IPv6)**

[IMG]https://cdn.shortpixel.ai/client/q_glossy,ret_img/https://www.vpnuniversity.com/wp-content/uploads/2016/07/NordVPN-logo-square-150x150.gif[/IMG]
**[NordVPN]("https://www.vpnuniversity.com/review/nordvpn") **doesn&#8217;t  support IPv6 but they have built always-on IPV6 leak protection into  their desktop and mobile software. Their solution won&#8217;t route IPv6  insecurely but instead directs it to a [&#8216;black hole&#8217;]("https://nordvpn.com/blog/nordvpn-implements-ipv6-leak-protection/") inside the VPN tunnel.
Essentially  it blocks all IPv6 connectivity without ever exposing your IPv6 address  through leaks. NordVPN is one of our favorite Zero-Log VPN services and  is fully Netflix-compatible (not blocked). Even better, they&#8217;re running  an amazing deal that gets you [2 years of service for under $4/month]("https://www.vpnuniversity.com/go/nordvpn-deal").


An article from NordVPN also states that they block IPv6 in 2019.

[https://nordvpn.com/blog/ipv4-vs-ipv6/](https://nordvpn.com/blog/ipv4-vs-ipv6/)
> 
The majority of VPNs operate on IPv4. This means that  this VPN will redirect your traffic to an external IPv6 DNS server if  you try to access a website that runs on IPv6. Your traffic would exit  its secure VPN tunnel and no longer be secure.
 This would make you susceptible to a DNS leak, which could expose [your original IP address and your location]("https://nordvpn.com/what-is-my-ip/")  or disrupt the service of the website you are visiting. This also means  that your ISP can now monitor your online activity, which defeats the  purpose of using a VPN. Such leaks are hard to detect without using a [DNS leak test]("https://nordvpn.com/features/dns-leak-test/").
 To avoid this, NordVPN offers DNS leak protection. Part  of our solution involves disabling most IPv6 traffic, but NordVPN is  planning to support IPv6 in the future. 



Also more notes from NordVPN.

[https://nordvpn.com/what-is-my-ip/](https://nordvpn.com/what-is-my-ip/)

> 
**Why hasn't IPv6 been fully implemented yet?**

Unlike  the IPv4 protocol, IPv6 won&#8217;t ever run out of unique IP addresses &#8212; it  can provide nearly 3.4×10^38 of them. Furthermore, some argue that IPv6  is a more efficient technology, providing better quality and  connectivity.
However, IPv6 has not been fully implemented for two reasons:
1. IPv6 isn&#8217;t backward compatible with IPv4. You can&#8217;t access IPv4 websites if your device runs on an IPv6 protocol.
2.  It&#8217;s hard to adopt the new technology without immediate gain. IPv4  still suits our needs, and until we reach its limit, a worldwide shift  is unlikely.


More on what the vendor says about IPv6 leaks

[https://support.nordvpn.com/Connectivity/1047408942/How-to-avoid-an-IPv6-Leak-with-NordVPN.htm](https://support.nordvpn.com/Connectivity/1047408942/How-to-avoid-an-IPv6-Leak-with-NordVPN.htm)

> 
 **How to avoid an IPv6 Leak with NordVPN?**

  
   NordVPN has integrated IPv6 leak protection. You can read more about it here: [https://nordvpn.com/blog/nordvpn-implements-ipv6-leak-protection/](https://nordvpn.com/blog/nordvpn-implements-ipv6-leak-protection/)

 Depending on your device and/or network, you can simply disable the  usage of IPv6 altogether - in 99.9% cases it will have no additional  effect on your internet usage - as noted in the section above, IPv6  adoption process is slow, and almost all services allow access through  IPv4.

 **Disable IPv6 in your home network:** You can disable  IPv6 in your network completely by changing your router configuration.  Each router is different, but most have the ability to turn IPv6  completely off - in that case, you won't have to change anything in your  devices. For information how to disable it on your router, consult your  user manual or network administrator. If you are not able to disable it  on the network (for example, when using public networks), you can  disable it on your device instead:

 
 

---

### Post by slickymaster on 2020-04-13
*Thread moved to **Networking & Wireless**.*

---

### Post by The Cog on 2020-04-13
> More on what the vendor says about IPv6 leaks

[https://support.nordvpn.com/Connecti...th-NordVPN.htm](https://support.nordvpn.com/Connecti...th-NordVPN.htm)

sgn-gnu's original post says he still gets IPv6 connectivity through the router. Either he is mistaken or NordVPN's claim of IPv6 leak protection is wrong. 

NordVPN's "How to avoid an IPv6 leak" refers to a claim that they have implemented IPv6 leak protection, and invites you to test that with their IP Leak Test. Their Leak Test just tells you your IPv4 address - nothing to do with IPv6 at all.

---

### Post by EuclideanCoffee on 2020-04-14
I do not want to disagree for the sake of it. Please read the entire article, which I quoted above.

> 
Technically speaking, when establishing an OpenVPN connection, our  clients add additional routes. IPv6 traffic is effectively rerouted to a  &#8220;black hole&#8221; within the device. This feature happens by default on all  NordVPN applications that use OpenVPN, requiring no user action.  IKEv2/IPsec protocol does this automatically. Up next, we plan to tackle  the IPv6 support on our servers &#8211; follow our blog for updates on the  topic.


This black hole functionally disables IPv6 and routes it to IPv4, which is very common.

The IP leak test determines if Nord VPN can detect any immediate leaks, but this cannot be considered a comprehensive test.

---

### Post by The Cog on 2020-04-14
I have read the entire article. It is very plausible. But so is sgn-gnu's claim that he still gets IPv6 connectivity through the router. 
And he's asking for help fixing that. We should at least try to help. And I'm interested in what's really happening.

sgn-gnu also says that NordVPN support IPv6 although NordVPN says they don't, but that's a different issue.

---

### Post by EuclideanCoffee on 2020-04-14
> 
And I'm interested in what's really happening.


Oh, I see.

You say that IPv6 works "through the router." This cannot be "fixed."

IPv6 "leak" is non-issue when using the Internet from a consumer router. ISPs typically provide IPv6 since it's the "future" and it is less expensive. If you are a cellphone user, your ISP will likely always provide an IPv6 to IoT devices such as phones, sometimes because quite literally there aren't enough IPv4 IPs to go around. This is the context to our "issue." Note our original poster also uses quotes, as I believe they are keen to that IPv6 works like this, which is why I didn't bother to provide context. :)

The user cannot change their public IP address, but they want to route all data from private LAN through the VPN via Internet.

The user asked what is the correct configuration for IPv6.

The correct configuration is what was written, to disable it.

This is what the vendor says. If their policy has changed, they would've notified the user base.

It is not incorrect to disable IPv6 because IPv6 packets will not be used to transmit TUN packets. It simply won't be used. And it's not the goal of the user to use IPv6 via the VPN. The user's goal is to use IPv4 strictly.

> 
find a way to install both a killswitch for VPN, force DNS to NordVPN ones & define a fixed  IPv4 adress.


The user is very resourceful. I think they'll find a way to use IPv6, but I want to warn them that all their work then would be wasted if they enable IPv6. Leaks are how people identify a user. If the user wishes to prevent others from knowing his/her IPv6 address (very personal indeed), they indeed are at risk if they have any leak. Simply disabling the IPv6 features on Ubuntu would be the best route. Therefore all IPv6 incoming data would be converted to IPv4 and then likely sent out as such. You won't be able to stop your ISP however from leaking IPv6 as it is configured this way.

A side, the private LAN is likely IPv4.

**The crux: The best way then is to use SOCKS5 from a remote device with a pre-configured IPv4 address and use NordVPN from there. But obviously NordVPN has developed its product to not need such an intervention.**

---

### Post by sgn-gnu on 2020-04-15
Hello to all of you and thank you for your answers, it appears I did not received the mail notif, and I was unaware of your replies, anyway.*



Regarding EuclideaCoffee answers : Thank you very much for your help at first, indeed I read at first an article saying NordVPN was able to route IPv6 through VPN and was protecting them also, but it appears through all the article you've send and more research that I've done that they don't. I guess it explain why my Ipv6 was leaking. 
To be precise, when my IPv4 was VPNed and protected the IPv6 was not and though I did not have any DNS leak or any IPv4 leak, the IPv6 was not protected so the site using it were able to locate me. 
But I don't know whether it is NordVPN not really protecting it or just a misconfiguration from me
I must say I was when posting this concerned about letting IPv6 blocked but reading you and the various article, I ends my concern. So just to be sure, I won't restrict any of internet uses if I just use IPv4 ?

Regarding TheCog answers: I've run the commands you asked and here is the result 

```
ip -6 rule list -->
0:    from all lookup local
32766:    from all lookup main
//// ip -6 route list table all -->
::1 dev lo proto kernel metric 256 pref medium
fe80::/64 dev eno2 proto kernel metric 100 pref medium
fe80::/64 dev tun0 proto kernel metric 256 pref medium
local ::1 dev lo table local proto kernel metric 0 pref medium
local [ip] dev eno2 table local proto kernel metric 0 pref medium
local [ip] dev tun0 table local proto kernel metric 0 pref medium
ff00::/8 dev eno2 table local metric 256 pref medium
ff00::/8 dev tun0 table local metric 256 pref medium

```

I do not understand what it is saying but ... it says it ;)

Regarding you ask about my IPv6 leak, I do have IPv6 connectivity if it is not deactivated on the router setttings or on the computer settings.

I must have mistaken about NordVPN support of IPv6 though.


About EuclidieanCoffee last reply [19 hours ago] 

> **EuclideanCoffee said:**
> Oh, I see.

You say that IPv6 works "through the router." This cannot be "fixed."

IPv6 "leak" is non-issue when using the Internet from a consumer router.  ISPs typically provide IPv6 since it's the "future" and it is less  expensive. If you are a cellphone user, your ISP will likely always  provide an IPv6 to IoT devices such as phones, sometimes because quite  literally there aren't enough IPv4 IPs to go around. This is the context  to our "issue." Note our original poster also uses quotes, as I believe  they are keen to that IPv6 works like this, which is why I didn't  bother to provide context. :smile:

The user cannot change their public IP address, but they want to route all data from private LAN through the VPN via Internet.

The user asked what is the correct configuration for IPv6.

The correct configuration is what was written, to disable it.

This is what the vendor says. If their policy has changed, they would've notified the user base.

It is not incorrect to disable IPv6 because IPv6 packets will not be  used to transmit TUN packets. It simply won't be used. And it's not the  goal of the user to use IPv6 via the VPN. The user's goal is to use IPv4  strictly.



The user is very resourceful. I think they'll find a way to use IPv6,  but I want to warn them that all their work then would be wasted if they  enable IPv6. Leaks are how people identify a user. If the user wishes  to prevent others from knowing his/her IPv6 address (very personal  indeed), they indeed are at risk if they have any leak. Simply disabling  the IPv6 features on Ubuntu would be the best route. Therefore all IPv6  incoming data would be converted to IPv4 and then likely sent out as  such. You won't be able to stop your ISP however from leaking IPv6 as it  is configured this way.

A side, the private LAN is likely IPv4.

**The crux: The best way then is to use SOCKS5 from a remote  device with a pre-configured IPv4 address and use NordVPN from there.  But obviously NordVPN has developed its product to not need such an  intervention.**

I now understand that the correct solution for privacy is to disable IPv6 and I think that is what I will do


Best regards and sorry for the late

---

### Post by The Cog on 2020-04-15
Disabling IPv6 is one way to prevent leaking your IPv6 address, as is switching the PC off and breeding carrier pidgeons.
But before you do, try visiting this site both with and without NordVPN being up: [https://ipv6-test.com/](https://ipv6-test.com/)
As far as I can tell, you don't have an IPv6 default route, so can't connect to anything IPv6 (at least, not while the VPN is up). I'm curious to know why you say you have IPv6 connectivity through the router.

---

### Post by EuclideanCoffee on 2020-04-15
> 
Disabling IPv6 is one way to prevent leaking your IPv6 address, as is switching the PC off and breeding carrier pidgeons.[COLOR=#000000]
[/COLOR]

This is so incredibly rude and off-topic that I'm done responding.

---

### Post by sgn-gnu on 2020-04-15
> **The Cog said:**
> Disabling IPv6 is one way to prevent leaking your IPv6 address, as is switching the PC off and breeding carrier pidgeons.
But before you do, try visiting this site both with and without NordVPN being up: [https://ipv6-test.com/](https://ipv6-test.com/)
As far as I can tell, you don't have an IPv6 default route, so can't connect to anything IPv6 (at least, not while the VPN is up). I'm curious to know why you say you have IPv6 connectivity through the router.



Well now that you say it I've got a bunch of pidgeons for my... No just kidding you had me laugh with that sentence ;) 

Well I've tried it, with & without the VPN result is the same (for IPv6 only of course), it displays my private one as my real location and so on. By side, with VPN it displays VPN IPv4 and without my real IPv4.
Adding to that when IPv6 & VPN are enabled Youtube and other site locating through IPv6 now that I'm in France and when IPv6 is disabled they think I'm in US. 
I must admit I do not fully understand the default route thing but I'm quite sure IPv6 connects to some sites 



Best regards


PS : Thanks for support EuclideanCoffee but I tend to beleive there is more joke in here and potential rudeness is more caused by text discuss without voice and tone than real intention ;)

---

### Post by The Cog on 2020-04-15
Well, I have to admit defeat. If ipv6-test shows you your real IPv6 address then when the VPN is up, then clearly you are leaking, and NordVPN's claim about leak protection is wrong. 
I can't see a default route in your IPv6 routing table though, which puzzles me. I wonder if some javascript from ipv6-test is downloading over IPv4 and then querying and reporting all your addresses. 

If you can spare the time, I'd be very interested to see the output of "ip route get 1122::3344" with and without NordVPN. Again, edit out your actual IP addresses. 
But given the leak and wanting to hide your real address, I think I agree you need to fully disable IPv6, either in the router or in your PC. Disabling it in the router will mean that you get IPv6 connectivity when NordVPN get round to implementing it.

---

### Post by makakanyon on 2021-02-20
More recently, I wanted to use Vpn because of the encrypted connection between the networks. I've also heard that VPNs allow Internet users to keep their privacy. As a result, I started looking for the high quality vpn service that I needed to help me keep my privacy. After visiting various sites, I found the [PinpointVPN]("https://pinpointvpn.com/") platform, which had several reviews of various vpn services. From there, I chose Nordvpn for an encrypted network connection. I also heard that Nordvpn is a quality service, so I decided to use it.

---

