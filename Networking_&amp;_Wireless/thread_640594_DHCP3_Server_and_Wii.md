---
title: "DHCP3 Server and Wii"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by btaylor101 on 2007-12-14
I recently set up a DHCP3 server on 7.04. I am having problems with my Nintendo Wii constantly sending DHCPREQUEST to the server. The server is sending the DHCPACK back to the Wii, but that does not stop the DHCPREQUEST from coming back from the Wii. I have the default lease time set up as 
> default-lease-time 86400;
max-lease-time 86400;
Does anyone know if this is a known problem with the Wii or could it be another setting in the dhcpd.conf file I need to update.

---

