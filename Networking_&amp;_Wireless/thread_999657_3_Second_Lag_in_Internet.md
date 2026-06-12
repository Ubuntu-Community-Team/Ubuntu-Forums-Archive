---
title: "3 Second Lag in Internet"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by iampriteshdesai on 2008-12-02
Recently my internet connection has slowed down considerably. I have noticed that there is around 3 second lag in every application which requires internet. If I click on a link in Firefox it takes about 3 sec before my router starts blinking. Previously it used to be instantaneous. Same thing happens with Rhythm box while fetching lyrics, album art.
Also my Ubuntu seems to have got sluggish. I have disabled some desktop effects.
Help

---

### Post by SpaceTeddy on 2008-12-02
only a guess - but if eveything is slow when using the network, i'd blame a dns server that is offline and your first choice. That would be the usual time for a dns request to time out before the backup dns is queried...
just an idea, though. 

Since you have a router, you'd need to lookup your dns server theres (they are supplied by your ISP). Try forcing your computer to use the second one first and see if it is still slow...

no other idea... really...

---

### Post by iampriteshdesai on 2008-12-02
But Vista zips along...

---

### Post by SpaceTeddy on 2008-12-02
well, in that case the only thing i can possibly thing of is looking at the acctual transmissions and seeing if any re-send or packet corruption is happening... It was a guess anyway... :(

Vista is on same comp ? if so, what is in your /etc/resolv.conf ? how long does a name lookup take ?
install dns utilities...
```
sudo apt-get install dns-utils
```
lookup of an ip
```
nslookup www.google.de
```

i am just guessing here... :(

---

### Post by superprash2003 on 2008-12-02
post your ifconfig output, do you find webpages loading partially or anything like that?? try this open firefox and type 209.85.171.100 basically open [http://209.85.171.100](http://209.85.171.100) .. do you notice the 3 second lag?? if not then its a dns problem

---

### Post by iampriteshdesai on 2008-12-02
Yeah you are right.
Google loaded within a sec. I guess it must be the problem with ISP, hathway. Coz now it is zipping along. Some times Ubuntu gets painfully slow and then it happens.
thanks!

---

### Post by superprash2003 on 2008-12-03
changing DNS servers to opendns , would fix the problem permanently.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by iampriteshdesai on 2008-12-03
> **superprash2003 said:**
> changing DNS servers to opendns , would fix the problem permanently.. [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

I liked your blog I'm subscribed.
Please take a look at my blog. Its mu signature, helpforlinux
Thanks for the help

---

