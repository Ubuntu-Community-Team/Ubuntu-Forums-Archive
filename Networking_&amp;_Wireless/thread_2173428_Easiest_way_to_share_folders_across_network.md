---
title: "Easiest way to share folders across network?"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by ELD on 2013-09-09
So I am looking to buy a raspberry pi to use on my tv as a media centre, I am wondering what the best way would be to open up a few folders on my computer to anyone on the same network to view and access?

---

### Post by JRV on 2013-11-25
If Linux to Linux:
```

[FILE-MANAGER] sftp://ip-address/pathname

```

Linux to shared Windows folder:
```

[FILE-MANAGER] smb://ip-address/share-name  (Windows hostname might work in place of ip)

```

---

