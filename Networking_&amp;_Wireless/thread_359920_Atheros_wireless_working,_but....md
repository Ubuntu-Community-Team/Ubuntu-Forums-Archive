---
title: "Atheros wireless working, but..."
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by bimpes on 2007-02-12
First post from a newbie. 

I am using Ubuntu 6.10 on a Toshiba laptop with an Atheros wireless card. The card works fine, but my two year old loves to turn off the switch on the side of the computer, disabling the wireless. In Windows, when I turned the wireless back on, my wireless connection would re-establish also, but Ubuntu does not seem to have this process automated, and the only thing I know how to do is to restart my computer each time. What should I do? 

Thanks

---

### Post by spd106 on 2007-02-12
First try this command at a terminal ```
sudo /etc/init.d/networking restart
```
If that's no good then try reloading the kernel modules with ```
sudo modprobe -r ath_pci
sudo modprobe ath_pci
```

---

