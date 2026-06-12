---
title: "Static IP"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by ex-para on 2013-11-23
Would the below instructions give me a static IP, or just a load of trouble?. It is for a website.

This is not a post I sent I sore it on the net. 
 
Re: How do I configure static IP addresses with BTHomeHub 2?
Options 
on &#8206;02-09-2010 21h09 
the address you posted looks like your public broadband ip address, your on the wrong page
*
settings > advanced > home network > then click on your device
*
you will notice that you cant simply type in a new ip. work around for you
*
on your laptop edit the tcp properties for your wireless connection
*
ip 192.168.1.xxx (replace xxx with a number from 1 > 253)
subnet 255.255.255.0
gateway 192.168.1.254
dns1 192.168.1.254
*
your laptop should connect with the new address
*
go back to the hub page above and select yes > "Always use this IP address"
*
you can set the tcp settings to auto on your laptop

---

### Post by bashiergui on 2013-11-24
What is the purpose of the static IP? Do you want your private or public IP to be static?

---

### Post by ex-para on 2013-11-25
It is for a website, thanks for the reply. i have tried DD client and I get messages that it is running etc. but it never works.

---

### Post by Bucky Ball on 2013-11-25
*Thread moved to** Networking & Wireless.***

> **ex-para said:**
> 
This is not a post I sent I sore it on the net. 
 
Re: How do I configure static IP addresses with BTHomeHub 2?


You give no indication of what you've done or what you're trying and am unsure what this has to do with Ubuntu in the first place. You might be better off looking on their support pages if you want to know how to set an IP address on BTHomeHub:

[http://www.filesaveas.com/search.html?cx=partner-pub-7058424672899018%3A9689387062&cof=FORID%3A10&q=static+ip&sa=](http://www.filesaveas.com/search.html?cx=partner-pub-7058424672899018%3A9689387062&cof=FORID%3A10&q=static+ip&sa=)

---

### Post by ex-para on 2013-11-25
Your answer is not much help, 8 years ago I built my own website that I host myself and I have my own web address so the whole thing costs me nothing. The only problem I have is the dynamic IP, it might go for weeks without changing but change it does. The question I asked is simple enough would what is on the post work or not. The computer is on Ubuntu 12.4 so that is what I think it has to do with Ubuntu so why answer me the way you have.

---

### Post by Bucky Ball on 2013-11-25
Provide a link to the site and some detail about what you've tried already. Thanks.

You can set the static IP for your machine in Network Manager. It must be set in a range outside the range your router/AP is assigning IP addresses via DHCP server, if it is.

---

### Post by drmrgd on 2013-11-25
Your internet service provider is the one who controls your IP address, and even if you set it to static on your computer, that won't prevent the ISP from changing the IP address next time your computer renews the lease on it.  So, you're stuck unless you ask your ISP to give you a static address instead.  In the US, this is possible, but usually comes at an additional cost, which makes it not worthwhile considering for the same price (approximately), you can just purchase web hosting service and get way more features.

There are dynamic DNS services out there that will map your dynamic IP address and point traffic to it.  One example that I've heard of people using is this one:

[http://www.noip.com/free](http://www.noip.com/free)

I've not ever done this, though, and I'm not 100% on how it works and how reliable it is.  Might be something worth checking out, though, if you really want to host your own website without a static IP address.

---

### Post by ex-para on 2013-11-27
Sorry for the late reply, [http://barrieb.dyndns.info](http://barrieb.dyndns.info) is the site address and for what information I have gathered the lease for BthomeHubb can only be extended to 21 days and sometimes the IP stays the same that long. As I have said I have had the site for 8 years and I built with the help of w3schools. I don't use it much now as I have retired but I need to keep it going as wish to change the contents to something else. The server I use is Nginx. If nothing can be done with hub I will try no-ip.

---

