---
title: "Need help with WLAN"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by Lmanovic on 2007-04-28
Hi,

I'm trying to get my wireless connection running on Ubuntu 7.04. But it doesn't seem to be working.

I have a Broadcom 4306 WLAN card and the guys on IRC told me to go to:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Follow that guide and it should work, I've been trying that for ages but I can't get past 5.1

Everytime I do
```

  sudo dpkg -i --force-depends ndisgtk_*.deb

```

I get a broken dependency.

Could anyone help me out?

---

### Post by dbott67 on 2007-04-28
You can try using the native bcmxx drivers.

A pretty popular fix is [located here]("http://ubuntuforums.org/showthread.php?t=405990").

-Dave

---

### Post by Lmanovic on 2007-04-28
> **dbott67 said:**
> You can try using the native bcmxx drivers.

A pretty popular fix is [located here]("http://ubuntuforums.org/showthread.php?t=405990").

-Dave

Right, that was easy :) 

Thanks man, really appreciate it. I was getting pretty frustrated after 3 hours of no progress :p

---

