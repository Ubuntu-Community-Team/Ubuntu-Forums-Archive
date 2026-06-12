---
title: "Redirect Hotspot requests to specific interface"
date: 2018-06-06
forum: Networking &amp; Wireless
---

### Post by medin2014 on 2018-06-06
[FONT=Ubuntu]I have two 3/4G USB modems, I created Hotspot wifi using network manager GUI to share internet, but all requests comming from the hotspot are redirected to only one interface and the other is not used, what I want is to redirect all hotspot requests to one usb modem and let all my local browsing requests use the second usb modem, how can I do it please ?[/FONT]

---

### Post by SeijiSensei on 2018-06-06
I believe you would need to use the advanced routing features in the Linux kernel for this.

[http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/](http://www.tldp.org/HOWTO/Adv-Routing-HOWTO/)

I only used these features once, when a client was in transition from one network provider to another.  I pretty much followed the cookbook as I recall.

---

