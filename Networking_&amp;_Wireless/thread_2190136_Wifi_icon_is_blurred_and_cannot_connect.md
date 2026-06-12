---
title: "Wifi icon is blurred and cannot connect"
date: 2013-11-25
forum: Networking &amp; Wireless
---

### Post by lovevn on 2013-11-25
Hi all,
I have had a problem for some weeks.
Earlier, I connect to my wifi normally and, every time I turn on my laptop and log in Ubuntu, it connects to wifi automatically.
But now, I cannot connect to my wifi, because the wifi icon is blurred :confused: I must reset tp-link and then I can connect, but it's very inconvenient.
You can see the picture below:
As you see, my wifi is Duc Mai, but it's blurred! What happened? :confused:

---

### Post by praseodym on 2013-11-26
Open the network-manager as sudo-user
```

gksudo nm-connection-editor
```
and tick "connect automatically"

---

### Post by lovevn on 2013-11-27
> **praseodym said:**
> Open the network-manager as sudo-user
```

gksudo nm-connection-editor
```
and tick "connect automatically"
Thank you for reply. But my main problem is I can't click on Duc Mai wi-fi icon - it's blurred even though I ticked "connect automatically" (as you see the picture: others is enable to click to connect, but Duc Mai isn't).
Today, I'm surrprised. Duc Mai wifi icon comes to normal. :)

---

