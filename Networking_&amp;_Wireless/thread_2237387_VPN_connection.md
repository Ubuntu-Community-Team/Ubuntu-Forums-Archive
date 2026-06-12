---
title: "VPN connection"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by Pepa_Jogurt on 2014-08-01
Hello,

I would like to ask you if is possible to set up 2 VPNs. I am going thru ATT connect to comapny network and thru Aventail I am going to customer network (VPN thru VPN). But only ATT connect create interface TUN0. I am connected on Aventail but I can not see any routing and so on. When I was checking config files I didn't find any option how to create for example TUN1 interface. Do you have any idea how to set up it? 

Thank you in advance.

---

### Post by TheFu on 2014-08-01
Allowing a "split tunnel" is generally considered extremely poor security - I doubt AT&T would allow that in their server-side settings.  Their internal security guys are pretty smart folks.  When I worked there, we did NOT allow split tunnels, at least not for the 65K users in my region that I knew about.

---

### Post by Pepa_Jogurt on 2014-08-01
I see so you think there is not any posibility? If not I will have to use Windows :(

---

### Post by TheFu on 2014-08-01
Windows shouldn't allow it either.  This isn't OS specific - it is tunnel settings controlled by the remote access administrator team. 

I'm not saying anything - I haven't worked at AT&T in ... er ... 7 yrs. They may have changed that policy, but I have doubts. When I worked there, if I'd circumvented their remote access policy, they'd know it and would talk to me - possibly fire me.  OTOH, I deployed remote access for about 20K users, so I would have known better than to risk my job over this convenience.

Let me reread your OP - ok - so if you need access to Aventail for work reasons - tell your manager that and have AT&T provide the tunnel from their network.  Heck, they'll probably setup a dedicated connection and will make the routing trivial for you.

---

### Post by Pepa_Jogurt on 2014-08-02
I am using Windows as virtual machine it is working fine. I trun on ATT and Aventail and it creates 2 virtual interfaces. But I would like use Linux because it is much faster and more comfortable. 

I will ask on that but I don't know I am the only one so it will not be posible but you never know.

Thank you for advice.

---

### Post by TheFu on 2014-08-02
If you didn't hack anything and it works under Windows, then it should work under Linux as well, provided the VPN settings for the different OSes aren't tuned differently on the server side.  I never used ATT-Connect - we were on Nortel or Cisco back then.

So - exactly which VPNs are being used? 
Exactly which routes are needed?
Might be easiest to contact ITO for internal help.

---

### Post by Pepa_Jogurt on 2014-08-02
Problem can be in different version. Because ATT connect for LINUX is from 2007 and I didn't find any new one. 

ATT connect = Version 2.0.1.3003
Aventail = Version 10.60.098

When I start Aventail in the company I receive a let of routes for example subnet: 10.0.0.0/8, 192.168.55.0/24 and so on...

---

### Post by TheFu on 2014-08-02
> **Pepa_Jogurt said:**
> Problem can be in different version. Because ATT connect for LINUX is from 2007 and I didn't find any new one. 

ATT connect = Version 2.0.1.3003
Aventail = Version 10.60.098

When I start Aventail in the company I receive a let of routes for example subnet: 10.0.0.0/8, 192.168.55.0/24 and so on...

So, I've re-read your initial post again - and I don't think I understand it.  I'd assumed you were trying to connect on two different VPNs on two different public internet IPs.  After re-reading, it seems that 1 of the VPNs only works when you are physically inside the office?  Is that correct?

---

### Post by Pepa_Jogurt on 2014-08-02
Yes, when I am in the office I will get let say IP from the range: 7.0.0.0/8 on interface ETH0 and Aventail creates interface TUN0 (private IP range: 10.200.0.0/16) and evrything is working fine. 

but

When I use ATT connect I will get IP from the same subnet (I am connected to comapny network) and It creates interface TUN0. But Aventail doesn't create any interface. I am connected to Aventail but I can not see new interface, routes...

---

### Post by TheFu on 2014-08-02
That's what I feared.
So - running 1 VPN (either of them) works, correct?

That is why I was talking about a "split tunnel." [http://www.tripwire.com/state-of-security/security-data-protection/36th-article-vpn-split-tunneling/](http://www.tripwire.com/state-of-security/security-data-protection/36th-article-vpn-split-tunneling/)  I think that is the only way you'll get this working and it should be prevented by both ATT and the client running Smoothwall.   I know that having multiple tunnels is supported by Linux, but cannot speak for proprietary VPN tools and their capabilities to play-nice with others.

Plus many home routers do not support multiple VPN connections.  I though this was a limit removed a few years ago, but .... I dunno.  I haven't run stock firmware on my routers in over a decade.

---

### Post by Pepa_Jogurt on 2014-08-02
I see, I was searching in ATT connect .sh and .conf files. But I didn't find anything usefull. So last option what I see is used Windows as "gateway" to get in customer network and still use Linux.

---

### Post by TheFu on 2014-08-02
Can't believe I didn't think of this previously - why not run two linux VMs?  
a) ATT-connect
b) Smoothwall

---

### Post by Pepa_Jogurt on 2014-08-02
I have already installed windows in VM because some application are running only in Windows. So the better solution is use windows as proxy server. I have to find how to...

---

### Post by TheFu on 2014-08-02
> **Pepa_Jogurt said:**
> I have already installed windows in VM because some application are running only in Windows. So the better solution is use windows as proxy server. I have to find how to...

That probably won't work - "split tunnel" issue.

---

### Post by Pepa_Jogurt on 2014-08-03
Maybe I can use some proxy solution.

---

