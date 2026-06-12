---
title: "Firestarter and printing sharing"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by CatMihV on 2008-01-29
Well, i have the following problem. I have 2 printers, an HP Laserjet 1020 and a photosmart c1300 series. Installed them, shared them, everything works ok until i launch Firestarter. When Firestarter is active the other 2 computers in the network (running winXP) can't acces them. If i turn off Firestarter they work ok but ther's no internet connection sharing. I tryed to enter lots of policies in Firestarter, opened all the ports that i saw they were used in "Events" tab and still it doesn't work. I searched for hours on google and on forum and still didn't find a solution. If someone can help me, without unninstaling Firestarter, pls help me.

And on top of that, 1 of the computers doesn't have any trafic with the ubuntu box (that i use as a router and soon some other stuff) and i can't understand why. I removed all policies and it simply won't work, no ping no nothing. The other computer works just fine.

Thnx in advance for your help.

---

### Post by CatMihV on 2008-01-30
Well? Isn't there anyone here that can help me? :((((

---

### Post by CatMihV on 2008-02-05
I solved the problem using guarddog instead of firestarter but now there is a new problem :). I installed a webserver (apache2, as instructed here: [http://www.lullabot.com/videocast/install-local-web-server-ubuntu](http://www.lullabot.com/videocast/install-local-web-server-ubuntu) ). Now, the 2 pc's in network can ping the server, can access the webpage but there is no net sharing. If i use Firestarter there is net sharing but the printers and the webpage can't be accessed :(. Should i start learning on how to make my own firewall using iptables? (Tryed kmyfirewall too, but there are some errors at launch that i couldn't find answers for them so i gave up)

---

### Post by TwoThirds on 2008-07-12
I'm having exactly the same here! I'm going nuts! Stopping firestarter solves the problem, but I can't ask my wife to stop firestarter whenever she need to print! I first saw that I also was running bastille firewall (dunno when I installed that!)  but removing this didn't help a bit! Anyone any ideas?

---

### Post by TwoThirds on 2008-07-14
I removed and purged firestarter, flushed iptables and put everything to accept, reinstalled firestarter, switched on and allowed everything I could find in the preferences:  solved! (which one of the settings gave me the trouble, or if I solved it by reinstalling: don't know, but it work: don't touch it! :) )

---

