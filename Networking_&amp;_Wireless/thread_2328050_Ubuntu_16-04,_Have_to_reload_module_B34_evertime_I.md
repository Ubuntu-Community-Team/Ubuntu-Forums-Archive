---
title: "Ubuntu 16-04, Have to reload module B34 evertime I reboot"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by adellaci on 2016-06-16
I have a HP ZD8000 laptop, with a broadcom BCM4306 rev3 wireless adapter. I have installed firmware-b43-installer, b43-fwcutter and ran the command
```
sudo modprobe b43
```

My network adapter was recognized and wireless networks started showing up. I've connected to my WIFI (using that laptop and wireless network to write this question)

Then ran
```
sudo -i
echo b43  >>  /etc/modules
exit
```

I then edited 
```
/etc/modprobe.d/blacklist.conf
```

Yet every time i restart my machine i have to issue modprobe command to get my wireless card to work. My wireless work just fine with Ubuntu 14.04.

What have i forgotten?

---

### Post by jeremy31 on 2016-06-17
I would bet another blacklist file is to blame
```
for f in /etc/modprobe.d/*; do echo $f; cat $f | grep b43; done
```

---

### Post by adellaci on 2016-06-17
Thank you Jeremy that is exactly what the problem was, in two file

```
/etc/modprobe.d/broadcom-sta-common.conf
blacklist b43
blacklist b43legacy
/etc/modprobe.d/broadcom-sta-dkms.conf
blacklist b43
blacklist b43legacy
```

---

### Post by jeremy31 on 2016-06-18
Those should be removed by uninstalling the packages ```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

---

