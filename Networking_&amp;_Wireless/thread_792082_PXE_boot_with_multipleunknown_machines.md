---
title: "PXE boot with multiple/unknown machines"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by speedkreature on 2008-05-12
I have an isolated network for experimentation's sake.  One computer (the sever) can get to the network for the sake of installing packages as needed, however usually this computer is not connected to the internet.

It is always connected to a 24-port Gb switch, each port with an computer that is set to boot via PXE.

I'm following a how-to to get the dhcp and tftp server set up but I've run into a problem.
This method requires that I know the MAC address of each computer that will be booted in this manner and this will not be a manageable solution. 

Does anyone know of a method that does not require me to know the MAC addresses so that any PXE bootable device I attache will boot with the image I've prepared?

The server is running Hardy Heron.

---

### Post by SgtDude on 2008-05-12
Could you please post your /etc/dhcp3/dhcpd.conf here?  I'm pretty sure the problem is in there somewhere.  (BTW, I'm pulling that path from memory, so if it's wrong, please don't shoot me).

---

### Post by wirelessmonkey on 2008-05-12
The DHCP server requires a MAC address to provide an IP address. So long as DHCP is configured correctly, each machine should be able to create a tftp connection. Based on your description, I don't see what would require non-automatic MAC information.

I hope that made sense :P
Best of Luck

---

