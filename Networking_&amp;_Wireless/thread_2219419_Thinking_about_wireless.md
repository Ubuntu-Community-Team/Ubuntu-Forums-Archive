---
title: "Thinking about wireless"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by vasa1 on 2014-04-24
Hi, I know nothing about wireless but I want to get started!

I have a Dell 1545 laptop (bought in 2009). It has Lubuntu 14.04 on it.

I've run the script to provide the experts with info about my hardware (after running *sudo apt-get install firmware-b43-installer* and rebooting): [http://paste.ubuntu.com/7320246/](http://paste.ubuntu.com/7320246/)

So my questions are this:
Is my hardware adequate?
I'm in India and connected to the internet through a "broadband" cable connection (600 kb/s nominal speed). What would be a suitable wireless router?
I want to connect my Samsung Galaxy Duos (GT-S7562) because I live in an area with no 3G and rotten 2G.

Any advice is will be appreciated (keeping in mind that I don't know about wireless at all).

Thanks!

---

### Post by Dennis N on 2014-04-24
> Any advice is will be appreciated (keeping in mind that I don't know about wireless at all).

I will put in my 2 cents worth:

The hardware is definitely adequate! My laptops are even older (2005 aand 2007 Dells). The issue with wireless is usually with the wireless card and drivers. Yours is common, and the guys here know all about getting it to work.

Comments:

The router I use now is Netgear Wireless G (model G54). 4 ethernet ports, plus wireless. This is probably considered a basic router, but all I require, and needs no attention. It works very well with Linux. A newer model is Wireless N (faster). You set up the wireless interface by connecting your computer by ethernet cable to the router and using the web browser interface (the router instruction sheet will tell you the URL to use).  You choose an SSID (network name), channel, encryption standard, and password. Be sure to set it up with the most secure encryption standard.

Then remove the cable. Usually, the the computer's wireless (which you already have installed the drivers for, of course) will immediately take over and look for networks and will notify that some are available (it gives you the SSIDs or names). Choose yours, enter the password, and you are in. The password is saved. Next time, it connects to the same network during boot up (if it's still available) without asking. That's it.

Good Luck. What are you waiting for?

---

### Post by SeijiSensei on 2014-04-24
> **vasa1 said:**
> I'm in India and connected to the internet through a "broadband" cable connection (600 kb/s nominal speed). What would be a suitable wireless router?

I found this: [http://techfeel.in/2013/05/10-best-wireless-router-2013/](http://techfeel.in/2013/05/10-best-wireless-router-2013/)

I browsed the reviews at [Newegg](http://www.newegg.com/) for the top-rated items in that list, and to me the best choice for the money is this [Buffalo N300](http://www.newegg.com/Product/Product.aspx?Item=N82E16833162069).  I have a similar Buffalo router, and it works well.  It also runs the "[dd-wrt]("http://dd-wrt.com/")" flavor of Linux rather than a proprietary operating system.  That means you can upgrade the device's "firmware" over the Internet for free from the dd-wrt site if you ever need to.  Since dd-wrt is basically Linux, it's very flexible as well.

I presume this router is available in India since it was in that guy's list. He reported a price of Rs 3355 or about US$60, which is a bit less than Newegg is charging.

---

### Post by vasa1 on 2014-04-25
> **Dennis N said:**
> ...
Good Luck. What are you waiting for?
Thanks for the push :) I took the plunge. My ISP's office is next to the store I bought the router (iBall: local brand) from. The ISP guys configured it for me so I just had to bring it home and just plug it in. They did whatever was needed without asking any details about my laptop.

Now my Android is fully updated and I'm happy.

---

