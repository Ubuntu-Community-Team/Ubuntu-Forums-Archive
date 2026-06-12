---
title: "Changing dns servers"
date: 2019-05-19
forum: Networking &amp; Wireless
---

### Post by again? on 2019-05-19
Trying to change dns servers to cloudflare.
Configured in gui as below.
[ATTACH=CONFIG]283283[/ATTACH]

What's the command in 18.04 to restart networking?
How can I check that cloudfare's dns servers are being used?

---

### Post by #&amp;thj^% on 2019-05-20
Ha don't know how I missed this one, but it seems routers come into play here also, for example my,
Netgear

When connected to your Wi-Fi, visit [http://www.routerlogin.com](http://www.routerlogin.com) or [http://www.routerlogin.net](http://www.routerlogin.net) in a web browser. Log in with your administrator credentials. Click &#8220;Internet&#8221; and then select &#8220;Use these DNS Servers&#8221; and enter the primary and secondary addresses. Then click &#8220;Apply.&#8221; Done. 
followed by:
```
sudo systemctl restart network, or service network-manager restart
```
However, all routers are not created equal, if you can&#8217;t find the tool to perform a test, you can still figure out if your DNS settings are configured correctly using the first method outlined.
Open the "dnsleaktest.com" website on your browser.

Click the Standard test button.

Once you&#8217;ve completed the steps, in the result, check the ISP column to see the name of the DNS service you&#8217;re currently using.

---

### Post by again? on 2019-05-20
Thanks for the reply.
dnsleaktest.com was what I was looking for to check dns server being used.

After restarting the network, dnsleaktest.com now shows cloudflare.
[ATTACH=CONFIG]283292[/ATTACH]

I could also change dns servers in the router but tests show my network-manager dns settings
override my router dns settings, so not necessary.
For complete info this is my router...
> Product Vendor: Technicolor
Product Name: MediaAccess TG789vac v2
Software Version: 16.3
Firmware Version: 16.3.7637-V2-2-1-CRF695
Hardware Version: VANT-6

P.S. Either of these methods worked to restart network.
[LIST]
[*]Disabling then enabling networking from the network-manager gui 
or
[*]sudo service network-manager restart
[/LIST]
Thanks.

---

