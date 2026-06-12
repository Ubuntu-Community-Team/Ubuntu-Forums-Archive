---
title: "How can I prevent rogue DHCP services/servers?"
date: 2019-08-03
forum: Networking &amp; Wireless
---

### Post by webmiester on 2019-08-03
Hi,

Every now and then, someone plugs in a router into our LAN with its own DHCP.  This DHCP starts handling IPs to some computers and these computers cannot communicate with the rest of the system.  Currently, I am in the process of redesigning the network to improve the security of the system.  The first step is to physically secure the switches and ports.  But of course, a wisecrack can still unlplug an office computer and plug his router from there.  What else can I do to prevent this from happening again?  

A thread I found where this was mentioned said that Microsoft's Active Directory could help this as it would verify the DHCP server in question before allowing it into the network.  I cant find resources describing this in LDAP.

---

### Post by TheFu on 2019-08-03
Have the CIO announce that anyone doing it will be fired.
When it happens again, the CIO needs to fire the person responsible.

You'll want to setup network alarming that tells you immediately if a rogue device is plugged in, and have a security guard come with you to confiscate the device.

Or you could setup complex methods to manage MACs on the network using specialized switches which block all non-approved devices from the network completely.  I've seen where some switches place unknown devices that haven't been validated onto different subnets.  It was a hassle, since the switch wanted our Linux machines to confirm they were running the company's approved AV tool before allowing them onto the network.  Ended up loading a small Windows install, running the AV, getting the device into their DB, then using Linux the rest of the time, after it was registered.

---

### Post by webmiester on 2019-08-26
Thanks Fu.

---

