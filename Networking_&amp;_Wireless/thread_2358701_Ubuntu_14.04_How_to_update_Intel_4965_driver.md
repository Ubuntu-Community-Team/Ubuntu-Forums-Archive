---
title: "Ubuntu 14.04 How to update Intel 4965 driver"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by bazianm on 2017-04-16
Hi,

I have a laptop with an intel 4965 wireless card. Performance is a little spotty and I was wondering if I might need to update the driver. What happens is that I can't connect to networks that aren't really strong. For example, I am tethered to my cell right now that and works great but to connect to the optimumwifi which is a weaker connection doesn't work.

1) How can I tell the version of which iwl4965 driver in use?
2) How can I update it. I am OK with linux but not a guru and I could a how-to guide.

Thanks in advance!

---

### Post by ajgreeny on 2017-04-16
Try **lspci -k** in terminal which will show the driver of all the pci devices including the wifi card.

---

### Post by bazianm on 2017-04-16
OK. This is what is says:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1120
    Kernel driver in use: iwl4965

Not sure how to read that. Is this the latest version?

---

### Post by wildmanne39 on 2017-04-16
See if this helps:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
it is normal for speeds and connections to get worse the lower the signal, in Ubuntu it is hard to connect under 50 percent strength.

---

