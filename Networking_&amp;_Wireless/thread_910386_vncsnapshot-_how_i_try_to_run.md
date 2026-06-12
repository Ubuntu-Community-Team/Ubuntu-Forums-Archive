---
title: "vncsnapshot- how i try to run?"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Dark Wolf on 2008-09-04
Hi

I have a problem with the vncsnapshot. I will try to get a screenshot from a vncsession. 

```
vncsnapshot 192.134.20.3 test.jpg
```

```
VNC server supports protocol version 3.7 (viewer 3.3)
No authentication needed
Desktop name ""
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 0 green 8 blue 16
Unknown message type 109 from VNC server
Image saved from (local host) 1280x1024 screen to test using 1280x1024+0+0 rectangle
```


But all what i see is grey colour on the picture. What is wrong? 

Greetings 
Dark Wolf

---

### Post by HermanAB on 2008-09-04
Can't you just do an ordinary session and use ksnapshot or similar?

---

### Post by Dark Wolf on 2008-09-04
No, i can't start so. It is a virtual server over XEN. 
Another option is directly over X, but since the networktraffic would be very quickly too high.

Greetings
Dark Wolf

---

