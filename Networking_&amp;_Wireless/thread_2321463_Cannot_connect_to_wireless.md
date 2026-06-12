---
title: "Cannot connect to wireless"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by Stephen_Hull on 2016-04-22
Like so many others, I am having issues with 14.04 connecting to wireless.  A couple days ago it just stopped working and now it will not let me access the internet.  I am able to connect to the wireless network, but when I open the browser or try to ping I get no internet access.

I have updated everything and am able to access the internet with ethernet but I am not sure how to upload it here.  I have tried to make it a attachment but nothing happens and when I copy and paste it I get a error saying to many images

---

### Post by DM2016 on 2016-04-22
Is it just internet - local network okay wirelessly?  

Anything happened to the wireless drivers?

---

### Post by Stephen_Hull on 2016-04-22
Yes all other devices are fine connecting to the wireless.  I updated my wireless drivers after the problem started, but it did nothing.  

I was doing homework on my comp when the computer disconnected form the wireless and it has not been working since.

---

### Post by jeremy31 on 2016-04-23
Looks like UFW is blocking a lot of traffic from wlan0.  See if wireless works correctly with UFW disabled

---

