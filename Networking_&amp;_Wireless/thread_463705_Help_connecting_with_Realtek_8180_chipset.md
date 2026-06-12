---
title: "Help connecting with Realtek 8180 chipset"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by oranges on 2007-06-03
First of all, here's my tech information:
Ubuntu: Edgy Eft
Wireless Card: Realtek RTL8180L 802.11b MAC
Wireless router: Linksys,  BEFW11S4 V4
Me: Not very sure of what he's doing. :)

I haven't had much problem with my wireless internet for about a year now, but for about four days now it's just been getting more and more frustrating. At first the connection was just choppy, but now it seems to be all but dead. As far as I can tell, I'm getting a connection with my network (about 74-100% signal strength, packages are being sent/received), but I'm... *not* getting a connection, because I can't access the internet regardless. Sporadically, I can load Google, but then it all just goes dead again and I can't figure out why.

I think my problem may be that I'm not connecting directly with my router, but instead piggybacking (?) a connection off one of the other (Windows) computers in the house. I think this because when I access my router's DHCP client list, I see my computer's MAC address, listed with my computer's ip on the network, but the name of one of the other (Windows) computers in the household. That may/may not make any sense at all, and it may/may not have any relation to anything!

Does anyone have any ideas on what I could do to get my happy fun magical internet box working again? If you require any additional information about my system just let me know. :)

---

### Post by cornsnap on 2007-06-04
If you go to "System/Administration/Network" and click properties on your wireless card do you see your access point?

---

### Post by oranges on 2007-06-04
> **cornsnap said:**
> If you go to "System/Administration/Network" and click properties on your wireless card do you see your access point?All that shows me is my interface settings for wlan0, which includes my manually inputed ESSID setting. I don't have anything that gives me a list of access points.

---

### Post by tturrisi on 2007-06-04
turn off the comps.
reset the router.
reboot comps starting w/ linux first.
reconfig router.

---

### Post by chili555 on 2007-06-04
> Wireless router: Linksys, BEFW11S4 V4I have one of these in the garage waiting for hunting season so I can legally discharge my 12-Ga. pump shotgun right in its ugly little LEDs. This is the most unreliable router I have ever owned. It looked like it was connected, but wouldn't actually transmit traffic. I power-cycled it about once a day to get any packets moving. I replaced it with a WRT54G and have never had a single problem.

I rarely suspect hardware, but I will make an exception for this one!

---

### Post by oranges on 2007-06-04
> **tturrisi said:**
> turn off the comps.
reset the router.
reboot comps starting w/ linux first.
reconfig router.What do you mean by "reconfig router"?> **chili555 said:**
> I have one of these in the garage waiting for hunting season so I can legally discharge my 12-Ga. pump shotgun right in its ugly little LEDs. This is the most unreliable router I have ever owned. It looked like it was connected, but wouldn't actually transmit traffic. I power-cycled it about once a day to get any packets moving. I replaced it with a WRT54G and have never had a single problem.

I rarely suspect hardware, but I will make an exception for this one!It often gives me trouble, but up until now it was nothing that time, or rebooting my system or the router wouldn't fix. I can't really afford to throw ~$100 at this problem, though. :(

---

### Post by cornsnap on 2007-06-04
Are you using WEP?

---

### Post by oranges on 2007-06-04
> **cornsnap said:**
> Are you using WEP?No. That is disabled for the moment.

---

### Post by tturrisi on 2007-06-04
> **oranges said:**
> What do you mean by "reconfig router"?It often gives me trouble, but up until now it was nothing that time, or rebooting my system or the router wouldn't fix. I can't really afford to throw ~$100 at this problem, though. :(

Press the router reset button.
This sets the router to default password called "admin"  and default SSID called "Linksys".
Login to router as above and reconfiguire it, meaning set a new password other than the default "admin:" and give your SSID a unique name such as Oranges or MyWlan or MyLastName or 12345ABCD, anything other than the defaults.  If using any security like WEP or WPA, re-do it.

---

### Post by oranges on 2007-06-04
> **tturrisi said:**
> Press the router reset button.
This sets the router to default password called "admin"  and default SSID called "Linksys".
Login to router as above and reconfiguire it, meaning set a new password other than the default "admin:" and give your SSID a unique name such as Oranges or MyWlan or MyLastName or 12345ABCD, anything other than the defaults.  If using any security like WEP or WPA, re-do it.Yes, that would be what I used to do to get it working again, but this trick has since stopped working.

---

