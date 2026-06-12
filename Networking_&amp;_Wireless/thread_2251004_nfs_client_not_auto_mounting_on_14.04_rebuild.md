---
title: "nfs client not auto mounting on 14.04 rebuild"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by hundred1906 on 2014-11-01
My desktop was running a system that had been upgraded over time from a 12.04 install, reaching an up to date 14.04.

Long story why .. but I decided to rebuild from scratch onto a SSD, starting at a new downloaded 14.04. I used my original build notes as a basis.

The old system automounts my nfs server using a FSTAB entry:
```
culture-serve:/mnt/users /culture nfs
```

On the new system this entry does not result in anything being mounted into the /culture position on the client. However I can mount the nfs location manually from the terminal:
```
sudo mount culture-serv:/mnt/users /culture
```

DMESG outputs from both boot processes look similar - both have the "killed by TERM message":
> [    3.840586] [drm] Initialized drm 1.1.0 20060810
[    3.850750] init: idmapd-mounting (/culture) main process (290) killed by TERM signal
[    4.004346] systemd-udevd[369]: renamed network interface eth0 to eth1
[    4.009336] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X

Obviously that is only part of the output.

Could the failure be to do with the eth0/eth1 remapping?

Would appreciate advice on where I go to look for other diagnostics.

---

### Post by bapoumba on 2014-11-01
*Thread moved to **Networking & Wireless**.*

---

### Post by SeijiSensei on 2014-11-02
Looks like a typo in /etc/fstab to me. The command-line entry uses "culture-serv" while the fstab entry uses "culture-serve".

---

### Post by hundred1906 on 2014-11-02
SeijiSensei, thank you so much. I must have stared at that for 12 hours.

---

