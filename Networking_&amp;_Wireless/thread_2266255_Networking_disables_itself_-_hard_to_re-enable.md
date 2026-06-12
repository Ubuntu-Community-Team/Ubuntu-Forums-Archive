---
title: "Networking disables itself - hard to re-enable"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by jackrubysdog on 2015-02-21
Hi

I hope someone can help me with this as it is driving me spare.

Running Gnone NM on Ubuntu 14.04LTS.

Several times a day, my network disables itself. It can happen at any time, even when I am not using the computer while it is on. Getting it working again is very tough.

When I click "Enable Networking" it re-enables, although Wi-fi is disabled.

When I try and enable Wi-fi the fun begins. When I click "Enable Wi-Fi" the text changes to "Enable _Wi-Fi" (note the underscore) and a tick appears and disappears next to this text. This tick will flash off and on - sometimes every two seconds, sometimes several times a second. The LED on the card indicator blinks from white to orange at the same time.

This will carry on until Wi-fi connects, but more often than not this will last a split second before Networking disables itself again and I am back to step one.

Usually, with perseverance, several attempts and various hardware commands, I can re-establish a connection. This takes 10-20 minutes.

Please help!

Everything you may need to know about my network can be found here:

[http://paste.ubuntu.com/10340364/](http://paste.ubuntu.com/10340364/)

Thanks in advance!

---

### Post by steeldriver on 2015-02-21
Hello and welcome to the forums

Here are a couple of things to try (before the real network gurus stop by):

[LIST]
[*]disable the connection's IPv6 support ('Edit connection' --> 'IPv6  Settings' --> 'Ignore') 
[*]change your router's channel setting - there seem to be 4 or 5 adjacent access points all using the same frequency 
[/LIST]

---

