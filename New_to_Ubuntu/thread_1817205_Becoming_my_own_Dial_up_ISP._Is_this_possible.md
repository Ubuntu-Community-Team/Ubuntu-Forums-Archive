---
title: "Becoming my own Dial up ISP. Is this possible?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by h4ck3rk1ng on 2011-08-03
Ok, here's what I want to do.
I have cable internet at my house.
It is 15mbps downstream, and like 2 mbps upstream.
That's not the point though.

I want to know, if i can somehow use the modem in my computer ( I have an old 56k modem PCI card somewhere) so that I can use another computer to dial into it, and use the internet.

I realise I won't get speeds as fast as my cable, but I am going on vacation, and i dont have internet, but I do have a phone line, so i want to bring my laptop and dial into my home server and get internet.


Is this possible?
Also, I know DSL runs on phone lines. Could I do this, only with DSL so that my connection is faster?
Can i configure ubuntu to accept a call on it's modem and route internet traffic to it?
And what software would I need to connect?

---

### Post by jtarin on 2011-08-03
[All things are possible.]("http://www.howtoforge.com/linux_dialin_server")
Your in for some work as the article is a little dated but you should be able to find replacements for newer Ubuntu installs.
The document is RedHat centric so there is some factors you will have to adjust.

---

### Post by carverj on 2011-08-03
> Also, I know DSL runs on phone lines. Could I do this, only with DSL so that my connection is faster?


I didn't know these existed previously but found this which may help with that: -
[http://www.cisco.com/en/US/products/hw/modems/ps296/products_user_guide_chapter09186a008007cf34.html](http://www.cisco.com/en/US/products/hw/modems/ps296/products_user_guide_chapter09186a008007cf34.html)

---

### Post by bigpayne69 on 2011-08-03
Wow, if you only knew the world of hurt your trying to get yourself into. If your going on vacation, almost all hotels, truck-stops, McDonald's, ect provide free WiFi access now a days. I'm not going to pretend to know how to pull that off but I can tell you that if you want to set that up, you better brush up on your programing skills. You'd need to find a way to get a modem to register an incoming call, answer said call, and then bridge the dial-up connection to the NIC ... Good Luck.

---

### Post by bigpayne69 on 2011-08-03
As for using DSL ... no. If you really want to know why making a DSL connection from one computer to another over a commercial phone line won't work, send me a message. Other wise, just take my work for it, it would take to much time to explain.

---

### Post by Gone fishing on 2011-08-03
I think in principle not too difficult. Set up the modem to accept incomming calls, setup a dhcp server to assign an IP address to the incomming computer connection (or you could use fixed IPs), set up squid to hand out the internet.

However, at the end of the day you may connect at 33kbs and pay for the phone call to the house. Would it not be cheaper and much better to use a mobile broadband dongle?

Obviously it might be fun to do the setup.

---

### Post by MartyBuntu on 2011-08-03
If you can "dial in" to your home computer from your remote location, then you already have internet.

---

