---
title: "Interface not accepting DHCP IP?"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by Bogaurd on 2006-10-13
Hi guys,
I'm trying to setup a connection that my isp offers: basically I have ppp0 as my PPPoE connection to the internet, getting a WAN IP. The modem then has another bridge connection, which will assign an IP to the interface the modem is connected to via DHCP - a 10.x IP, this is for a sort of 'local lan' that my ISP allows me to use with other users in the same area as me.

The problem I am having is that when i try to get an IP on the interface (eth1), I'm having this problem:
```
terry@jupiter:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:e0:4c:31:3c:dc
Sending on   LPF/eth1/00:e0:4c:31:3c:dc
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPNAK from 10.25.15.254
DHCPACK from 192.168.1.1
SIOCSIFNETMASK: Cannot assign requested address
SIOCSIFBRDADDR: Cannot assign requested address
SIOCADDRT: Network is unreachable
bound to 0.0.0.0 -- renewal in 65190 seconds.

```
192.168.1.1 is the IP of the modem, running in bridge mode. The funny thing is, it worked perfectly yesterday, then i rebooted the box, and now it's failing to assign an IP! 

Does anyone have any idea why this might be happening? It looks like it's being offered an IP... but just not assigning it.
Thanks!

---

### Post by wieman01 on 2006-10-13
Have you installed a firewall configuration tool such as Firestarter in the meantime?

---

### Post by Bogaurd on 2006-10-13
No... I havent.
I run arno's IPtables firewall script, could this possibly have anything to do with it?
Edit: I should add that I have always run arno's firewall script... and this seemed to be working fine yesterday :S

---

### Post by wieman01 on 2006-10-13
> **Bogaurd said:**
> No... I havent.
I run arno's IPtables firewall script, could this possibly have anything to do with it?
Oh yes, very likely. Could you disable IP tables for a minute & try again? It's likely that this is the issue. If this works, I'll let you know which ports you need to open.

---

### Post by Bogaurd on 2006-10-13
Hmm - is there an easy way to disable IPtables as a whole?

---

### Post by wieman01 on 2006-10-13
> **Bogaurd said:**
> Hmm - is there an easy way to disable IPtables as a whole?
Mmm... Don't use them because I am running Firestarter which does that for me. But you for sure know what you have done to "enable" it, right? Could you reverse that?

---

### Post by Bogaurd on 2006-10-13
hey wow!
I removed all iptables rules, and it worked!
where shall i go from here?

---

### Post by wieman01 on 2006-10-13
> **Bogaurd said:**
> hey wow!
I removed all iptables rules, and it worked!
where shall i go from here?
Yes, fell into the same trap a while ago when I installed Firestarter. :-) Pretty common problem.

You need to open these ports:

1. Port 80: HTTP (Internet)
2. Port 443: HTTPS (secure Internet)
[COLOR="Red"]3. Port 67-68: DHCP (network connection)[/COLOR]

If you need help with the script, then post the contents & I'll see what I can do.

---

### Post by Bogaurd on 2006-10-13
thankyou very much :)
I'm just at work here, i'll be home in an hour or two, i'll have a shot at doing that then.

---

### Post by wieman01 on 2006-10-13
> **Bogaurd said:**
> thankyou very much :)
I'm just at work here, i'll be home in an hour or two, i'll have a shot at doing that then.
No problem. I'll keep an eye on the thread. :-)

---

### Post by Bogaurd on 2006-10-14
ok, i'm home now, and trying to get this working. I've opened the ports in the firewall config... but it's being very difficult and not working very well. I'm still getting that error most of the time. DHCP is udp or tcp?

---

### Post by wieman01 on 2006-10-14
If you don't mind upload the script. I usually open both TCP & UDP. 

What exactly is not working well? Do you get error messages?

---

### Post by Bogaurd on 2006-10-14
Ok, here's the script:
[http://pastebin.ca/202224](http://pastebin.ca/202224)

And here's the config file:
[http://pastebin.ca/202228](http://pastebin.ca/202228)

The problem i'm having is that when i try to do dhclient eth1, it fails. I can only get an IP on eth1 if i bring down ppp0 first, bring down eth1, and then bring it up. I'm guessing this means the interface will die once the lease expries...

---

### Post by wieman01 on 2006-10-14
Oh... This is a tough one. Since I am not using 'PPP' I am not sure if I am the right person to talk to I reckon. 

Is PPP using a dedicated port perhaps? Or does rebooting the modem help (seen this before)?

---

### Post by wieman01 on 2006-10-14
Since the troubles starting after you had configure your firewall I suspect this has something to do with other ports.

---

### Post by Bogaurd on 2006-10-14
I've juest added bits in to try to get it to work, so thats why its pretty messy (the config file). :)

---

### Post by Bogaurd on 2006-10-14
Hmm, i'm having a play with it now, i'll let you know how I go!
Thanks for your kind help! :D

---

### Post by wieman01 on 2006-10-14
> **Bogaurd said:**
> Hmm, i'm having a play with it now, i'll let you know how I go!
Thanks for your kind help! :D
No problem. Sorry I cannot say more than that. But it definitely has to do with the firewall. So you're on the right track. 

BTW: I you want to avoid such troubles, I can recommend "Firestarter" which is a tool that makes use of IP Tables but furnishes you with a nice little GUI. I attached an image of Firestarter, perhaps it's worth a shot. You'll find it in the repositories.

---

### Post by Bogaurd on 2006-10-14
I seem to have it working for the mostpart :)
I would use firestarter... but the box has no GUI or monitor/input devices :)
Can firestarter run headless?

---

### Post by wieman01 on 2006-10-14
I see... yes, Firestarter can be run without a GUI. You would have to configure it through text files in that case. So that kind of defeats the purpose of it I guess. ;-)

---

