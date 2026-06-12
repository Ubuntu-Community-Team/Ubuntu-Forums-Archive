---
title: "Network interface name and MAC address changes when laptop lid is closed"
date: 2024-06-05
forum: Networking &amp; Wireless
---

### Post by christianfosli on 2024-06-05
I'm using Ubuntu Desktop 22.04 LTS on a Lenovo Thinkpad with all the defaults wrt networking.


Today I noticed that the network interface and mac address I get when connecting my laptop to a USB-C display with some integrated ports/docking, at my work desk, which has a wired ethernet connection, has changed.
My laptop doesn't have any Ethernet port, so the NIC is for the display at my desk.



It used to be enp121s0 and mac address ending in 90:1f:a0, but now I get enxa84a63910179 and mac address ending in 91:01:79.

Upon further investigation I found out I get the old network interface name (in `ip a`) if I have my laptop lid up when connecting to the display,
but I get the new network interface name and MAC address if I have my laptop lid closed when connecting the display, and wake up the laptop using an external keyboard.


I find this surprising, and a bit annoying because my work has whitelisted my MAC address for a few services that I occasionally need.
Any ideas why this might be?

Thanks in advance

---

### Post by TheFu on 2024-06-05
systemd finds devices in different order sometimes.  That order and the driver determine the "name" for some devices.  Using boot options, I think you can override any default names. I don't exactly know how, but you can google as well as I can. Try this: [https://www.howtogeek.com/880124/how-to-permanently-change-your-mac-address-on-linux/](https://www.howtogeek.com/880124/how-to-permanently-change-your-mac-address-on-linux/)

That won't change the MAC.

Some MACs allow changing through local tools on the system. That is dependent on the driver software. I used to do it when my cable/COAX ISP required a specific MAC as authentication ... perhaps 20 yrs ago.  I think changing the MAC is less likely for wifi chips, but it won't hurt to try.

---

### Post by currentshaft on 2024-06-06
MAC whitelisting for security is the equivalent of a "No Tresspassing" sign to keep intruders out.

Let your system administrators know attackers are living in the 21st century and stop relying on silly totems.

---

### Post by TheFu on 2024-06-06
I'd never trust MAC filtering beyond convenience needs.

If the people paying me want MAC address filtering, I'll do it. It isn't a holy war and I know getting them to change is very unlikely.  Pick your battles.  

I've worked places that kept a list of MACs and if a new device showed up on the network, it was dropped into a "go nowhere" network until an agent was added to validate some policy was followed.  That was hard for contractors since their agents never supported Linux systems.  We ended up getting the CIO to approve our devices and the security guys (all MS-Windows-centric, of course), manually added our 10 consultant devices.

I suspect our poster here isn't interested in being "that guy" and just wants to connect to get work done.  That's completely valid too. Pick your battles.

---

