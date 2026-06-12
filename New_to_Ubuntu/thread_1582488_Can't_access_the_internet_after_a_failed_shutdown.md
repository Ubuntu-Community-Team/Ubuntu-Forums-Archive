---
title: "Can't access the internet after a failed shutdown"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by MHC on 2010-09-26
This is my second day with Ubuntu, having got 10.04 LTS installed on my new PC. It worked well for a day, then did not shut down properly. After turning the power off manually, then re-booting some hours later, neither Chrome nor Firefox could access the internet. I re-started Ubuntu with its own power button, which seemed to work OK. But still no internet. It worked before the failed shutdown, and there are no problems getting the internet with Windows with the same network (that's how I am posting this!) Can anyone help me?

---

### Post by xircon on 2010-09-26
Try:
```
cat /var/lib/NetworkManager/NetworkManager.state
```

If this shows:
```
[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

``` 

Then edit the file and change anything that says false to true:

```
gksu gedit /var/lib/NetworkManager/NetworkManager.state
```

Then reboot.

---

### Post by MHC on 2010-09-26
Brilliant! Thanks for your help Xircon. That's fixed it.

---

### Post by xircon on 2010-09-26
No problems.  Had the same problem, bit of a pain not being able to suspend my computer though.  Hope the bug is sorted out in Maverick, waiting to update as soon as the ATI problem is sorted completely first.

---

