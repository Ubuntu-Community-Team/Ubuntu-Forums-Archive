---
title: "LTSP DHCP with Verizon FiOS ActionTec Router"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by lipinski on 2008-09-11
I'm trying to configure my network to support some PXE clients.  My PXE Server is Ubuntu 8.04 using LTSP.

The problem I'm having is with the DHCP side of things.  I have Verizon FiOS internet service, and their Router (ActionTec) is serving as the DHCP Server.  Unfortunately, I cannot find a way to customize their router to support PXE booting since I can't seem to find anywhere to provide DHCPd options.

So, my thought was to have my PXE Server doing the DHCPd.  If I went this route, however, I wanted my PXE server to only serve DHCP Requests for PXE clients, and have my Verizon FiOS router serve DHCP Requests for all other hosts on my network.

Can this be done?

It seems that I could probably configure DHCPd on my PXE Server to only provide IPs for DHCP Requests that are PXEClients.  However, I don't know how to prevent my ActionTec router from serving IPs to PXE Clients. 

Any ideas?

---

