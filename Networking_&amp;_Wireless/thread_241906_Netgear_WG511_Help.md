---
title: "Netgear WG511 Help"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by WSTGangsta on 2006-08-22
I have a Compaq Armada m700 with ubuntu, and a Netgear WG511 wireless card. now how do make this thing work? I have no clue. I'd imagine I'd have to get some wi-fi library, but Im a total linux noob.
Thanks.

---

### Post by amohanty on 2006-08-23
This:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
says your card is almost supported.
It also lists some relevant threads.

ALso the wiki might help:
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=wireless)

HTH
AM

---

### Post by WSTGangsta on 2006-08-23
None of that really helps me, doesnt really say what to download and stuff.
EDIT:
Ok I am using a different wireless card, a linksys one, and this time it detects it but I cant connect to the actual signal.
It just says "disconnected" under signal.

---

### Post by amohanty on 2006-08-24
Which Linksys card?
What make?

AM

---

### Post by WSTGangsta on 2006-08-24
WPC11

God I hope this thing works.

EDIT: Ok a step further, I just disabled eth0 (the wifi card is eth1) and now I dont get a disconnected error. And Im getting a 91% signal strength, but no pages load, I had this same network problem with linux on my desktop. So do I need to use kubuntu then? (worked fine there).

EDIT AGAIN: Okay I can load some web pages, but the only one that worked at a decent speed was ubuntu.com

---

### Post by amohanty on 2006-08-24
Try sitting right next to your wireless router and try this:
[http://www.dslreports.com/stest](http://www.dslreports.com/stest)

then walk over to another room and check it out again.

AM

---

### Post by WSTGangsta on 2006-08-24
The page loads, after half an hour, then I click the text link and it times out. I dont have the best ISP either. Quest DSL, and Im at the end of the phoneline. So...any one had this kind of problem, and would it go away if I got cable internet?

---

### Post by WSTGangsta on 2006-08-25
Sorry for bumping and DP'ing. But I really want to solve this as soon as possible.  Why this great dude the only one helping, I dont mean to complain but this is a very serious issue. I need internet access!

---

### Post by amohanty on 2006-08-25
Try this and post the output:

> ping google.com

After about 10 secs type Ctrl-C

AM

---

### Post by WSTGangsta on 2006-08-26
> **amohanty said:**
> Try this and post the output:



After about 10 secs type Ctrl-C

AM

Ahh dammit. Now its not working at all, can you please tell me what fields in the network manager need to be filled out with what information from ipconfig /all in windows?

---

### Post by amohanty on 2006-08-28
Are you working with a DHCP server or are you using static IPs?
Are you sure you dont have some sort of bandwidth throttling setup on your router?

The easiest way would be to check the box that says something to the effect of (ask the server or automatic configuration).

HTH
AM

---

### Post by WSTGangsta on 2006-08-28
DHCP.
And I'll check my router config page for bandwidth throttling.

---

### Post by WSTGangsta on 2006-08-28
Crap, how do I delete this post?

---

### Post by devilsadvocate1987 on 2006-08-28
your connection problem seems to be caused maybe by some configuration error - make sure that its set to automatically acquire IP address if you have DHCP or that you've set the static IP if you dont have DHCP and have an IP address assigned to you. 

Is your wireless working normally from another operating system, or maybe even another laptop? 

As for the Netgear WG511 problem, if you have a card thats made in china, then you will have to use the windows drivers. Atleast thats what I could figure out after a few hours of google. I posted a short how-to on that on my blog - you can find it at [http://devilsadvocate-chs.blogspot.com/2006/08/netgear-wg511-wireless-adapter-on.html](http://devilsadvocate-chs.blogspot.com/2006/08/netgear-wg511-wireless-adapter-on.html)

hope this helps

---

