---
title: "can anyone tell me why localhost doesn't exist..."
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by vivichrist on 2008-06-28
can anyone tell me why localhost doesn't exist when I disconect from the network? thhis problem I fixed by modifying '/etc/hosts' to look like my other machines:

```

127.0.0.1 laptop

...etc
```
to:
```
127.0.0.1 localhost
127.0.1.1 laptop

...etc
```

this is a really bad thing to happen right? because some apps rely on there being localhost? I dont know how this happened, I would be interested to find out though.

---

### Post by HalPomeranz on 2008-06-29
Might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209)

---

### Post by vivichrist on 2008-06-29
true but this only happened recently when I booted disconnected from the internet ... there was no localhost. I would definitly say this is related though and to add that more recently dhcp and roaming stopped working, this could be the router but from what I can tell no one tinkers with it. what I originally thought this was effecting could be something completely different. I've been experiencing really sloe gnome initialisation (could be compiz) and really slow open and save dialogues in gnome. panels and other stuff take forever to appear.

---

### Post by vivichrist on 2008-06-30
I vow never to install proposed updates ever again

---

