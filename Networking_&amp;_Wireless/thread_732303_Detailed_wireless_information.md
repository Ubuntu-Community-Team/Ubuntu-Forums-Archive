---
title: "Detailed wireless information"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by Mb0742 on 2008-03-22
Hey I want to see more than just the wireless network name and strength, (i'm in Ubuntu 7.10) how do I get detailed information on it such as the mac address and all that info?

---

### Post by Eiríkr on 2008-03-22
Run the [font=courier]ifconfig[/font] command in a terminal.  The MAC address is shown right after the "HWaddr" label.  

Cheers,

Eiríkr

---

### Post by Mb0742 on 2008-03-22
Thanks but I want information on a host I am yet to connect to. (shouldn't iwlist wlan0 scan work? It just says no results to display yet in the network thingo at the top it says information about the network)

---

### Post by Eiríkr on 2008-03-22
If you're not connected to a remote host, I don't think there's any direct way to get this information.  If you can access your DHCP router, that will contain the MAC addresses of any hosts that have obtained leases from it.

---

### Post by daniel. on 2008-03-22
Yeah, if you have access to the DHCP server then usually that's how people find out that stuff.

And I haven't tried it, but my guess is that an ARP tool would be able to give you the MAC addresses on your network, assuming your on the network. And if you're not... ahem, why do you need the MAC addresses again? ;)

Cheers,

daniel.

---

