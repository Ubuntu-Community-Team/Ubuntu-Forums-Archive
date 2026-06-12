---
title: "Skype on version 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by aroha on 2009-10-31
Hi there everybody !
I am totally newbie at ubuntu and just upgraded from Jaunty J. to
Karmic K.

My question is now about Skype on my netbook acer aspire.
Will you please explain to me, step by step, how I can make skype work on my netbook ?
After I have just signed in and try to make the test call,  message says :
" Problem with audio play back "
I did not happen with the previous version.

Thanks a lot for your help !
Aroha
:popcorn:



"

---

### Post by sdpiowa on 2009-10-31
Is your netbook using Pulse Audio?  That made it a LOT harder for me to configure.

---

### Post by sandyd on 2009-10-31
> **sdpiowa said:**
> Is your netbook using Pulse Audio?  That made it a LOT harder for me to configure.
you have a point.

try
```

sudo apt-get remove pulseaudio*

```
sorry, but im just not a fan of it. (please don't bash me)

---

