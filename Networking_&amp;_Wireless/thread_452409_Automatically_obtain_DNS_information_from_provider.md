---
title: "Automatically obtain DNS information from provider"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by tma_it on 2007-05-23
How do i configure my network adapter to "Automatically obtain DNS information from provider" which is an option in Fedora. I need to get my hostname set automatically via DHCP.

/Thomas

---

### Post by blazercist on 2007-05-23
your modem gets that info and your network card gets it from your modem, if you are set to use DHCP then it should automagically get all your DNS info as well.  just go into network-manager and chose DHCP for your connection of choice.

---

### Post by tma_it on 2007-05-23
No, i have my own dns and dhcp server running on another box. I need the dhcp-client to set my hostname to whatever comes from the dhcp-server. How does that work in Ubuntu/Debian. I Fedora fx. there's an option called "Automatically obtain DNS information from provider" which sets the hostname (FQDN).

---

