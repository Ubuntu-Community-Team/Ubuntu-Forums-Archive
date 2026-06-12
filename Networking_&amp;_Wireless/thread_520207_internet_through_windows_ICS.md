---
title: "internet through windows ICS"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by stlouis1 on 2007-08-07
well, i'm having a bit of a network problem here

i have a windows xp pro PC sharing a dialup connection and a linksys wrt54g wireless router which hass DHCP turned off, because windows pc is my dhcp server as its running ICS

now i had a d-link router before, and when it had dhcp turned off, the other windows pc's on my network would see the ICS machine right away.

but when i got the linksys and turned DHCP off on the router because my lame self has to share a dialup connection at home. anyway, wheni got the linksys router setup, my windows machines wouldnt recognize my ICS machine. so i came up with a workaround, the windows machines have DHCP as the primary configuration still, but since windows has an alternate configuration option, i set a static ip.

which was a good compromise for my laptop when it was running windows. because didnt have to revert to DHCP when i go out hijacking wireless connections, but when i came home it would work there too

now im running kubuntu on my laptop, and im looking to get it setup the same way basically

i tried to set a static ip on my laptop as well, and when i put the gateway ip, it tells me its not a valid gateway?

i need help, thanks

---

### Post by spd106 on 2007-08-08
Can you give us the settings you have tried? Be sure to check that all IP addresses are on the same subnet.

i.e.  
Windows  ICS -> 192.168.0.1 
Ubuntu            -> 192.168.0.x  (where 1 < x < 255)

both with netmask of 255.255.255.0.

If my memory serves Windows ICS defaults to the 192.168.0.0/24 subnet, so the gateway should be 192.168.0.1, which will also be the DNS server address.

---

### Post by stlouis1 on 2007-08-08
my ICS machine has a 192.168.1.1 ip
my router is 192.168.1.3

theres 3 more desktops on my network that have ip's 192.186.1.4/5/6

theres a vista laptop with a 192.168.1.20

i did manage to get my kubuntu install on my laptop connected last night with a 192.168.1.21 ip though

i set a static ip on the ethernet connection, so i still have DHCP on my wireless, and my laptop mostly sits on a desk at home, but for the odd time i want to lounge on the couch, it defeats the purpose of having a wireless router. i think the setting i missed, the reason why it wouldnt take the 192.168.1.1 as a gateway was  i didnt put it in the route tab

i guess my settings are different since im using kubuntu, i probly have a different network manager. i noticed it does have profile options, i need to play around with it i think, i might be able to compromise with manually switching profiles

but it would be nice to have it automatically do it on its own

---

