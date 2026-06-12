---
title: "Another wired problem with my wireless?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by zggame on 2008-05-27
I recently put Xubuntu 8.0.4 into a Dell latitude c610 PIII w/Dell TrueMobile 1150 802.11b miniPCI. Fortunately it works out of box. But it does have some weird problem. Here is two questions. 

At home, I have a Belkin router connect to a cable modem.  And all the PCs connected to the router on wire or wirelessly.  I set the WPA-PSK on the router for wireless.  I can connect to the router through the wireless only by manually setting the "WPA personal" in the network setting.  On the tray icon, I only get the a couple of WEPs or LEAP options.  Are all these WPA/WEP some encrypting methods?  Why some in tray or some only in the manual setting.  Just curious, are they the card hardware feature or the software encryption feature?  


Another more weird problem is like this.   I cannot find the c610 in the DCHP list in my router's set-up page.  ( I config it to get the IP DCHP)  I check with the [www.ip-adress.com]("http://www.ip-adress.com").  It has an IP different from all other computers.  All of other share the same IP.  When I connect it to the router by cable, it has the same IP as all others.  How can I get two different IPs with my modem?  All the time, I have several other computers (including one winXP using wireless) connecting internet unbrokenly. So the shared IP has not changed. 

:confused:


Any thought on this? Thanks.

---

### Post by zggame on 2008-05-28
After some reading, it seems that dell TrueMobile 1150 has no support for wpa.  And with a more careful check, although the application->system->network shows my wireless id, the iwconfig actually shows that I connect to another unsecure wireless point.  So no wonder it has another IP.

---

