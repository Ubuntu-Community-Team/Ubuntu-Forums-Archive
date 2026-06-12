---
title: "how to renew dhcp lease to my router automatically"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by iwannamarrymiju on 2008-05-21
hi,

i have a d-link ebr -2310 router which is being reset constantly by network attacks . I notice that altho the windows box on my network registers automatically with the router again; the linux box does not register again. however, the network traffic to the linux box seems to pass thru as usual.

what is happening here and why? I would not care except the linux box is running freenet and freenet complains it is not receiving any traffic because of blocked ports. but i am port forwarding the ports I should forward. I think that maybe the failure of the linux computer to reregister prevents the freenet ports from being forwarded.

how can I fix this problem? :confused: thanks

---

### Post by nicedude on 2008-05-21
How did you determine that this behavior is due to "attacks"? and by attacks do you mean wireless attacks or through your ISP's modem you are using ? If you provide the answers to that I can advise you further as to if that is the case and what it means for you.

But in general I think you would be best served by configuring a static route to your router and setting your IP, mask & gateway by hand and also in your router setup if it is supported set the PC in questions mac to always receive this IP, If its not a supported feature of your router then it shouldn't matter as your router should just accept the IP you chose for the PC as long as it is in its range of IP's its set to be providing.

Hope this helps and please answer the questions I pose and I will try to advise you about the "attacks" as well.

nicedude

---

### Post by iwannamarrymiju on 2008-05-21
> **nicedude said:**
> How did you determine that this behavior is due to "attacks"? and by attacks do you mean wireless attacks or through your ISP's modem you are using ? If you provide the answers to that I can advise you further as to if that is the case and what it means for you.

But in general I think you would be best served by configuring a static route to your router and setting your IP, mask & gateway by hand and also in your router setup if it is supported set the PC in questions mac to always receive this IP, If its not a supported feature of your router then it shouldn't matter as your router should just accept the IP you chose for the PC as long as it is in its range of IP's its set to be providing.

Hope this helps and please answer the questions I pose and I will try to advise you about the "attacks" as well.

nicedude

well, by attacks I mean that I receive constant ping of death attacks and syn flooding attacks. my router is wired so I mean thru my ISP. When I setup the connection between the linux box and the router the latter assigns an address. 

I think that the linux box knows all the information you mentioned because when I use the command sudo /etc/init.d/networking restart..I see it list all that information...then it reregisters with the router. So I think this internal address is stable. As I wrote before - the linux box network traffic seems to continue anyway.

---

### Post by nicedude on 2008-05-21
I meant log into your router and stop it from setting an address for your linux box ( ie dhcp ) and instead assign an IP for your linux box, then in your linux network setup put the IP that you set in the router along with the mask ( 255.255.255.0 ) and the gateway (your routers internal IP address ie 192.168.0.1 could be different though). If you do that then you shouldn't ever lose your connection with your router ever. As far as constant ping of death and flood attacks try reseting your external wan IP ( there are allot of ways ) unless you have a static external IP from your ISP which you shouldn't unless you run a website on this connection. If you get a new wan IP and still get attacked constantly I would call my ISP as that is not normal if it happens on multiple IP's as that would mean someone is doing it to their whole network and it is their job to find the offenders and report them and block off the offending traffic.


nicedude

---

### Post by iwannamarrymiju on 2008-05-22
> **nicedude said:**
> I meant log into your router and stop it from setting an address for your linux box ( ie dhcp ) and instead assign an IP for your linux box, then in your linux network setup put the IP that you set in the router along with the mask ( 255.255.255.0 ) and the gateway (your routers internal IP address ie 192.168.0.1 could be different though). If you do that then you shouldn't ever lose your connection with your router ever. As far as constant ping of death and flood attacks try reseting your external wan IP ( there are allot of ways ) unless you have a static external IP from your ISP which you shouldn't unless you run a website on this connection. If you get a new wan IP and still get attacked constantly I would call my ISP as that is not normal if it happens on multiple IP's as that would mean someone is doing it to their whole network and it is their job to find the offenders and report them and block off the offending traffic.


nicedude

ok, thank you. I am trying your advice now. But is it possible the reason that I am being POD/syn floods is because my server is acting as a tor and freenet node? Is there something about how these two networks operate that would make them ping/syn flood so many random ports? or is it possible that foreign goverments are doing this? or am I just being attacked by malicious enemies? my ip address appears to be static altho it is a home connection. my address has remained the same for many months.

---

### Post by nicedude on 2008-05-22
I will try to assist you in this matter via PM's so please respond to the one I send you.

---

