---
title: "Ubuntu only running ipv6, needs to be running ipv4."
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Keatonguy on 2008-06-05
I've got this ubuntu 8.04 box I installed literally yesterday, so it's totally vanilla. I try to install the edubuntu disk, and in turn I realize that the network isn't working. Turns out it's running ipv6 but not ipv4, and our network dosen't support ipv6.

So, can anyone tell me how to fix this?

---

### Post by prshah on 2008-06-05
> **Keatonguy said:**
>  Turns out it's running ipv6 but not ipv4, and our network dosen't support ipv6.
So, can anyone tell me how to fix this?

Add the following line to the end of your "/etc/modprobe.d/blacklist" file:
```

blacklist ipv6

```

Then reboot.

Post for further advice if you don't know/can't edit "/etc/modprobe.d/blacklist" file.

---

