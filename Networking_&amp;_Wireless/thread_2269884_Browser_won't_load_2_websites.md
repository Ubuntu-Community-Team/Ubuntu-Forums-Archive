---
title: "Browser won't load 2 websites"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by aeronutt on 2015-03-18
There are 2 websites that 'lock up' most of the time I try to view them. I have accounts on both, and it's very frustrating. No other web sites have this behaviour. Most of the time (~9 out of 10) my browser sits there with a blank page attempting to load, and nothing moves forward (other websites continue to work fine in other tabs). Maybe 10% of the time it'll complete the page load, but then often hangs up a few pages later on the same web site.

I've tried both Firefox and Chromium (fresh load), cleaning cookies, etc, but I think it's something more nuanced than that. 
The worst offender is :
[http://ezpassmd.com/](http://ezpassmd.com/)

What can I look at to debug this problem (assuming it's something I can control).

A few details:
Dell inspiron laptop
Ubuntu Linux 14.04
Firefox and Chromium browsers

---

### Post by aeronutt on 2015-03-18
More info:
```
curl -v https://www.ezpassmd.com
```

returns

> * Rebuilt URL to: [https://www.ezpassmd.com/](https://www.ezpassmd.com/)
* Hostname was NOT found in DNS cache
*   Trying 138.69.165.55...
* Connected to [www.ezpassmd.com](www.ezpassmd.com) (138.69.165.55) port 443 (#0)
* successfully set certificate verify locations:
*   CAfile: none
  CApath: /etc/ssl/certs
* SSLv3, TLS handshake, Client hello (1):



And it hangs there.

---

### Post by sammiev on 2015-03-18
I tried the address and it works but there are warnings from FF.

---

### Post by aeronutt on 2015-03-18
Interesting.

Here's what FF developer network tool sees. It just STOPS at [www.ezpassmd.com](www.ezpassmd.com)

[img]http://i.imgur.com/V3Vd2Yn.png[/img]

---

### Post by MrSteve on 2015-03-19
when trying the link i get a redirect to this ...

[https://www.ezpassmd.com/en/home/index.shtml](https://www.ezpassmd.com/en/home/index.shtml)

---

### Post by aeronutt on 2015-03-19
Yea, that link locks up for me just like ezpassmd.com.

I've pretty much figured out it's my Clear 4g-to-wifi router. I can easily access the site on my android phone, but when I turn off data, and turn on Wifi (through my Clear wifi router), the site gets stuck.  I've tried every setting I can on the Clear router, but nothing fixes this! There's another web site that does similar but not as bad as the ezpassmd.com site.

---

### Post by MrSteve on 2015-03-19
have you tried using another set of DNS server addresses, setup within the router, other then the default ? ...

---

### Post by aeronutt on 2015-03-19
> **MrSteve said:**
> have you tried using another set of DNS server addresses, setup within the router, other then the default ? ...

I have tried this in the 'network connections' settings of ubuntu, but it does not appear that I have the option to set the DNS server addresses in my 'router'. FYI, my 'router' is only a Clear USB wifi hotspot. It does have a page for router settings, but I don't see settings for DNS servers.

My guess is this is exactly the problem as I'm able to access the webpages when I'm connected to any other network.

---

