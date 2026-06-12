---
title: "[SOLVED] wireless works but oddly"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by thantos on 2008-01-24
So here is the deal:

1.  My wireless works; however, if I do not use the internet for a period of about 5 mins.
    my wireless stops working.  I work around this by pinging my wireless router every 4
    4 minutes; however, I do not understand why this is happening and would like to know
    if there is a better solution than what I have come up with.

   Wireless info:
   -Using ndiswrapper driver for Broadcom 48xx
   -Wireless is WPA-PSK

If there is any other info that would be helpful please ask.


2. I have to restart my wireless interface upon logging into ubuntu.
    For some reason it doesn't connect the first time and uses the ava settings
    (I think that is what it is called).   I think I saw this in the forums so not a big
    deal but thought I would mention it.

Edit:

I fixed both issues:

1.  Just made a startup script to ping my router (not so good for a mobile device, but since the only time I have issues is at home, no biggie).

2.  For some reason after I edited my /etc/interfaces file to use a script to choose how to set-up my wireless, it works just fine.

---

