---
title: "[SOLVED] Help in installing a wireless router (ubuntu 8.10)"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by manilaph on 2008-12-01
My PC (pentium 4) is on pure Ubuntu 8.10 (no windows) and it is connected to a wired dsl modem.

1) How do I install a wireless router (and what is a good brand to purchase) and connect this to my dsl modem?

2) Are there any obstacles that I would likely encounter?

3) Will this be a simple "plug n' play" installation?

4) Do I need extra hardware besides buying a wifi router?

I am totally clueless in installing a wifi router for the home. I just want to use my Ubuntu Compaq Presario V3000 laptop wirelessly in the home.

---

### Post by benhur99ph on 2008-12-01
Connect your DSL to your wireless router.
Then connect your Ubuntu Desktop to your wireless router via LAN cable.
Open your browser and type the IP address of the router on the address bar (Its usually 192.168.1.1). 
It will prompt for the username and password. Check the wireless router's manual (this is commonly admin/admin).
It you have logged in successfully, you can now configure the wireless router. Check your routers documentation.
After you have configured, connecting your laptop should be pretty straight forward. By the way, what's the OS on your laptop?

I use a Linksys WRT54G wireless router and its been running pretty good. Some say D-Link wireless routers are good too but I haven't tried that one yet.

---

### Post by EXCiD3 on 2008-12-01
This would be an easy installation. Purchase a wireless router, plug the DSL ethernet cable into the router's internet port (which is off to the side of the rest). This will give the internet connection to the router to share up. You can connect to the router easily and configure it by going to its IP address in Firefox or any other browser. If you buy a wireless b/g router just about any device will be able to connect that supports wireless. As for good brands to purchase, any will work, some will get you better range than others. I personally wanted a small one and picked up the Fon+ router for personal use here at [http://shop.fon.com](http://shop.fon.com) Others that are good are the linksys wrt54g as it runs an open source OS just like the Fon. I also have invitations for the Fon+ to get it for $30 off making it $19.95 if anyone is interested.

---

### Post by manilaph on 2008-12-01
Thanks guys!

Will be going to a store to buy a wireless router right now. Will be updating again when all is well or not well.

I've seen other instructions over here but they had a dual-boot of XP/Ubuntu installed and not pure Ubuntu.

---

### Post by manilaph on 2008-12-01
for benhur99ph, my OS on my laptop is also Ubuntu 8.10. I noticed that the wifi signal is weak... I have to be very near the router when I am in my parents house. And even at 10 feet from the linksys router... it is at 80% and then i go a little bit farther... it becomes 30% and sometimes I cannot connect at all.

---

### Post by manilaph on 2008-12-01
Ok. I purchased a D-Link Wireless G Router model DIR-300

[http://ucables.com/ref/D-LINK-DIR-300-WIRELE-R45799](http://ucables.com/ref/D-LINK-DIR-300-WIRELE-R45799)

it comes with a CD that does not work in Ubuntu. It says on the box as a requirement: "Computer with Windows XP SP2 or Windows 2000 SP4 or Mac OS X (v10.4/v10.3) or Linux-Based Operating System and an Installed Ethernet Adapter "

---

### Post by manilaph on 2008-12-01
okay, d-link installed... did not need to use the CD that came with it.

now, my ubuntu 8.10 Presario V3000 connects to the wifi right away at 100% (very good).

next step is that i want to make it a "secure" connection. how do i make it a secure connection?

Thank you.

---

### Post by acreech on 2008-12-01
> **manilaph said:**
> 

next step is that i want to make it a "secure" connection. how do i make it a secure connection?

Thank you.

hook your computer directly to your router with a cable and then follow these instructions


To access the configuration utility, open a web-browser such
as Internet Explorer and enter the IP address of the router
(192.168.0.1).

Enter the user name (admin) and your password. Leave the
password blank by default.

If you get a Page Cannot be Displayed error, please refer
to the Troubleshooting section for assistance.

This should be page 14 of the manual for your router.

[ftp://files.dlink.com.au/products/DIR-300/Manuals/DIR-300_Manual_v1.00.pdf]("ftp://files.dlink.com.au/products/DIR-300/Manuals/DIR-300_Manual_v1.00.pdf")

---

### Post by manilaph on 2008-12-01
> **acreech said:**
> hook your computer directly to your router with a cable and then follow these instructions


To access the configuration utility, open a web-browser such
as Internet Explorer and enter the IP address of the router
(192.168.0.1).

Enter the user name (admin) and your password. Leave the
password blank by default.

If you get a Page Cannot be Displayed error, please refer
to the Troubleshooting section for assistance.

This should be page 14 of the manual for your router.

[ftp://files.dlink.com.au/products/DIR-300/Manuals/DIR-300_Manual_v1.00.pdf]("ftp://files.dlink.com.au/products/DIR-300/Manuals/DIR-300_Manual_v1.00.pdf")

thank you very much. secured already using wep. i will use wpa once i figure out how to do it.

---

### Post by bhsk_08 on 2008-12-25
> **manilaph said:**
> okay, d-link installed... did not need to use the CD that came with it.

now, my ubuntu 8.10 Presario V3000 connects to the wifi right away at 100% (very good).

next step is that i want to make it a "secure" connection. how do i make it a secure connection?

Thank you.

Hello,

i have a query here. how did you installed the wireless router in your ubuntu? I am also having the same router but need to know how to install it without the CD, bcoz the cd dnt work in Ubuntu.

---

### Post by redonwhite on 2008-12-29
> **manilaph said:**
> thank you very much. secured already using wep. i will use wpa once i figure out how to do it.

Yeah i would get WPA set up asap =).  WEP is extremely easy to break into.  Good luck!

---

