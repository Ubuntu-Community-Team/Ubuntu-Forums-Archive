---
title: "HANNSPREE and MSI Wind rt2860"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Peter09 on 2010-05-23
Sort of confused here -
my son and I installed netbook remix on his Hannspree netbook. The wireless driver failed to connect to my network and using google I was unable to resolve the issue.

I decided to use another wireless dongle until I had until a fix came through. However I needed to get rid of the rt2860 driver so I

```
sudo gedit /etc/modprobe.d/blacklist-rt2860.conf
```and inserted the line
blacklist rt2860

I then rebooted to start the setup of my wireless dongle. Imagine my surprise when the internal card connected and worked straight from reboot!

---

