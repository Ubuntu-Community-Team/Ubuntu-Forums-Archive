---
title: "Killing Active Connections Shown in Firestarter"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by superstylin on 2007-08-04
Good Evening!

I have been using Firestarter for the last couple weeks, and looking at the Active Connections section, there are at least 10 connections which arent GAIM, Steam or Firefox that I would like to kill/ban asap! Ideally I would want to simply right-click the active connection in Firestarter with a "ban connection to this IP" or add to a blacklist or such...

I am a noob when it comes to Linux and would prefer a simple GUI interface, I don't really need to monitor the traffic, the speed, etc etc... 

Also, I have noticed most of these connections are in the port range of 30,000-65,000! However, I don't really know if this means anything :O

Ubuntu 7.04, Latest version of Firestarter from the repos!

Thanks!


Super.

:)



PS: I tried an outbound policy disabling access from ports 30,000-65,000 but it doesn't do much, if anything... (and doesn't really serve my purpose...)

---

### Post by superstylin on 2007-08-04
Well, if this isnt possible in Firestarter, could someone recommend an GUI App that would serve a similar function? Detecting/Killing connections?

Thanks!

---

### Post by HermanAB on 2007-08-04
Well, the terminal *is* a GUI application...
;)

sudo iptables -I INPUT -s 1.2.3.4 -j DROP

BTW, those connections are probably advertisement servers hooked by your internet browser.  So it would be more efficient to add Adblock+ to Firefox.

Cheers,

Herman

---

