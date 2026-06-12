---
title: "Security risk?"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by stainblue on 2009-01-24
First off, hello! Im new. :)

But it seem that everyone here is friendly and helpful so im going to give this a shot.

this morning in my auth.log after I woke up at about 10am i saw this.

```
Jan 24 07:36:15 Stains-Box sudo:     root : TTY=unknown ; PWD=/ ; USER=stainblue ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jan 24 07:36:15 Stains-Box sudo:     root : TTY=unknown ; PWD=/ ; USER=stainblue ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jan 24 07:36:15 Stains-Box sudo:     root : TTY=unknown ; PWD=/ ; USER=stainblue ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
``` 

Can someone shed some light on what took place and if its normal?
I have a normal wifi network with no proxies involved.

---

### Post by SunnyRabbiera on 2009-01-24
Stuff like this happens all the time on any OS that connects to the net, for the paranoid try firestarter

---

