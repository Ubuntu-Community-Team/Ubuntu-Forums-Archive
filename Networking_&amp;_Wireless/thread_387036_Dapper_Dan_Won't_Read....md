---
title: "Dapper Dan Won't Read..."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by mzlizzy on 2007-03-17
I have wiped my hard drive clean and installed Ubuntu Dapper Dan.  Now, I just need to connect to my ISP which is DSL by Windstream.  I inserted my Windstream CD to set up my modem but nothing happens.  (I'm wondering if I need a new Windstream CD.)  I know Windstream doesn't support Ubuntu; could that be why it doesn't read my Windstream CD?
Can't I get connected to my server?  Help, please & thank you.

---

### Post by gradedcheese on 2007-03-17
What the heck is "dapper Dan"? :confused:   Your windstream CD has some windows software on it, you certainly can assume that it won't do you any good in Linux.  Get some other means of internet access so that you can follow this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

(read about how to add your Ubuntu CD to Synaptic or apt in general first, you need to do that since you don't have internet access via Ubuntu and thus can't download packages).  

That said, my suggestion is to go out and buy a cheap "home networking router" from any computer store.  Plug that in between the DSL modem and your PC(s) and enjoy normal internet access without the need for software and configurations.  I hate direct to DSL modem access setups and always let a router do the PPPoE stuff for me.  It's well worth the price :)  Either way, you'll get it to work.

---

### Post by mzlizzy on 2007-03-17
Dapper Dan 6.06 is my version of Ubuntu; the latest free release.  I live in the country; can a router pick up signals?  I'm confused now--don't I need some kind of ISP?  My neighbor has internet; I bet a router would pick up from that signal.  Am I right?  I don't know about all this.  I appreciate your helpfulness and clarifications.

---

### Post by gradedcheese on 2007-03-17
Dapper **Drake** is version 6.0.6 LTS :)

A router is a router... that is, it acts as a bridge between a local network (LAN) and the outside (WAN).  It goes like this:

"internet" -> DSL Modem -> router -> your network (LAN) with your PC(s)

This has nothing to do with picking up signals, sneaking on to your neighbors' networks, and so on.  Now the idea is like this: your DSL requires something called PPPoE, essentially the DSL version of dialup.  This sucks and requires software on your PC (both in Windows and Linux), that's what's on that CD from your ISP.  You can, instead, put your PPPoE ("ISP settings") in the router, and it will manage everything for you.  On the "LAN" side, it will just hand out DHCP addresses to your PCs just like in a real office LAN.  This means that you'll be able to just plug a PC into the router and things will just work, no ISP CD needed.  The ISP-related stuff is not affected, you still maintain the same service you had with them.

Some routers have wireless capability, enabling you to do all the above, plus have a wireless LAN (WLAN) if you wish.  If that interests you, buy one like that instead of a regular one.  The Linksys WRT54G is a popular choice.

---

### Post by mzlizzy on 2007-03-17
Most informative.  I shall get right on this.  Seems much simpler now.  Thanks alot!

---

