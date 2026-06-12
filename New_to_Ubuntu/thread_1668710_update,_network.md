---
title: "update, network"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Chuck_W on 2011-01-16
Just installed 10.04 LTS on a Dell Inspiron 6000. Went well but when the updates came it stalled at 130 of 198 files. The log said "Somthing Wicked happened resolving xxx. No address associated with hostname" and "Failed to fetch xxx unable to connect to us.archive.ubuntu.com :http: [91.189.88.46 80]" Is this a server problem that will resolve in time? Or is there something I need to do?

Also I want to have it so that at home it goes to my wired network, looks for a wireless connection at a wi-fi hotspot and does without a network connection sometimes. Is this possible?

Thanks

---

### Post by kn0w-b1nary on 2011-01-16
> **Chuck_W said:**
> Also I want to have it so that at home it goes to my wired network, looks for a wireless connection at a wi-fi hotspot and does without a network connection sometimes. Is this possible?

Thanks

As long as I have connected to WiFi before, it always searches. So... it should work. :)

---

### Post by cariboo on 2011-01-16
Try updating the sources list:

```
sudo apt-get update
```

and try again.

---

### Post by Chuck_W on 2011-01-17
Haven't had a chance to try that. Sounds easy enough.
Thanks

---

### Post by Chuck_W on 2011-01-17
Worked like a charm. Should have thought of that. I've used that command many times!
Thanks

---

