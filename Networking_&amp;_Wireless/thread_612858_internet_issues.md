---
title: "internet issues"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by Chymera on 2007-11-14
Ok, so I'm getting the following symptoms, once in a while my internet connection gets interrupted, ie. the browser tells me it cannot locate the hosts i'm trying to access, and ping [www.google.com](www.google.com) times out :-/

Now, i would usually take it as a sign of faulty handling of pppoe, since I know my internet connection is alright, however I do get some strange behavior: Even though everything else points to the fact that the connection is closed, my IM client, pidgin, runs without any problem, i can send and receive messages, and I don't get any complaints from it at all...

Any thoughts on this?

---

### Post by stevux on 2007-11-14
a 'working' IM client does not necessarily mean  you have no network issues. the protocol most likely has a way of trying to resend until it succeeds.

first, have a look at *where* your problem is.
you can do this with *mtr* 
**[COLOR="Red"]sudo apt-get install mtr[/COLOR]** and run 'mtr [www.google.com](www.google.com)'
if the gross of packet loss occurs before you exit your homenetwork, it's YOU. else, get on the phone with your ISP..

what could really help you out it a network trace from your pc.
**[COLOR="Red"]sudo apt-get installl wireshark[/COLOR]** and run as root, then start capturing, do something that does not work properly (like ping, or het a http page), then stop capturing, and see if there is something noteworthy in the trace (there should be some coloring for the less gifted).
if you're running pppoe on the local lan, you might have a problem with 'lost fragments'. If this is the case you will have to consult your ISP on the settings for your network.

hth,

---

### Post by Chymera on 2007-11-15
by "YOU" do you mean ubuntu?

---

