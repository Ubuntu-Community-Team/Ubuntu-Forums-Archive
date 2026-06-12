---
title: "RTL8812BU WiFi do not work,"
date: 2020-05-07
forum: Networking &amp; Wireless
---

### Post by x3ua on 2020-05-07
Should work with this:
[https://github.com/cilynx/rtl88x2bu](https://github.com/cilynx/rtl88x2bu)


```
$ lsmod | grep 88x2bu
88x2bu               2433024  0
cfg80211              716800  1 88x2bu
```

```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"
Linux daw 5.4.0-29-lowlatency #33-Ubuntu SMP PREEMPT Wed Apr 29 15:32:40 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```


```

$ sudo dkms install rtl88x2bu/5.6.1
Module rtl88x2bu/5.6.1 already installed on kernel 5.4.0-29-lowlatency/x86_64

```


Maybe that lowlatency kernel is not supported, what do you think?

---

### Post by chili555 on 2020-05-07
"Wifi do not work" covers a lot of territory. Please start by providing the wireless diagnostics report as outlined here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

