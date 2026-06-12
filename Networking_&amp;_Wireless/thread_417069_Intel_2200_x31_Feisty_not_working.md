---
title: "Intel 2200 x31 Feisty not working"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Vincent_Lin on 2007-04-21
Hi,

I have an IBM X31 with Intel 2200bg card.  It was running perfectly under 6.10, connecting to dlink 801.11g router, without WEP or anything.

I upgraded from 6.10 to 7.04 last night, and now both wireless and wired networking are gone.   Network Manager shows exactly the same configuration as before, except that the connections are gone.  I have a couple of other 6.10 machines in the house and they are happy cruising the net through this dlink router as before.  Is it a known problem?  Does anyone have a quick fix to it?  

Thanks.

Vincent Lin

---

### Post by Vincent_Lin on 2007-04-21
Hi,

Sorry for the bumping!

Is there any means to fix my X31 with Intel 2200BG wireless card?  I lost connection after upgrade to Feisty.  However, every setting still remains.  I can ping to localhost, but not to my router 192.168.0.1, which yields :
ping: sendmsg: Operation not permitted.

Hope someone can give me some direction to look to.

Thanks.

Vincent

---

### Post by Vincent_Lin on 2007-04-23
Hi,
Sorry to bump it up again.

It seems that ping: sendmsg: Operation not permitted is given by apf, the firewall program, after querying almighty google, and a change in apf configuration file /etc/apf/conf.apf to enable eth1/eth0 will give the networking back.

But, my problem is, I don't have apf installed, and therefore, /etc/apf directory does not exist.

Normal wired ethernet is not working either.  I am facing the possibility to re-install 7.04 from downloaded CD, which I am downloading now, but so relunctant to do.

Before that, does anyone have a clear-cut cause and cure for this problem: upgrade from 6.10 to 7.04 yields networking (both wifi and wired) not available??  Machine is IBM X31, with wifi  Intel 2200 Pro/bg , and Intel 8280 Pro/100 VE Ethernet controller.

Thanks.

Vincent

---

### Post by foureight84 on 2007-04-28
yea my 2200BG is not detected at all in the final feisty version. looks like we're on our own on this one. just find the ndiswrapper and install the 2200bg drivers.

---

### Post by J_tech on 2007-05-17
my intel 2200bg wireless seems to be working ( I ca nsee it transfer packets and communicate to theAP)  but because we have wep set to Key 2 it does not pull down an Ip - I cannot find where I can set the key for the passcode...any help would be appreciated...

---

### Post by chili555 on 2007-05-17
I assume you mean key 2 is the key the router or access point is broadcasting. To set key 2 in iwconfig, do, in a terminal:```
sudo iwconfig eth1 key [2] 0123456789abcdef
```Obviously, substitute your interface, if it's not eth1 and your actual key.

---

