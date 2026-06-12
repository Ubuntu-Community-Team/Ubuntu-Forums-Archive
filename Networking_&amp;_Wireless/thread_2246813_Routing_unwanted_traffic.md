---
title: "Routing unwanted traffic"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by HappySmack on 2014-10-03
delete me

---

### Post by Michael_McKenney on 2014-10-03
You can drop the traffic on a higher end firewall and router. It still ties up your pipe.   I run a Data Center.  On our Cisco 2911 router's ACL list it blocks the IP addresses from ICANN list for China, Russia, and Middle East.  I also block login port traffic from all for Novell, Microsoft, SQL, etc.  Blocking it just stops it from getting to the Cisco Firewall, which would block it anyway.  The pipe still has the data.  This is from the ISP to us.  If I see traffic going out of the ASA and router that is getting blocked by the rules, the workstation or server is infected.  

If you are seeing the traffic going up from your network to these addresses, you have malware or a virus on your devices sending the traffic.

---

### Post by HappySmack on 2014-10-03
Thanks for the reply. It seems someone started up a freenet session without my knowledge. All is well now.

---

### Post by Michael_McKenney on 2014-10-03
Our Cisco hardware monitors traffic inbound and outbound for same threats.

---

### Post by lisati on 2014-10-03
> **HappySmack said:**
> delete me

Thread closed.

---

