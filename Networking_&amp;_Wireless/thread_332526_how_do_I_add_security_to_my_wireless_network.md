---
title: "how do I add security to my wireless network?"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-01-06
I've finally got my ad-hoc wireless network running perfectly, all machines can access the net/samba/ssh and everything is looking good.

Now I want to add some security, like a password to connect and maybe some sort of encryption.

Keep in mind that this is an **ad-hoc** network, no AP.

Any help appreciated.

Regards, KEv :)

---

### Post by spd106 on 2007-01-06
AFAIK there's no difference. As long as you have the same key WEP should work fine. I've set one up before with WEP, no trouble.

Not sure about WPA though. Might be ok with PSK, but for anything more I can't really see why you would have an authentication server and not use infrastructure mode.

You could always use ssh to tunnel the connections over the open network. There are guides in the wiki and plenty of threads in this forum.

---

