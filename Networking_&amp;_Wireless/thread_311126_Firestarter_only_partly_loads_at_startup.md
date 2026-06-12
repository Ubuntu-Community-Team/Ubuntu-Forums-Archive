---
title: "Firestarter only partly loads at startup"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by argusBR on 2006-12-02
I always thought Firestarter was loading at startup, for when I type

 ```
sudo /etc/init.d/firestarter status
```

I get
```

 * Firestarter is running...
```

I was surprised, however, when I probed my machine with "Shields Up!" ([www.grc.com)](www.grc.com)), and it told me that some ports were not stealth (only closed), and that some (like 8080) were open.

Then, I ran the Firestarter GUI (System->Administration->Firestarter) and voilà! After that, Shields Up told me all ports were stealth.

It seems that Firestarter is not loading properly at startup, for when I type 

```
ps aux|grep firestarter
```

before running manually the GUI, I only get get

```
argus   5544  0.0  0.1   1956   768 pts/0    S+   14:27   0:00 grep firestarter
```

What may be happening?

---

