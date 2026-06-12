---
title: "Cannot connect to internet (wireless)"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-11-17
I have a Aspire 5735-4774 laptop with Ubuntu 9.04 installed on it. And I have been able to connect to the internet up until last night. And I have no clue why.

I have enabled networking and wireless, and my laptop does recognize the networks, but it won't connect (even though up until last night it connected no problem). It is a secured network, but I have the password, so that's not the problem either.

Here is what I did:

I went to the troubleshooting part of the 'Ubuntu Help' (for wireless - section 5.2) and the first step was to check that the device is on.

So I typed in the terminal 
> sudo lshw -C network  


It said that I would see an output, along with the words "CLAIMED,UNCLAIMED, ENABLED or DISABLED".

This was the output:

> 
*-network 
description: Ethernet interface
product: 88E8071 PCI-E Gigabit Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 16
serial: 00:1d:72:cb:51:c7
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
*-network
description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 01
serial: 00:17:c4:47:eb:75
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 3a:9c:62:82:a7:e1
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


So apparently, my wireless device is off (because it said 'DISABLED' on the output). It says in the help that I may need to turn on a switch or something, but there is nothing physical on my laptop that I need to switch on for wireless.


What should I do? Why would the internet suddenly stop working like that?

I really need someone's help with this please.  Thank you.

---

### Post by screaminfakah on 2009-11-17
My laptop has a button by the keyboard.

---

### Post by nayeret43 on 2009-11-17
Do you have the same laptop model that I have?

Acer Aspire 5735-4774

I don't see any button for it.  Which button?

---

### Post by screaminfakah on 2009-11-17
Sorry,  I should have been more clear.  I have an HP and I accidentilly hit the button on mine and had the same issue. 

Is your router broadcasting your network name or is it hidden?  If it is hidden you have to connect to it using that option in Ubuntu and then type in your password if it is secured.

Edit: you have type in your network name and password if it is secured.

I have had to in the past unplug my router for a minute and power back on to fix bad connections

---

### Post by nayeret43 on 2009-11-17
Yes my router is broadcasting my network name and it isn't hidden.  My computer recognizes the secured network and I have the password to it.  

But it still doesn't connect.

---

### Post by screaminfakah on 2009-11-17
Right click (I think could be left click) the network icon and make sure Enabled is ticked.
In the past I have deleted and reset up my connection to resolve issues with configuration.

---

