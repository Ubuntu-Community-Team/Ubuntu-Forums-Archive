---
title: "Winmodem final tweak help please"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Pogo_VA on 2007-07-31
I've got an HP dv1622nr laptop (essentially series dv1000) on which I'm testing a WUBI installation of Feisty Fawn after trying out the live 7.04 CD. It seems to see pretty much everything such as sound, video, ethernet, and wireless out of the box, but not my winmodem (of course - that would be too easy!!)

Unfortunately, I've got to have a working dialup connection.

After visiting Linmodem and reading various wiki & howto articles (thanks to all contributors), my Smartlink at /dev/ttySL0 responds to query modem requests in Gnome ppp as well as terminal probes from within Kppp. In fact, I was able to use the INIT2 information to help configure the Kppp dialer which is what I want to use.

Howsomever, the Kppp log shows that while modem initialization apparently goes without a hitch up to dialing the ISP's telephone number, the process stalls after that and fails with a NO CARRIER message. I get the same when I try the $ sudo wvdial approach. Gnome ppp also fails (not sure how to start a log file in this prior to dialing so not sure as to why, but I suspect the same issue). $ pon simply sits there, but I'm not sure if there's a log for that either that I don't know about ala Gnome ppp.

When I picked up my handset and dialed the ISP telephone number, I noticed that it takes somewhere between 5 - 10 seconds before the handshake tone comes on. I'm wondering if and where there's a setting that tells the dialer program how long to wait for the tone before deciding there's no carrier and making that note in the log or if the failure is coming from something else.

Any and all thoughts welcome and thanks.

-------------------------------------------------------
We have met the enemy and he is us - Pogo

---

### Post by _duncan_ on 2007-07-31
Try this using gnome-ppp:

1. click the 'Setup' button, then choose the 'Options' tab.
2. Make sure 'check carrier line' option is NOT checked.
3. Make sure 'Ignore terminal strings (stupid mode)' option is checked.
4. Try dialing out again.

---

### Post by Pogo_VA on 2007-07-31
Thanks _duncan_, I'll give that a try at some point.

BTW; When I was wandering through the threads, I found a post by RxRated who's got a Toshiba laptop with SmartLink and the same problem although things were working for him under Dapper.

When I tried his suggestion about:

$ sudo /etc/init.d/sl-modem-daemon restart 

the NO CARRIER went away, but now I'm getting NO ANSWER then the connection drops. It sounds as though there's some handshaking issues that still need resolution. Hmmm??

-----------------------------------------
We have met the enemy and he is us - Pogo

---

