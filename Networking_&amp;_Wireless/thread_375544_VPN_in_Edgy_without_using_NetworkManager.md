---
title: "VPN in Edgy without using NetworkManager"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by Skeletron on 2007-03-03
With Dapper, I used pptpconfig to connect to my work's VPN.   When I upgraded to edgy, this stopped working.  I get this error message:

Cannot determine ethernet address for proxy ARP

I found some instructions that said to use NetworkManager.  I tried this, but as far as I know NetworkManager does not work with my wireless card:

02:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

Is there any other solution for Edgy users?

---

### Post by spiderdijon on 2007-03-04
I have the exact same problem - using a Broadcom 4306 mini pci wireless card, pptd does not work in edgy "...ARP proxy" error, network-manager doesnt give any errors apparently it just brings up a little progress bar when the VPN is selected and goes away and the VPN still doesnt work, I would really like to know if there are any edgy pptp vpn solutions available.

---

### Post by snitramc on 2007-03-06
Yeah same problem here.  I installed network manager and pptpconfig on edgy and get not much. WHen I "disconnect" pptpconfig, I see IP adresses representing known DNS servers inside my work network. But I can never connect. I get the ARP proxy message too. I think I'll try this a few more times and then try 6.06 to see if it helps.

---

### Post by Skeletron on 2007-03-11
In addition to the PPTP VPN, my work also provides a Cisco VPN.  I installed the Cisco VPN client and set up a user profile, but when I run the Cisco VPN I get:


Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

privsep: unable to drop privileges: group set failed.
The application was unable to communicate with the VPN sub-system.

---

### Post by r4e on 2007-03-13
Hi Skeletron,

Did you try executing that as a super user? Try:

su -c 'vpnclient connect **profile**'

where **profile** is **profile**.pcf

---

### Post by ebola15 on 2007-03-15
I have the same error I have tryed

su -c 'vpnclient connect profile'

but I get this error

bash: vpnclient: command not found

---

### Post by Skeletron on 2007-03-15
> **r4e said:**
> Hi Skeletron,

Did you try executing that as a super user? Try:

su -c 'vpnclient connect **profile**'

where **profile** is **profile**.pcf

Ah, the thing I was missing from my command before was that I was including .pcf in the profile name.

Now I get this:

Cisco Systems VPN Client Version 4.8.00 (0490)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system.


EDIT:  Oh, right.  I forgot to run /etc/init.d/vpnclient_init start

After doing that, and then try to connect, it seems to work.  Except I then can't seem to hit any sites (internal or external to the VPN).

---

### Post by Skeletron on 2007-03-16
Note: When I connect, I *can* hit sites by their IP address, and I can continue to hit sites I'm already on.  So I assume this is a DNS issue at this point?

---

### Post by r4e on 2007-03-17
I was running a software firewall that was disrupting me from being able to connect to machines on the external network. Disabling the firewall allowed me to get through. If you are running a firewall, it might be worth a shot disabling it to see if that fixes the problem. I didn't get around to figuring out specifically what ports needed to be opened, but will be working on that again soon (just switched from Ubuntu to Kubuntu, so I'm reinstalling everything).

To check the DNS have you tried executing:

nslookup [sitename]

ie. nslookup ubuntuforums.org

If the DNS works it should return the IP that you are trying to connect to.

---

