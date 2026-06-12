---
title: "Trouble with internet ADSL on Feisty Fawn"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by phoenix910 on 2007-04-05
Hey, wondering if anybody could help or point me in the direction of another thread that might help. I'm having trouble with my D-Link DSL-502T. It works fine with windows, but I just installed Feisty Fawn and I can't get it working on there. I've tried various static adresses, changed the default gateway address, tried DHCP (which is the same as Windows), and nothing will work. Yet I can still ping and do things via FTP. Any ideas?

---

### Post by spd106 on 2007-04-05
When you're on a static configuration check the DNS tab in network-admin. There should be a DNS server address. If not add one, you can use your router or ISP's DNS servers directly.

---

### Post by HereInOz on 2007-04-05
Yes, spd106 has it right I reckon.  Set the DNS ip addresses to the ones given you by your ISP, set the gateway to the internal IP address of your router, with a static IP address for the Feisty network card, and it all should come together.

---

### Post by phoenix910 on 2007-04-05
My ISP didn't give me a DNS server address, but I have set the gateway to the internal addy of the router. If I change it to static, it still doesn't work, it only stops my ability to ping anybody, which is the only thing that was working before.

---

