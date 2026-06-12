---
title: "Cant get to *ONE* webpage"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by luken8r on 2007-03-28
I cant seem to get onto cbs.sportsline.com from either one of my Ubuntu boxes on my network, but oddly enough, a third Win PC can get there with no issues. Seems to be only this one page.
I did the normal deleting cookies, cache, etc on both but no dice. 
One machine is running 6.10, the other 6.06.  Ive tried FF 1.x and 2.x, and Epiphany; both wireless and wired (changed IPs) but nothing. I can ping the site but when i do a tracepath, it dies at some hop:

 1:  192.168.100.50 (192.168.100.50)                        0.105ms pmtu 1500
 1:  isa.eng.xxxxxxx.com (192.168.100.2)                 0.768ms 
 2:  host34.72.248.105.conversent.net (72.248.105.34)     asymm  3   1.241ms 
 3:  host33.72.248.105.conversent.net (72.248.105.33)      36.832ms 
 4:  ma1-bb1-ge-0-3-0-2.conversent.net (216.41.101.24)    asymm  5  36.541ms 
 5:  ma1-bb2-ge-0-3-0-2.conversent.net (216.41.101.23)     27.135ms 
 6:  sl-gw4-spr-0-3.sprintlink.net (160.81.249.97)        asymm  5  23.466ms 
 7:  sl-bb22-spr-10-0.sprintlink.net (144.232.21.23)      asymm  6  26.618ms 
 8:  sl-bb20-spr-14-0.sprintlink.net (144.232.21.70)      asymm  7  25.321ms 
 9:  sl-bb24-nyc-14-2.sprintlink.net (144.232.19.185)     asymm  8  26.549ms 
10:  sl-bb24-nyc-0-0-0.sprintlink.net (144.232.20.121)    asymm  9  36.864ms 
11:  sl-bb21-dc-5-0-0.sprintlink.net (144.232.8.164)      asymm 13  36.716ms 
12:  sl-bb21-mia-6-0-0.sprintlink.net (144.232.9.26)       65.071ms 
13:  sl-st22-mia-15-0-0.sprintlink.net (144.232.2.206)     71.396ms 
14:  144.223.64.142 (144.223.64.142)                      asymm 15  64.573ms 
15:  66.165.161.193 (66.165.161.193)                       67.580ms 
16:  no reply
17:  no reply
18:  no reply
19:  no reply



When I run the same trace on my Win box, the website is two hops away
What can I check to get this working?

---

### Post by blockcipher on 2007-03-28
On your ubuntu box try the following opendns ips and see if it makes a difference

[http://www.opendns.com/start/](http://www.opendns.com/start/)

Just for testing.

---

### Post by luken8r on 2007-03-29
no luck. any other suggestions?

---

