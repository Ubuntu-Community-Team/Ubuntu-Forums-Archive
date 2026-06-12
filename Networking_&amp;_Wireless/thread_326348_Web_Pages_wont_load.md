---
title: "Web Pages wont load"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by klittzzer on 2006-12-27
I need help for the folowing

I am running Ubuntu Edgy and have a Netgear DG630 router which is connected with Ethenet.

I have a conection and can ping google etc with no packet loss. It is set to dhcp. I cannot, however get any web page to load. It always times out. I have tried disabling IPv6 in etc/../aliases but have had no joy.

Could anyone please tell me how to set up a static IP address? (I will not be able to download anything from repositories without one) I have tried but can't seem to sort it out.

Does anyone know why web pages won't load?

Any help would be welcomed

klittzzer

---

### Post by dbott67 on 2006-12-27
You may want to try 2 things (you can skip the ipv6, as you mention you've already done it):

1. Blacklist ipv6
2. Change default DNS servers to OpenDNS servers.

Both steps are outlined in this thread (post #3 and #5):

[http://www.ubuntuforums.org/showthread.php?t=323747](http://www.ubuntuforums.org/showthread.php?t=323747)

-Dave

---

