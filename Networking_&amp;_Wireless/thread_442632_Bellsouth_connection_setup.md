---
title: "Bellsouth connection setup"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by falonyn on 2007-05-13
Okay, my brother is running Ubuntu Edgy Eft. It was installed on his system while his computer wasn't connected to the internet. He is now trying to get his internet connection working but neither of us know how to get it up and running. 

His connection runs straight from the wall to his computer, and requires a special connection program through windows. (what I am saying is that it almost seems like dial-up, but it is dsl). 

Do any of you know how to set this up?

---

### Post by PilotJLR on 2007-05-13
He just needs a PPPoE client.
Try this:

```

sudo pppoeconf

```

---

