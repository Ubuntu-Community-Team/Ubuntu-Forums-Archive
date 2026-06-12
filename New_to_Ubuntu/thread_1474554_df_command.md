---
title: "df command"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Franz01 on 2010-05-06
I ran a df command and I got the following:

```

root@xxxxxxx:/dev# df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1      33506948   6698828  25106036  22%   /
varrun         257688     92       257596    1%   /var/run
varlock        257688     0        257688    0%   /var/lock
procbususb     257688     257676   12        **100% ** /proc/bus/usb
udev           257688     257676    12       **100%** /
devdevshm      257688     0         257688    0%   / dev/shm

```

What about this 100% disk space (4th and 5th line)?

---

### Post by kpkeerthi on 2010-05-06
Those two are virtual filesystems (and not some space occupied on your HDD) and there is no reason to worry about it. Relax. :)

---

