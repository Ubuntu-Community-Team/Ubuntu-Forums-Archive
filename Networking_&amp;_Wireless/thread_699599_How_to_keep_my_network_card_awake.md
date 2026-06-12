---
title: "How to keep my network card awake?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by Doughy on 2008-02-17
I live on a university campus, and my apartment has direct ethernet connections for internet access.  The network requires a user to log in via a webpage to gain access to the web.  The network periodically pings my computer to see if it is still present, and if it is, it will not require a re-login for at least 24 hours.

Here's my issue.  Every time my computer is idle for a while, my network card falls asleep and stops replying to the pings.  This causes me to have to re-login every time I'm idle for a while.  Furthermore, when I try to log into my computer remotely via SSH, my card is usually asleep so I can't get in.

This just recently became a problem, so I am wondering if some kind of ubuntu update caused it.  A month ago everything worked perfectly.  Anyone know why this may be happening?

My network card is integrated on the intel 965 motherboard.

---

### Post by lluisanunez on 2008-02-17
Its something similar to the wifi connection at my uni. We use Pidgin (Gaim, Amsn...) and it works, even in state "away" or "busy"

---

### Post by Doughy on 2008-02-17
> **lluisanunez said:**
> Its something similar to the wifi connection at my uni. We use Pidgin (Gaim, Amsn...) and it works, even in state "away" or "busy"

I'm not sure I understand what you're saying.  Are you saying that by leaving Pidgin on, your network card stays awake?

---

### Post by lluisanunez on 2008-02-17
Yes, I think Pidgin keeps pingin the network. Try it...

---

### Post by Doughy on 2008-02-18
Ok, I tried Pidgin and it did indeed work.  Thanks lluisanunez.

Now, the question is, how do I fix the problem without a workaround like this?  Is there a setting on my network card that I can change so that it will not become inactive after a certain period of time?  Anyone have a more direct solution.

---

### Post by Hightide on 2008-02-18
Sorry I have wrong input

---

