---
title: "How To setup a WAN miniport connection in UBUNTU 9.10"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by AnandTerry on 2010-01-13
I have a dualboot with windows XP.
 I have a WAN miniport connection which asks me for username and password. 

I am unable to make such a connection in UBUNTU 9.10

I get an active eth 0 connection in wired connections.
When i try sudo pppoeconf, it first shows me the active eth 0 connection and asks me if it is the only active connection. 
When i say yes i get some progress bars like 'scanning devices' , ' looking for pppoe access concentrator' , and then , i get a window saying 
'Sorry, I scanned 1 interface, but access concentrator did not respond. Please check your network modem cables. Another reason for the scan failure may also be another pppoe process which controls the modem'.

And in the teminal i get the following /user/sbin/pppoeconf:521:modconf:not found

I am tired of booting xp again and again in search of solutions. Could anybody please help?


When i try sudo ethtool eth 0
I get Settings for eth 0:
cannot get device settings : operations not permitted
and some 4 more sentences.

Multimedia does not work, it says some plugins are required
I need to change my ethernet speed to 10 half duplex to get my internet connection as per the conn in windows XP

Please help, i am all lost.

---

### Post by AnandTerry on 2010-01-23
1 week since i posted.
30 views
0 REPLIES. :confused:

Should i wait for some more time guys ?

---

