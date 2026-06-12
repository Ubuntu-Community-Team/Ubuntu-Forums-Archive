---
title: "Share files over a wireless network"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by therealtigger on 2008-03-18
Ok,


I have one laptop and one ps3. The laptop connects to a wireless router via ethernet. The ps3 also connects, via wireless. I would like to be able to access media from the laptop through the ps3. Is this possible? and if so, how can I do it? Thank you.

---

### Post by dacorr on 2008-03-18
if i understand the question you have a laptop connected to router via cable and playstation 3 via wireless?

if this is correct they will not see each other because they are on different networks, both need to be wired or wireless.

you could try pinging the playstation private IP from the laptop to be sure but you should get ICMP Destination unreachable. The router will see all devices on the wireless and wired network.

It maybe possible to share files but this would depend on how the PS3 share is configured,

Hope it helps

Dac

---

### Post by Eiríkr on 2008-03-19
Not to burst your bubble, Dacorr, but wired-vs-wireless does not a network make.  ;)  The key is the IP address range.  In my home LAN, I've got two iBooks both connecting via wireless, and two beige boxes and a network printer connected over ethernet cables, and all sharing the same subnet in the [font=courier]192.168.10.XXX[/font] space.  Provided your laptop and PS3 are both on the same subnet (the part like above) and have the same network masks (the network address part that looks like [font=courier]255.255.255.0[/font]), they should be able to at least ping each other.  Whether or not they'll have any sharing software in common that would allow you to do anything useful is a different matter.  :)  

What are you running on your PS3?

Cheers,

Eiríkr

---

### Post by therealtigger on 2008-03-19
hmmm... i did a bit of research and it seems i have to set up my laptop as a "dlna" server . Rythmbox has a plugin for upnp/dlna support or w/e, but when i try and turn it on i get an error message "unable to activate plugin UPnP support

@Eiríkr: running plain ps3 os, but also ubuntu, however, the wireless on ubuntu was broken last time I checked (something to do with a ps3 firmware update)

thanks for the help

---

