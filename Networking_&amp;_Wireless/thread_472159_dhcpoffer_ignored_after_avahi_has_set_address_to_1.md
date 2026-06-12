---
title: "dhcpoffer ignored after avahi has set address to 169.x.x.x"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by rogerjames99 on 2007-06-12
If dhclient already has an old address it will attempt to renew it using a DHCPDISCOVER. If this fails (short timeout) then avahi will set the network addrss to 169.x.x.x. Dhclient will then retry the DHCPDISOVER but this will always fail becuase the DHCPDISCOVER is sent without the DHCP broadcast flag set so the unicast DHCPOFFER is ignored in the ip layer (because the destination ip address does not match). After a random lenght of time/events (which I have not been able to determine); dhclient reverts to sending out a DHCPREQUEST which seems to have a better chance of working since the response is broadcast.

Has anyone else seen this behaviour. Can anyone point me at any relevant informartion. I have "fixed" this by increasing the the lease times on on our wireless network.

Thanlks,

Roger

---

### Post by friendly2004 on 2007-06-13
hey!

am not sure, if i understood it but if then i can at least tell you that i've the same problem...

the last two times even i didn't have a wifi/internet connection inspite of static ip.. but avahi is set..

don't know what to do..

if i find summit to help ya i'll post it here.

---

### Post by rogerjames99 on 2007-06-13
The "fix" I came up with was to dramatically increase the length of time our dhcp server offered ip address leases for. This is not ideal and just minimises the chance of the problem occuring. I have no idea of the circumstances which cause dhclient to revert to sending out DHCPREQUESTs, but as soon as that happens the interface gets set up properly (I don't know if this is beacuse the OFEER is broadcast in that case or the 169 address has been removed from the interface).

This looks like a bug to me. When avahi has set the interface address it should somehow tell dhclient to start setting the "broadcast" flag in any DHCP messages it sends out.

I am a network guy not an ubuintu/avahi expert.

Is there anyone out there who can shed any light on this, or tell me a better forum to post the information in.

Roger

---

### Post by friendly2004 on 2007-06-13
as 4 me i've tried to increase the dhcp lease time.. no success 4 my problem.

---

### Post by rogerjames99 on 2007-06-14
You could try disabling avahi-autoipd by going to /etc/dhcp3/dhclient-exit-hooks.d and editing the zzz_avahi-autoipd file.

Comment out the line which runs /usr/sbin/avahi-autoipd by putting # at the start of it.

This will completely disaable avahi-autoipd which the thing which sets the address to 169.xxx

Roger

---

