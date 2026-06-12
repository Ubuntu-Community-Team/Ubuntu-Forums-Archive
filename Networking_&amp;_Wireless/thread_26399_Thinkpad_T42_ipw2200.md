---
title: "Thinkpad T42 ipw2200"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by tmd3 on 2005-04-12
I am having some trouble connecting to my wireless router using dhcp?  I have tried everything.  I even turned of wep just to see if it would work. I can see it through my computer.  I can even seem to connect but I can not get through to the internet.  I get an error when I boot up.  something like rwr: name resolution temporarily not found.  It is very odd.

Also if my wep for example is 01 43 ac 03 bd 3c how do i input that into iwconfig or the gui.  Thank you

---

### Post by luca_linux on 2005-04-13
Are you using the latest version of the ipw200 driver or the one included in the kernel?
You should use the latest one from ipw2200.sourceforge.net, that is 1.0.3.

---

### Post by tmd3 on 2005-04-13
I'll give it a try and get back to you.

---

### Post by luca_linux on 2005-04-14
Ok, I'll wait for your feedback.
Anyway here's a howto I wrote: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by darkrider01 on 2006-10-13
A bit old thread but I have the same problem on an Inspiron 9300 - ipw2200.

Question for luca_linux. The howto you wrote the link to is not for dapper drake right? In that howto there is another link which leads to another how to for ubuntu after hoary... but it only describes how to use wpa... what if I use WEP? am I all set up right now? (just did a fresh install of ubuntu dapper drake) but I think not, because tried installing some network managers for gnome etc but still nothing...

Thanks

---

### Post by luca_linux on 2006-10-15
With Dapper you have no big need to update the ipw2200 driver. So just make sure you have configured the system the right way.

---

### Post by philippe_carlo on 2006-11-03
> **darkrider01 said:**
> A bit old thread but I have the same problem on an Inspiron 9300 - ipw2200.

Question for luca_linux. The howto you wrote the link to is not for dapper drake right? In that howto there is another link which leads to another how to for ubuntu after hoary... but it only describes how to use wpa... what if I use WEP? am I all set up right now? (just did a fresh install of ubuntu dapper drake) but I think not, because tried installing some network managers for gnome etc but still nothing...

Thanks

Just a (naive?) suggestion: if you  are using wireless, is your eth0 (wired) interface down? This may be a routing conflict between both NIC's.

---

