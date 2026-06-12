---
title: "ISP can block Internet connection sharing?"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by ktalinu on 2006-10-31
I spend a week trying to make my ubuntu PC a router for another PC with XP. Nothing seems to work. 

My question is: The ISP can block "Internet connection sharing" ?

I ask than because, in the past I used "Internet connection sharing" option in XP. From some time, the ISP do not permit that any more. 

And I switch to ubuntu to make routing with some SNAT and iptables, .... but no success.

---

### Post by blind0wl on 2006-10-31
If you have it setup correctly, your ISP, should not see any difference, and therefore not know your running ICS.

When you NAT on a Router, you are basically presenting one IP out to your ISP, not several, so theres no way for them to know.

---

### Post by ktalinu on 2006-10-31
But, like I told, "Internet connection sharing" works for a while but now don't work. I call at ISP and they told me "Internet connection sharing" is not permitted anymore. 

How they do that? 
And, trust me, I tryed every method I find in forums to make ubuntu router. With Firestarter (has a internet connection sharing option), Guidedog, and manualy with iptables. 

Nothing works !

---

### Post by netztier on 2006-10-31
> **blind0wl said:**
> If you have it setup correctly, your ISP, should not see any difference, and therefore not know your running ICS.

When you NAT on a Router, you are basically presenting one IP out to your ISP, not several, so theres no way for them to know.

Basically, you are right - but not quite. By carefully scrutinizing the way UDP/TCP source ports are used by your source IP address, it is possible to tell that there might be more than one system "at work". It all depends on how and if your NAT device is rewriting the source ports of the connections flowing through it. 

A lot of operating systems allocate source ports sequentially, sometimes starting in the low 1000's (Windows). Some (AFAIK the some of the BSDs) have a feature to completely randomize the TCP/UDP source port as a security feature.

Source Port allocation strategy is in fact a way to guess what operating system is running. Network scanners like nmap can make edducated guesses based on source port allocation alone.

It is very hard to tell, but it's not impossible to find hints that support the assumption that there is a NAT router at work somewhere. Therefore I think that no ISP is going down that road, unless there's evidence or suspicion of severe net-abuse.
[B]
To the OP:[/B] if in your firewall/NAT configuration (I don't have practical experience with these in Linux) you can find a "randomize source port" feature, enable it. Your ISP *will* have a harder time figuring that one out.

regards

Marc

---

### Post by bionnaki on 2006-10-31
would cloning the mac address help?

---

### Post by ktalinu on 2006-10-31
> **bionnaki said:**
> would cloning the mac address help?

How ? and what's the point?

---

### Post by ScrewItFix on 2006-10-31
hello gays - 
my guess is that your ISP is not really blocking Internet-Sharing. Beside that many ISP prohibit Internet-Sharing in their terms, I never get notice of a case where a ISP blocks the user.

I understand that you have two Computer - one Ubuntu another WinXP ? 
Just make a test - set up the WinXP Computer to share the connection. If that works you know that the Ubuntu-Router is not working correct.

Ubuntu can act as a router, but that doesn't make much sense to me . 
1.The Ubuntu-Desktop must always run to act as a router for the WinXP-Desktop. 
2.The performance of the Ubuntu-Desktop will be reduced.

Todays Hardware-Router are quite cheep, You can get on for 45,- to 80,- Euros. The main advantage ist that you can use Internet with both Computer ( independent ) and that the NAT/Firewall is working correct.

this are my 2 cants – Screw IT Fix

---

### Post by blind0wl on 2006-10-31
Im not gay!!  Cant speak for the other guys :p

---

### Post by drogatoo on 2006-11-14
i have the same problem too
I have a dual boot computer windows XP/Linux with 2 network cards
I have tried ICS in winxp but it doesn't work then i've tried with linux and SNAT but still does not work 

this is the iptables script that i've used

#! /bin/sh
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -F
iptables -F
iptables -t mangle -F

iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i ! eth0 -j ACCEPT

iptables -A FORWARD -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to myexternalipaddress

is something wrong with it?

P.S. I've also installed vmware server in linux and in it windows xp and when i select the network card for the winxp virtual machine to use NAT and share the host ip address everything works fine

---

### Post by Malac on 2006-12-02
I take it you've tried installing dnsmasq and ipmasq.
This worked for me I am now running four pc through my Ubuntu pc.
My ISP has a single use policy but it has never complained.
I'm no expert but as I understand it ipmasq presents just the one ip to the outside world, so no isp would know.

---

### Post by technodigifreak on 2006-12-04
Your ISP may only assign an IP address to a specific MAC address (such as the one machine that was connected to the internet before)  You may have to clone the the old machine's MAC to get the ISP to assign it a dynamic address.  Not sure on the specifics, but that should start you in the right direction.

---

### Post by drogatoo on 2006-12-07
The packets that get routed through my linux box have the same IP and MAC address of my linux box so i think that this is not the problem.
I am wondering how can they block the sharing of my internet connection.
I know one method but I think in my case it does not fit.The method is sending packets with TTL=1 , but I checked , with Ethereal, the TTL of the incoming packets (whom were initiated by connections from the linux box because only from those I get reply) and is somewhere over 100.
Is there another way of knowing that I am sharing my internet connection?

---

