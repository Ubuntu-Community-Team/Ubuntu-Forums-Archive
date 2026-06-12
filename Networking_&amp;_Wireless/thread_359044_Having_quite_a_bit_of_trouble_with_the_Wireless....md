---
title: "Having quite a bit of trouble with the Wireless..."
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Blazingsun20 on 2007-02-11
Here is the situation. First though the computer stats:

Compaq Presario V2000
AMD Turion 1.6 GHz 
60 GB HD
According to Ubuntu--Broadcom 4318 Wireless card

I have gone through the wiki on how to get the light to come on and all of that other stuff, but for some reason I cannot connect to any wireless connections. Ubuntu recognizes that there is a card there and my wireless light is on. What could be the issue? I did some searching here on the forums and unless I missed something, I didn't see anything about this situation. Any and all help will be appreciated. I am sort of new to Linux as well. Thanks all!

---

### Post by Blazingsun20 on 2007-02-11
Well I figured out what was wrong with it. If you ever encounter this problem, just open up a terminal and run:

sudo modprobe ndiswrapper

And then restart. Works beautifully!

---

