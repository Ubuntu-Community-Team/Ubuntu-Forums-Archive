---
title: "DNS Settings remain blank"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by Stephen_A on 2008-05-09
On 'Network Settings' on 7.10 there are the tabs for Connections, General, DNS and Hosts. On 'DNS Servers' there's a space to enter the addresses and 'Add' and 'Delete.' Whenever I enter some settings and click 'Add' the settings just disappear. They don't show in the space for 'DNS Servers.' Is this normal? How am I supposed to see the settings I've entered?  
Thanks for any input on this.

---

### Post by jetsam on 2008-05-09
The interface is a bit strange.  After you type in the DNS ip address, hit enter.  It will be saved then and turn blue.  You can then hit add again to add another fallback server.  

These settings get over-written if you're using dhcp.  If that's the case, you can set them in your router's dhcp server setup so that they persist between reboots.

---

### Post by Stephen_A on 2008-05-09
Thanks for that. Just what I was after.

---

