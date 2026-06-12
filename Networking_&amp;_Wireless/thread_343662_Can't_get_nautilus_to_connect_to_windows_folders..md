---
title: "Can't get nautilus to connect to windows folders."
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Royle on 2007-01-21
I'm trying to connect to my windows shares on on my networked computers.  If I got to network in nautilus and click on windows network, there is nothing there.  I tried connecting like this as well
```
smb://192.168.0.100/
```
but that didn't come up with anything either.  I just installed ubuntu and do have internet working.  Have I forgotten to do something or is something else wrong?  Any help is greatly appreciated.

---

### Post by jpeddicord on 2007-01-21
I have always had to have my Windows username in the URL in addition to the IP. You add it right before it, like so:
```
smb://username@192.168.0.100/
```

If you have a password on your Windows PC, then it *should* ask you for it.

Jacob

---

