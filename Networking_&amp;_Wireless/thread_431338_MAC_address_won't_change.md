---
title: "MAC address won't change?"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Jawbreaker4Fs on 2007-05-02
I've been attempting to change my MAC address lately, and I've been having mixed results. First of all, I've got MAC address filtering enabled on my router for testing purposes. I add my actual MAC address to the whitelist, attempt to change it, and then see if I can connect. Well, in all cases it seems as though I can always connect! The router seems to still be seeing my original MAC address, despite attempts to change it with both ifconfig and macchanger. Additionally, I just tried to change the MAC address via these means, connect to the router, and check to see if I was assigned a new IP or if there were any new entries in the DHCP client list. No dice! Every time the router still manages to see the original MAC address. Anyone have any thoughts or ideas?

Edit: I've also tried changing the mac address in /etc/networks/interfaces and rebooting as well. That doesn't seem to work either.

Edit: I should also mention that ifconfig is showing the changed address in every case attempted.

---

### Post by netztier on 2007-05-03
> **Jawbreaker4Fs said:**
> The router seems to still be seeing my original MAC address, despite attempts to change it with both ifconfig and macchanger. 

Same problem here: I am not sure, but I believe that after upgrading from Dapper to Edgy, macchanger stopped working. My observations were the same: ifconfig an macchanger believed there was another MAC address than the one my ath0 interface was actually using. I had to use another computer with kismet to see why my connection attempts kept getting refused by the access point.

I have not done any further investigation into this, since I found another way around the problem.

best regards

Marc

---

### Post by Jawbreaker4Fs on 2007-05-03
So you're saying it's probably a version-specific problem with Ubuntu? If I use, say, a knoppix liveCD to change the MAC address and reboot... might that fix the problem? Perhaps even an old Dapper liveCD?

---

### Post by netztier on 2007-05-03
> **Jawbreaker4Fs said:**
> So you're saying it's probably a version-specific problem with Ubuntu? If I use, say, a knoppix liveCD to change the MAC address and reboot... might that fix the problem? Perhaps even an old Dapper liveCD?

I think that this won't "fix" the problem. The MAC address of a card can't be changed - that's why it's called a burned-in address sometimes. A driver or kernel module will read this address upon load and place it at a specific location in memory and/or one of the NIC's registers.

And that's precisely where it will be overwritten when using some special tool like macchanger. The ethernet driver will use that address as source-MAC address when composing the ethernet frames before sendig them out to the media or "physical" part of the NIC, and it will instruct the NIC to listen for incoming frames with that destination-MAC address.

Unless the NIC has some special feature to make this change persistent, this change is volatile and lost on the next reboot.

But just for testing purposes, you might fall lucky with a (liveCD) version of Ubuntu that has a working combination of WLAN driver and macchanger.

best regards

Marc

---

### Post by Jawbreaker4Fs on 2007-05-03
Hmm, doesn't seem like such a thing exists.... is it not a bug that none of these Ubuntu MAC changing utilities seem to be effective? Should I file a bug report on this?

---

