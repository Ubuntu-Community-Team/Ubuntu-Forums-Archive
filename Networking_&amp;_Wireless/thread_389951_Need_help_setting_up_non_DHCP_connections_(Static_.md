---
title: "Need help setting up non DHCP connections (Static IP and VPN)"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Hortinstein on 2007-03-21
I have a Dell 1501 that I configured using the numerous guides and ndiswrapper to get Ubuntu to recognize my wireless card, and I have no trouble at all connecting to any DHCP connection.

However when I got back to school, and tried to connect to my assigned IP in the fraternity using Wifi radar, I cannot do it when I enter the settings.  It says it connects and even shows the IP as connected in Conky, but I cannot do anything (Firefox, Gaim, Updates).  

In windows, under Internet Protocol (TCP/IP) Properties (WIRED CONNECTION)
I use the following up

IP address: 216.9*.2**.10
Subnet Mask: 255.255.255.0
Default Gateway 216.9*.2**.1

DNS (preferred 216.98.2**.1)
DNS (preferred 216.98.2**.3)

And it connects on reboot.

How do I do this with both wired and wireless, and still be able to connect to my network at home which is DCHP.



After I solve this too, it would be nice to know why my pptpconfig was not able to connect to university internet following these instructions: [http://lug.wsu.edu/node/641](http://lug.wsu.edu/node/641)

Any help would be greatful, I dont know too much about networking, but enough to answer any more needed information....i hope

Thanks!

---

### Post by Hortinstein on 2007-03-26
shameless bump

---

### Post by Mr. C. on 2007-03-26
The system doesn't know that in one location it should use static IP information, but in another use DHCP.

You have to configure it for one or the other.  Pick the network interface you will use at school, and enable it, while disabling the other in System->Adminstration->Network.

You can write scripts to allow you to quickly switch.

MrC

---

### Post by Hortinstein on 2007-03-26
yeah i have multiple profiles set up....and i just got the linux user groups help getting it connected to the VPN...and i think the problem might be with my route table 

when i type route it spits out: 

nothing...i think i need to add soemthing in here...just not sure what or how to do it...maybe someone could help me write a script to add proper values, which it what the linux guy did in comp lab

---

### Post by Mr. C. on 2007-03-26
Yes, you must have some routes.  TCP/IP being a packet routing protocol doesn't work without them.

MrC

---

### Post by Hortinstein on 2007-03-26
any idea what the commands are to add these routes....or the values i need to add...I am a little new at this networking stuff

why cant everything be DHCP

---

### Post by Hortinstein on 2007-03-26
ok i just redid route when connected to network and get the following

destination        gateway   genmask             flags    metric   ref    use   iface
216.98.230.0    *             255.255.255.0     U        0         0       0      eth1

---

### Post by Mr. C. on 2007-03-26
I can't possible know what values to add for your routing table.  By default, routes are created when an interface is brought up.  And you will have routes for loopback.  Something you did removed them.

There was nothing in your original post that indicated a VPN - but on a subsequent post this came into the picture.  I can't possibly know what and how your VPN is setup, or what you are trying to accomplish.

Your initial inquiry was about getting your system to work in two different locations.  You can setup profiles to accomplish that.  What's with this VPN stuff now ?  And what have you done to lose your routes ?

MrC

---

### Post by Hortinstein on 2007-03-26
hmmmm

Ok i have gotten the routes back, we removed them in lab to connect to the schools VPN network so that is resolved

the only problem now I think is that I dont have a gateway set when I see the output of route, and I really dont know what to put there.

i would assume its some type of router ip like 198.x.x.x etc, but really not sure.

again this my output for route when connected to my fraternity profile internet

destination gateway genmask flags metric ref use iface
216.98.230.0 * 255.255.255.0 U 0 0 0 eth1


EDIT ok i found my gateway....but when i try to add it to routing table it will not work...it says network unreachable

---

### Post by Mr. C. on 2007-03-26
The default route must be on the same network as your network interface.  In your case, your network is 216.98.230.0/24, your IP 216.98.230.10.  Your default route must be something inbetween 216.98.230.1 and 216.98.230.254.  You'll have to ask your admins for that value.

MrC

---

### Post by Mr. C. on 2007-03-26
> **Hortinstein said:**
> 
EDIT ok i found my gateway....but when i try to add it to routing table it will not work...it says network unreachable

Show data - I can't resolve without data.  Your interpretation doesn't help me see what's wrong.  Show the command you used, and its result.

MrC

---

### Post by Hortinstein on 2007-03-26
Thanks for your help....ill post it when i get home....at library now trying to get my grpahics drivers working with beryl hahha

---

