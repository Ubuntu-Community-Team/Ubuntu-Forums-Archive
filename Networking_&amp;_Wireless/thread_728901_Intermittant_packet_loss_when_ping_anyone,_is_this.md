---
title: "Intermittant packet loss when ping anyone, is this the problem?..."
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-03-19
I've been having lots of problems with my DSL connection lately, and I think I've narrowed down the problem, but could use some help from someone who knows more about this than I do.

if I ping say [www.google.com](www.google.com) or [www.yahoo.com](www.yahoo.com), I often get packet loss between 20-40%. I did a tracepath to [www.google.com](www.google.com) and got:

 1:  USER3141.local (192.168.1.23)                          0.411ms pmtu 1500
 1:  jc-in-f99.google.com (64.233.187.99)                 asymm 36   4.306ms 
 2:  adsl-71-159-231-99.dsl.sndg02.sbcglobal.net (71.159.231.99) asymm 36   6.456ms pmtu 1492
 3:  adsl-71-159-231-254.dsl.sndg02.sbcglobal.net (71.159.231.254)  40.210ms 
 4:  dist2-vlan60.sndg02.pbi.net (63.200.206.195)          41.173ms 
 5:  151.164.94.4 (151.164.94.4)                           43.969ms 
 6:  ex1-p14-0.eqlaca.sbcglobal.net (151.164.191.225)     asymm  8  43.715ms 
 7:  no reply
 8:  no reply
...

If I ping (or even flood ping) my router at 192.168.1.1 or my modem at 192.168.0.1, all is well with no packet loss. If I ping 71.159.231.99 and 71.159.231.254 (from above), I don't get any packet loss either. But 63.200.206.195 and 151.164.191.225 don't respond at all to pinging and I get 100% packet loss. Also, "ifconfig" does not show any errors as I might surmise since my router/modem seem to be working OK. 

I assume that 63.200.206.195 and 151.164.191.225 could just be blocking ping requests, so that's not necessarily a problem, right? So how do I troubleshoot this problem? It sure seems like the problem is happening at my ISP level or beyond, is this correct?

Thanks for any help! :)

---

### Post by tgalati4 on 2008-03-19
Check your wiring and connections from your DSL modem.  Since DSL goes through the phone lines, it is subject to degradation when the phone lines get wet, chewed, stretched due to tree limbs, or anything else that can effect the connection.  If a neighbor gets a new phone line, it can mess up your connections at the pole.  

You could also have a failing filter somewhere in the house.  Try disconnecting all other phones in the house and see if changes the behavior.

Packet loss of more than a few percent will cause problems.

Sounds like you need to call the phone company to help troubleshoot.

---

