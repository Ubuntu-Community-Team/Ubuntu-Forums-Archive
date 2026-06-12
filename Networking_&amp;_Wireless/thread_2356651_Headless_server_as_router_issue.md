---
title: "Headless server as router issue"
date: 2017-03-25
forum: Networking &amp; Wireless
---

### Post by Ziggid on 2017-03-25
Apologies up front for any spelling errors or anything, but I'm forced to write this post on my phone. 

I'm running ubuntu 16.04.2 LTS headless which I also use as a router for my LAN. Typically I use webmin for maintenance (mainly firewall). Eth0 is directly connected to the modem, and p5p1 to a network switch. 

This setup has been working for me for a couple of years until yesterday I started playing around with configuring alternative DNS servers in webmin. When this didn't have the effect I was looking for (ad blocking) I briefly set the IP for eth0 to static. From that point on Internet on both my windows machine (ethernet)  and android device (wifi) was lost. I tried manually rolling every setting back to what it was (hadn't  changed much and haven't touched the firewall), but to no avail. 

Currently the server is accessible, both from outside as from inside the network, and I can ping other servers from it. However when I try to ping google.com (or any other external site) from my windows machine the name is resolved into an ip - adress but the request times out. 

IP forwarding is still enabled as is masquerade for output interface eth0 (according to webmin at least). When running tracert on the windows machine to any external ip (e.g. 8.8.8.8) I only get a single hop, namely to the gateway (p5p1 interface on the server) before it times out. I am able to ping the ip of eth0 (dhcp from isp) from the windows machine. 

Does anyone have any idea what could be causing this? Thanks in advance!

---

### Post by TheFu on 2017-03-25
Check that if-forwarding is enabled. Don't trust webmin. Check the real settings.  
[https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

Can't help with webmin issues. Never use it.

---

### Post by Ziggid on 2017-03-25
> **TheFu said:**
> Check that if-forwarding is enabled. Don't trust webmin. Check the real settings.  
[https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent](https://askubuntu.com/questions/311053/how-to-make-ip-forwarding-permanent)

Can't help with webmin issues. Never use it.

Thanks. cat /proc/sys/net/ipv4/ip_forward yields 1 (after reboot) so that seems to be in order. Webmin is just a shell as far as I know. Happy to solve it without webmin if you have any other suggestions.

---

### Post by TheFu on 2017-03-25
Is ipv6 enabled? If so and you aren't using it, try disabling it.

---

### Post by Ziggid on 2017-03-25
Ok.. This is a bit silly. Turns out for some reason starting the firewall at boot had been disabled. Re-enabling it solve my problems. Thanks! 

Now how do I close this topic?

---

### Post by lisati on 2017-03-25
> **Ziggid said:**
> Now how do I close this topic?

You can mark the thread "Solved" using the "Thread tools" drop-down menu near the top of the thread.

---

### Post by weightgain40002 on 2017-03-25
If your wanting a change you could consider IPFire, I was setting up a similar setup and switched to IPfire, which seems to be very lightweight solid and easy to setup

---

