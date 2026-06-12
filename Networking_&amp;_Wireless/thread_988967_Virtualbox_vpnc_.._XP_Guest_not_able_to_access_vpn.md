---
title: "Virtualbox vpnc .. XP Guest not able to access vpn through nat"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by stickman77 on 2008-11-21
Hi, 

I've recently installed virtualbox on my ubuntu 8.10 laptop. I connect to a vpn with vpnc and everything is working from that angle on the host. 

To begin with the guest vbox xp machine was also able to access the vpn network and everything was working swimmingly. 

I rebooted my laptop and now the guest xp machine is able to access the internet but is not able to access the vpn network. 

Is there a best practice here.. the guest is set to NAT (which worked originally) ... the host has only one nic eth0. 

I tried the stuff mentioned in the vbox user manual with bridged mode and that also worked of until i rebooted.. at which point neither the host nor the guest could access the internet. So I removed br0 and have rebooted back to normal again but the guest still cant access the vpn network. 

I'm not sure where to start and would greatly appreciate some help. 

Cheers 

also just on a side note i have an issue with screen redraw in seemless mode... I subsequently installed stardock inplace of the windows task bar and this has resolved that issue for me completely. Also looks much nicer.

---

