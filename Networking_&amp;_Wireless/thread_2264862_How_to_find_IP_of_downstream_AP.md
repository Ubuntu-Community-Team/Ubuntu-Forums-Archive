---
title: "How to find IP of downstream AP?"
date: 2015-02-10
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2015-02-10
My internet comes in through a D-Link DIR-655 AP/router which has four ports. Not enough, so downstream from the 655 is a Trendnet TEG-SBOg gigabit switch. One of the 8 switch ports is connected by ethernet to the other end of the house, where I have just plugged in a D-Link DL-624 wifi AP/router.

It is receiving communication from the DIR-655 router and I can access the internet over wifi there (it is a strong wifi signal and should be up to 13 Mbps over the internet, but it is very slow. However the slowness seems to have started before I hooked up the AP there, in fact just after the last android upgrade, so maybe nothing to do with the signal.)

My android phone tells me that the IP# of the 624 AP is 192.168.0.103, but I am unable to access that address in my firefox browser on my Ubuntu linux desktop. So I used the phone to log onto the wifi of the 655 near my desktop to see what it's IP# is, and it is also showing 192.168.0.103.

So I am not understanding something fundamental here. They cannot both be .103, and if either were, I should be able to reach the admin panel at .103 and log in. 

BTW, my internet comes to my house over fiber optic and there is a gateway (is this the right term?) outside my house where the optical is converted to copper digital. Could this be the 192.168.0.103, or is it something else? (it is not the 655 which is at 192.168.0.1)

BTW, what is the correct terminal command to see the IP# of the 655? IFCONFIG shows IP# of this computer as 192.168.0.106, so I deduce that the 655 is 192.168.0.1 (which does take me to the 655 admin panel), but how can I get the computer to tell me using the terminal?

Please walk me through this. Thanks.

Edit: Moderator, 

There does not appear to be much interest in the beginners forum. Would it be a good idea to move it to the networking forum? 

Thanks.

---

### Post by howefield on 2015-02-11
Thread moved to "Networking & Wireless" forum.

---

### Post by Hadaka on 2015-02-11
Hi, the router is controlling the ip address handout.
from a terminal  please do..
```
nm-tool
```
this will show you the ip addres of the computer you issued
the  #nm-tool# command and it will also show the GATEWAY ip address
the GATEWAY address on a usual configuration  is the    *MODEM* ip address.
in your case  modem = 192.168.0.1. The modem will recycle an ip address if it
is not in use. as you saw with 192.168.0.103. Hang out here and read threads,read tutorials
and you will have all this down in no time.

---

### Post by Odyssey1942 on 2015-02-11
Thanks for that most helpful information.

Also how can I find the IP# of the "downstream" AP (i.e., the 624)? I should also mention that I tried to connect the ethernet cable to the 624 through its wan port, but then could not connect wirelessly to the internet through the 624.

Then changed the cable to one of its lan ports and am able to connect wirelessly, albeit slowly.

---

### Post by SeijiSensei on 2015-02-12
Install **nmap** on a Linux box, then run the command
```
nmap -sP 192.168.0.0/24
```
It will ping every address in that network range and report all the machines it finds.

---

### Post by Odyssey1942 on 2015-03-01
Back home again, yippee.

Have used the nmap command and, by unplugging then replugging the cable to the 624 router/AP, have determined that the ip # is 192.168.0.104.

I put that address into a browser, hit enter, and nothing happens.

Is it possible to reach the admin panel of a downstream router/AP? For info, the router has had DHCP disabled and the cable is plugged into one of the four lan ports.

---

### Post by steeldriver on 2015-03-01
Which port (WAN, or one of the LAN ports?) on the DL-624 did you plug to from the switch? the key will probably be to use one of the LAN ports so that **that** device also acts as a dumb switch rather than as a router itself.

---

### Post by Odyssey1942 on 2015-03-01
From your question, I see that I should have written: > For info, the 624 router has had DHCP disabled and the cable from the switch is plugged into one of the four lan ports of the 624, not the WAN port.

I hope these changes will make it easier to answer.

Thanks.

---

### Post by Odyssey1942 on 2015-03-02
When I turned off DHCP, I did forget to change the IP address of the 624 to 192.168.0.99, but ithe 624 seems to work OK with the exception of being slow to load non-mobile enabled web pages on my Nexus 7 tablet. 

However does this have anything to do with not being able to reach the admin panel of the 624 from my desktop?

---

### Post by Odyssey1942 on 2015-03-02
That was it! Changed the LAN setting to 192.168.0.99

Just needed to get the 624 outside the range that the 655 was using. Thanks all for you patience and help.

Finally I must be confusing the 624 with another router/AP that I have been working on in a different city, but I thought that I had found an option to turn UPnP off. The 624 may even pre-date UPnP. Anyway I cannot find it now even after going through every option that I can see.

Does anyone know if the 624 has PnP?

Edit: Found it. From startup menu, click on Tools, then Misc.

---

