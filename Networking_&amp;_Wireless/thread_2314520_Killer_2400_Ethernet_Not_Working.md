---
title: "Killer 2400 Ethernet Not Working"
date: 2016-02-21
forum: Networking &amp; Wireless
---

### Post by liam28 on 2016-02-21
[FONT=arial]Hi

I recently have just changed to ubuntu 14.04.4 LTS for study and uni purposes and have instantly ran into the problem of not being able to connect to the internet via my ethernet cable. I have a Asrock Fatal1ty Gaming K6+ motherboard with Killer 2400 Lan. I have found a small temporary fix, I can get it to work by entering:

sudo modprobe alx
echo 1969 e0a1 | sudo tee /sys/bus/pci/drivers/alx/new_id >/dev/null

But as soon as I restart its not working again. Is there a way to get a permanent fix instead of having to retype that in every start up?[/FONT]

---

### Post by jeremy31 on 2016-02-22
```
gksudo gedit /etc/rc.local
```

Then add
```
modprobe alx
echo '1969 e0a1' > /sys/bus/pci/drivers/alx/new_id
```
Above the last line which needs to be exit 0
Save, exit program, reboot

---

