---
title: "ESSID has a underscore is this a problem?"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by cubbiechris on 2007-02-01
My ESSID has two underscores  ex. Linksys_ow_5888  is this a problem?  I can connect to a nonsecure wireless that doesn't have underscores fine, but when I try to access mine it doesn't work.  I'm using WEP as my security.

---

### Post by chili555 on 2007-02-01
Don't know for sure, but I have some suggestions: first, let's see what happens when you issue the command sudo iwconfig eth1 essid Linksys_ow_5888. Second, is this your router? That is, not your employer's or family's. If it is yours, I would change the essid.

In my Linksys router, under Wireless -> Basic Wireless Settings, I can set the SSID to be anything I want or blank.

Finally, according to man iwconfig, >  With some cards, you  may  disable  the  ESSID  checking  (ESSID promiscuous) with off or any (and on to reenable it).

So you may be able to disable essid checking with sudo iwconfig eth1 essid any

Good luck and have fun.

---

### Post by cubbiechris on 2007-02-01
> **chili555 said:**
> Don't know for sure, but I have some suggestions: first, let's see what happens when you issue the command sudo iwconfig eth1 essid Linksys_ow_5888. Second, is this your router? That is, not your employer's or family's. If it is yours, I would change the essid.

In my Linksys router, under Wireless -> Basic Wireless Settings, I can set the SSID to be anything I want or blank.

Finally, according to man iwconfig, 

So you may be able to disable essid checking with sudo iwconfig eth1 essid any

Good luck and have fun.

It is my router that I use for my PS3, Xbox 360, and two laptops.  I've never had a problem with it.  I'll try those things you listed when I get back home.  Thank you so much!!!!

---

### Post by Handssolow on 2007-02-01
What does iwconfig show as your essid?

If you have a problem and it doesn't show your essid exactly then I suggest you use the terminal to input your essid and put quotation marks example "your_essid"

In Puppy Linux I had to use single quotation marks example 'my<>essid' under similar circumstances before it was correct.

---

