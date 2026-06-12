---
title: "how can I use my computer to self host a web page"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Russell Burrows on 2009-03-31
I have close to zero money so renting a domain is out.
I want to try and use my computer and its broadband conection to self host my own web page about cosmology.

I am using Ubuntu 8.10 and a celeron 1.7 ghertz procesor with a one gig ram module

So are there any gui tools for this as to further complicate things I can barely open a terminal window so command line tools are real scary.

On the other hand I managed to get my laptop to run Ubuntu 8.10 and virtualbox and xp and had fun harvesting tiberium when a lot of folks told me there were no games on virtualbox xp so maybe theres hope for me to be able to learn stuff about web pages.

Thank you for reading this and thanks in advance for helping me.

---

### Post by 3rdalbum on 2009-03-31
Ubuntu makes it easy.

Install the "apache2" package and put your web pages into the folder /var/www/  - you will need to open a root file browser in order to do this. If you don't have any sort of NAT or router-based-firewall in between you and the internet, your pages will immediately be visible to anyone who types in your IP address into their web browser.

If you have a firewall in your router, then you will need to configure it to pass incoming requests on port 80, through to the internal IP address of your computer. You can find your internal IP address by right-clicking the network manager icon and choosing "Connection Information".

Then, anyone who types your external IP address into their web browser will get your page. You can find your external IP address from [www.whatismyip.com](www.whatismyip.com)

What's the difference between internal and external IP addresses? Your internal address is how your router and other computers on your network can communicate with your computer. Your external IP address is how computers on the Internet can communicate with your computer; in reality the external IP address is the IP address of the router as seen from the Internet.

If it starts with "192.168" then it's your internal IP address. Otherwise, it's your external one. When you give people your IP address so they can go and visit your website, it needs to be the external address.

---

### Post by mikechant on 2009-03-31
Note that some ISPs forbid you from running a server via their connection, and (perhaps more commonly) others put restrictions on it such as it not being public/generally accessable (e.g. password protected), or not on port 80 or something. I think in practice, most don't care/notice unless you get very high traffic, but it's well worth reading your ISP's Terms and Conditions before setting anything up.

---

### Post by LowSky on 2009-03-31
> **mikechant said:**
> I think in practice, most don't care/notice unless you get very high traffic, but it's well worth reading your ISP's Terms and Conditions before setting anything up.

Very good thing to bring up. One option is to check out the free web page hosting companies

[Here is a google search on Free Web Hosts]("http://www.google.com/search?hl=en&q=free+web+hosting&aq=0s&oq=free+wed+ho")

the other thing to consider is to pay for it. sure you say you have no money but  sites like godaddy are cheap for low bandwith sites  there chepest price is $3.99 a month for 3 months with 10 GB of space.
[http://www.godaddy.com/gdshop/hosting/shared.asp?isc=gooh1003af](http://www.godaddy.com/gdshop/hosting/shared.asp?isc=gooh1003af)

All this looking up is getting me think about starting my own website.... oh the possibilities!

---

### Post by NE Key on 2009-03-31
Have you looked at [www.one.com](www.one.com)   - they charge me about GBP10 per year ( around USD 18 ).

Just looked - it is even cheaper now - almost free.

---

### Post by hackett on 2009-09-22
Cheap first class website hosting

[http://www.hosterware.com](http://www.hosterware.com)

Demo

[http://cp.hosterware.com/demo.cgi?account=400468]("http://ubuntuforums.org/view-source:http://cp.hosterware.com/demo.cgi?account=400468")



JH

---

### Post by zkriesse on 2009-09-22
It's incomplete but I should have it finished soon. But for reference, check this out. [https://wiki.ubuntu.com/Ubuntu-with-Firebird-Database](https://wiki.ubuntu.com/Ubuntu-with-Firebird-Database)

---

