---
title: "dialing up but can't connect"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by pollinator on 2008-11-21
I am reasonably new to ubuntu and have been trying to get dial-up to work correctly. I'm using a pcmcia card which dials out fine but can't negotiate with the isp(iguess). See the attached gnome ppp connections log; it seems like there may be an access problem?
I'm at witts end . .

---

### Post by jonobr on 2008-11-21
OK, Im just looking through your logs and here is what I can see,
(Im not familiar with the dialer, just commenting on your logs and explaining some things you should see and hear)

Your actual modem calls to the ISP. (I tried the number and tone sounds fine)
The ISP is using an ascent TNT remote access box.

I know ascent TNT ended up with Alcatel lucent.
However, Im thinking this box your connecting to is old.

Anyway, where it says V90/V42 bis, ARQ yadda yadda, these are the negotiation speeds and control protocols negotiated between the endpoints.
It seems to agree to these protocols on the TNT side.

Im guessing you hear the modem negotiation and its getting v90, 
(V90 has a very distinctive boing-boing at the end of the negotiation, its like a sonar ping on the line to ensure its a good enough quality to support the faster data rate. If it failed it would fallback to V34.)

I digress. I am guessing after the two boings, the negotiation stops and then its just sitting there and sitting there and then does nothing until it hangs.

It appears your end is trying to send PPP (point to point protocol- this is what enscapsulates IP datagrams into packets to send across the link) and it appears you TNT is rejecting it.

Im thinking a few things,
1) I dont see any authentication mechanism on the command line and byu defualt it seems to use another config file, it may be irrelavant and handled by the application.
2) The TNT reject the request for PPP negotiation and then pppd is tried.
You then get it trying PAP ( a basic form of authentication) and CHAP ( a more advanced form of authentication) and it fails indicating problems .

This almost looks as if there are authentication problems when using PAP or Chap.
The only thing I could recommend is doing a dial up networing connection with another  dial up client to verify your user name and password.
If they both work then I would compare to what you have in your dialer for this OS.

---

