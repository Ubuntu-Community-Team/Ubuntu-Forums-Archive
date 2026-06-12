---
title: "Net. failure (not on ubuntu...)"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by [pl]ice on 2005-09-05
i'm really really sorry; this can be called OFF TOPIC, but i NEED help !!! 
       we can't solve this problem; please please, don't post any silly comments, excetp admins of course... ;)
Thank You!     



From the main sever(DHCP) signal is going to a switch, then is divided into 2 subnets.
2nd subnet goes to me, like that:
     from switch, onto converter, to fibreoptic,, for about 80 km, then to converter, from that  it goes via Planet modem through copper wire for 18 km, then back to Planet modem, to a switch, from a swith to one PC, and then to a AP. around 10 PC at the moment are using AP.
like:  server>switch1>catalist-1>optic>catalist-2>modem1>copper wire>modem2>switch2>eth0 + (from switch) AP
Problem: 
      	after a while(randomn) there is no connection with the server, not only using the AP, but eth0 as well. During this, ping can be sent from eth0 ca reach AP,   both modems, catalists, but not to the server.
 If DHCP is re-enquired(obtaining IP procedure) then everything is ok.
  At this same time(while the net is down) server can see the AP(and all the route to AP), but NOT the eth0 (or other wless PC's).  
There is another subnet caming out of switch1, (they have no problems).
  Often, if someone pings from the server to the eth0, everything comes back to normal.
   All was fine for 2 months or so. no none can find what's happening.

the server is on PLD linux.

any advise?
please bear in mind that i cannot walk and check each route, it's over 12 thous. km away.... and both modems have been replaced, without any sucess.

---

