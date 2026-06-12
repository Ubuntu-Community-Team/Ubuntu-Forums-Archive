---
title: "Very slow boot due to networking.service on 16.10 on Dell XPS 9550"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by mark-bobak on 2016-11-06
Hi all,

Freshly installed Ubuntu 16.10 on Dell XPS 15 9550.

Boot is *really* slow.

```
mjb@hawking:~$ sudo systemd-analyze blame
     5min 2.702s networking.service
          1.956s lightdm.service
          1.954s plymouth-quit-wait.service
          1.524s ModemManager.service
          1.520s vboxdrv.service
          1.519s click-system-hooks.service
          1.483s NetworkManager.service
          1.474s snapd.firstboot.service
          1.474s apparmor.service
          1.472s ebtables.service
          1.470s lxd-containers.service
          1.467s systemd-timesyncd.service
          1.460s lxd.socket
          1.459s snapd.socket
          1.244s gpu-manager.service
          1.007s NetworkManager-wait-online.service

```
It's pretty clear that networking.service is the culprit.

Any thoughts or suggestions as to my next move?

I should add, once it does boot up, everything looks fine, networking works fine.

Thanks,

-Mark

---

### Post by mark-bobak on 2016-11-12
Still struggling with this....not having any luck figuring out how to profile networking.service.

---

### Post by wildmanne39 on 2016-11-12
Please try:
```
systemctl disable NetworkManager-wait-online.service
```
and report back if this works or not.
Thanks

---

### Post by mark-bobak on 2016-11-12
No joy.  > systemd-analyze blame still show 5min on networking.service.

---

### Post by mark-bobak on 2016-11-12
Ok, I'm not sure if this is a solution, or a workaround, but it worked for me.

I did:
```
 sudo vi /lib/systemd/system/networking.service

```and I changed:
```
TimeoutStartSec=5min
```
to
```
TimeoutStartSec=10sec

```I still have no idea what is timing out or why, but this solves the slow boot problem, and didn't seem to have any adverse effect.

-Mark

---

