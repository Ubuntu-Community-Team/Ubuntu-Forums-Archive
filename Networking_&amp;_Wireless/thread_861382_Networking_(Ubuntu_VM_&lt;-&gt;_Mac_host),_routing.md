---
title: "Networking (Ubuntu VM &lt;-&gt; Mac host), routing issue"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by ZacharyPruckowski on 2008-07-16
OK, so I have an Ubuntu VM (CLI only, no X Server) running in Parallels on my Mac.  I can't get the two to connect, and I'm fairly sure it's a network issue, not a Parallels issue.  I have set up IP aliases on the Linux and on the Mac in the same subnet (172.16.12.101 and 102), but I don't know how to set up the routing (I get a "no route to host" going both directions).  They're both aliased on the same device (en0 and eth0, which should be the same Ethernet port), so do I just do:

Mac: route add -net 172.16.12.102 netmask 255.255.255.0 en0
Linux: route add -net 172.16.12.101 netmask 255.255.255.0 eth0

Or do I need to use a gateway address?  A complication is that I don't have a cable plugged in to that port because I have no networking at home (but I do at college).  So I assume I need to set it to ifconfig up on boot?

Thanks in advance for any help.

---

### Post by ilrudie on 2008-07-16
Is parallels setup bridged or NAT? Can you ping the router on the linux box?  Can you ping google on the linux box?

---

### Post by ZacharyPruckowski on 2008-07-16
> **ilrudie said:**
> Is parallels setup bridged or NAT? Can you ping the router on the linux box?  Can you ping google on the linux box?

It's set up as bridged at the moment.  I can switch to NAT if you think that'd help.

I have no external router.  As I said in the first post, I have no networking to any other box whatsoever.  The linux side cannot ping google, but that might have something to do with not having internet access from that computer :).

Ultimately (in a month) it'll come with me to my college apartment where there is a NAT router and high-speed internet.  But I don't want to wait that long, because I'm setting this up as a learning experience to teach myself Linux and Python and Apache and stuff and don't want to put that off for a month.  I'm just trying to get the VM and the host to have static local IPs so I can SSH back and forth and browse my VM's Apache sites from my Mac.  The only way to get internet to that tower at home is to borrow my sister's laptop (mine died :( ), dial that into AOL, and share the connection over wireless (not having a 30 foot Cat5).

---

### Post by ilrudie on 2008-07-17
I don't recall exactly if parallels has a host only option but it sounds like this is what you want for right now.  I'm pretty sure VMware has this option so Parallels probably does also.  I think the problem you are having is Parallels is giving your Linux vm direct access to a virtual interface off the physical interface.  Since there is no link on that interface they can't talk to each other.  With host only your vm won't be able to see the internet but this should not be a problem since you don't have internet right now anyway.  You could also see if NAT might work since it should cause parallels to do some routing but I'd recommend the host only option first if its there.

(sorry I forgot about the not having networking at home part of the question when writing the original response)

---

### Post by ZacharyPruckowski on 2008-07-17
Yeah, I'll try host-only networking.  I tried linking the two ethernet ports on my mac together without success, and Bonjour/avahi-daemon gets me Linux -> Mac but not Mac -> Linux.

Thanks for your help.

---

