---
title: "Reduced wirless throughput on Ubuntu 17.10 compared to Windows"
date: 2018-01-29
forum: Networking &amp; Wireless
---

### Post by abe-stew on 2018-01-29
I have been experiencing much reduced wireless throughput on Ubuntu compared to Windows. On Ubuntu my wireless download speed tends to max out around 7Mb/s (ranges from 6-8Mb/s) and upload barely breaks 200Kb/s. On Windows, using rough estimates as I deleted my Windows partition, speeds were around 20-30Mb/s and at least a couple Mb/s upload. 

Following the instructions from the pinned thread I have uploaded my wireless.info.txt to [http://paste.ubuntu.com/26485791/](http://paste.ubuntu.com/26485791/). Please let me know if you require any further info, and what commands I need to use to get it.

---

### Post by praseodym on 2018-01-30
Lets try

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```

---

### Post by abe-stew on 2018-02-02
Thanks for the reply. Unfortunately download and upload throughput appear to be the same.

---

### Post by abe-stew on 2018-02-15
*bump* - anyone know anything else that might be worth trying?

---

