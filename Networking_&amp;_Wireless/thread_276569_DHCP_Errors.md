---
title: "DHCP Errors"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by gnomer_ on 2006-10-13
Hi, I'm having a bit of trouble with "dhclient", "ifup", and "dhcpcd". As you can tell, I've tried almost everything to get DHCP to work. I can get it to work, if I don't make the changes I want to.

I have a Belkin Wireless router, I've shut off all encryption, and everything. I try to spoof my MAC Address with the "ifconfig hw ether 00:01:00:01:00:01", and it doesn't work..I don't know why. It complains that there is no "DHCPOFFER", and no lease.

I know it sounds odd, me spoofing my address. Let me assure you though, It's my own personal Wireless router. I live in the country, the REAL country and am the only one with internet within a miles radius. I've called my ISP, and asked them, and they said they can't help with router problems.

There is no MAC Filter, there is no WEP Key, nothing. It only works for my original MAC..And I want to know why I can't spoof it.

---

### Post by gnomer_ on 2006-10-13
Bump!

---

### Post by spd106 on 2006-10-13
You could try your own with only a simple change, eg increment the last digit. Then go from there.

---

### Post by gnomer_ on 2006-10-13
I did, no luck. Any other suggestions?

---

### Post by spd106 on 2006-10-13
I knew this was possible, but I hadn't tried it before. 

After a little tinkering I've managed to get it working with my atheros based card. I'm using madwifi-ng 0.9.2 compiled from source so the interface tools are available. I also had to download macchanger from the universe repo.

Unsurprisingly I had to delete the ath0 entry in /etc/iftab to allow the use of ath0 with a different mac address.
 
I followed the instructions on [http://madwifi.org/wiki/UserDocs/ChangeMacAddress](http://madwifi.org/wiki/UserDocs/ChangeMacAddress) and it seems to work. I'm can't say whether all drivers support this but you might want to try macchanger.

---

### Post by gnomer_ on 2006-10-13
I also use an atheros chipset and the Madwifi-NG drivers. What you showed me worked execellent, and I thank you.

Many Kudos..

-G

---

