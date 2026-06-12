---
title: "deluge it taking up all my bandwith"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by blake7 on 2009-05-13
hi using deluge even thoe it not using all the bandswith (accouding to deluge)my computer can down load web pages it just times out

can you help

thank you

---

### Post by MrWES on 2009-05-13
> **blake7 said:**
> hi using deluge even thoe it not using all the bandswith (accouding to deluge)my computer can down load web pages it just times out

can you help

thank you

Hrmm..well if you're behind a router, and it has a QoS (Quality of Service) feature, you can set it to give certain internet connections priority -- like DNS and http. I have a linksys router running a third party firmware called Tomato and it has a terrific QoS service.

~Bill

---

### Post by blake7 on 2009-05-13
really and thats the easist way of doing it???/ps what does behind the router mean

---

### Post by blueridgedog on 2009-05-13
This works, but is pretty granular:

[http://freshmeat.net/projects/trickle/?topic_id=87](http://freshmeat.net/projects/trickle/?topic_id=87)

---

### Post by Ragnar Bocephus on 2009-05-13
> **blake7 said:**
> really and thats the easist way of doing it???/ps what does behind the router mean

I would try setting an upload speed cap in Deluge's preferences dialog.  What are the rated up/down speeds for your connection?

---

### Post by lavinog on 2009-05-13
Reduce the max number of connections.
Some routers can't handle more than 50+ connections.

---

### Post by MrWES on 2009-05-13
> **lavinog said:**
> Reduce the max number of connections.
Some routers can't handle more than 50+ connections.

Better yet, leech your torrents while you sleep :)

~Bill

---

### Post by aeiah on 2009-05-13
my up speed is 125kb/s and i find limiting deluge's upload to 110 usually does the trick. upload of course doesnt affect download speed but maxing out your upload will slow down the initial connection to the website.

---

### Post by lavinog on 2009-05-13
You can always download a torrent of the internet and store it in your browser cache

---

### Post by blake7 on 2009-05-14
thanks i put the max connectioons to 49 and that now works fine,,

thankyou all for your time and experience

---

