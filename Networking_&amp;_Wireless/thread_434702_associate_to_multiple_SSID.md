---
title: "associate to multiple SSID"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by aknight_sa on 2007-05-06
hi guys,

is there a way to associate to more than one SSID that are detected by the computer at the same time??

---

### Post by netztier on 2007-05-06
> **aknight_sa said:**
> hi guys,

is there a way to associate to more than one SSID that are detected by the computer at the same time??

No, not with a single WLAN interface. If you find a way to create logical sub-interfaces from your main WLAN NIC, then it might be possible to join different SSIDs at the same time, but probably not when the respective APs use different channels. 

I believe - but I am not 100% sure there - that some Atheros chips provide such functionality.

best regards

Marc

---

### Post by aknight_sa on 2007-05-06
at work, i can detect 3 SSID's which are broadcasted from one AP.. so if the AP can send 3 from the same channel.. why couldn't the WLAN client on the laptop or desktop do the same??...

is it a drawback from the client itself?? or from the OS??

---

### Post by netztier on 2007-05-07
> **aknight_sa said:**
> at work, i can detect 3 SSID's which are broadcasted from one AP.. so if the AP can send 3 from the same channel.. why couldn't the WLAN client on the laptop or desktop do the same??...

is it a drawback from the client itself?? or from the OS??

So do the access points that I maintain at work. And they do so with - guess what - logical sub-interfaces. Each Sub-Interface gets it's own SSID, encryption mode etc. Behind the access point they're mapped into different LANs with different connectivity: Internet for guests, VPN gateway for staff, WAN to a partner company etc. The restriction is the same: you can have multiple sub-interfaces with different SSIDs, but they all have to be on the same channel and they share the bandwith of the physical interface.

So it's about your **driver/NIC/software combination**: it might work if it allows the creation of subinterfaces and their individual configuration, provided all the SSIDs you want to use are on the same channel. If the SSIDs are broadcasted by different APs or different channels, you'll have to use two (or more)  phsyical NICs. 

I think that most WLAN client software doesn't allow for such a configuration via GUI - it's not a mode a user should ever be using - not even Cisco's version of the Atheros GUI for teir Atheros based cards has the notion of a "subinterface". Currently, GNOME's **NetworkManager** in Ubuntu only allows for one active interface among the ones it manages itself. Maybe one of the alternative "WLAN managing tools" (search the forum, there's posts about these) are better in that regard. As a last resort, you can do the entire configuration in **/etc/network/interfaces** manually. 

You will run into difficulty as soon as  it comes to routing, though, what with your system (probably) becoming a DHCP client to multiple networks. Each of the respective DHCP servers is going to dole out a different IP address per WLAN-SSID/subnet your are going to join - which is ok. But it's also going to send **default gateway** information - which will be different for each subnet. So.. which one is your system going to install as first "default route" in the routing table? Same for **name resolution** - dhcpclient is going to get IP addresses of DNS servers from multiple DHCP servers - and they should all go into /etc/resolv.conf - of which there is only one per system. Which entry is going to make it first? Which ones will be overridden by the next? 


best regards

Marc


[SIZE="1"]Lets imagine a setup like this: assume we have a well-encrypted SSID called "company-staff" and a public nonecrypted one called "company-guest". The former gives access to the corporate network, the latter to the public internet, a setup not uncommonly seen today. Now a PC joins both. The guy doing this is even clever enough to configure routing correctly: default route towards the Internet router on the public LAN, and a static route (summarizing the company's IP address ranges) towards the internal router on  the "company-staff" subnet. Now that PC has become a (possible) gateway between an outside and an inside network, bypassing a firewall or crossing the VLAN separation that has been carefully put in place between them. 

No one wants to  imagine the amount of damage a *9-tail whip made out of Cat5 cables *does to a patch of bare skin, so the guy running that PC better **[COLOR="Red"]beware of the network admin![/COLOR]** :twisted: [/SIZE] :-)

---

### Post by aknight_sa on 2007-05-07
well written netz,

i dont really think issue of routing will bother me.. as i have been playing around in the routing tables and was able to fix it up as i like in both linux and windows using one or two NICs... i even had two different subnets on one ethernet card.. and made it work smoothly..

i even got two IPs on one WLAN card.. but my main problem is how can i make it associate to two different SSIDs on the same channel that is...

it seems that its not possible at this time.. maybe someone would write an app that allows that to be done..


i did create sub-interfaces on my card.. and both had an IP.. but only to one ssid..

thanks,

---

