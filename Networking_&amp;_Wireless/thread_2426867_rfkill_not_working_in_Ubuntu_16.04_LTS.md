---
title: "rfkill not working in Ubuntu 16.04 LTS"
date: 2019-09-14
forum: Networking &amp; Wireless
---

### Post by trillionaire on 2019-09-14
-$rfkill
The program 'rfkill' is currently not installed. You can install it by typing:
sudo apt install rfkill
-$sudo apt install rfkill
...Unable to locate package rfkill
-$sudo rfkill
sudo: rfkill: command not found

There is a file called rfkill in /dev/, but I can't seem to access it.
Does anyone know of a way to turn on the WiFi switch either by fixing rfkill or some other method?
The hardware button on the laptop is broken.

---

### Post by TheFu on 2019-09-14
```
$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:        16.04
Codename:       xenial
```

rfkill is in:
```
rfkill/xenial-updates,now 0.5-1ubuntu3.1 amd64 [installed]
  tool for enabling and disabling wireless devices

```

---

### Post by pcfan1234 on 2019-09-15
Run ```
sudo apt update
```

---

### Post by TheFu on 2019-09-15
> **pcfan1234 said:**
> Run ```
sudo apt update
```

Excellent point.  We assume that an update/upgrade cycle is run at least every week.

```
sudo apt update && sudo apt upgrade
```

Do that weekly to remain patched until support ends.  From time to time, it might be useful  to run dist-upgrade and about once a month or quarter, run 
```

sudo apt autoremove
sudo apt autoreclean
```

Of course, always make backups before running these commands. Things seldom go wrong, but if/when they do, having a backup that has been validated during a test restore is required.  These forums are full of people working without a net - not having backups - who wish they had backups.

---

