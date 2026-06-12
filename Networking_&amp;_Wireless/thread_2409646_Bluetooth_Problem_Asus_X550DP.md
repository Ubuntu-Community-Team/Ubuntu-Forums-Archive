---
title: "Bluetooth Problem Asus X550DP"
date: 2019-01-04
forum: Networking &amp; Wireless
---

### Post by gammonjosh on 2019-01-04
Good day,  

I have a small bug or problem that keeps my BT from running normally after a reboot or when I turn BT off then back on.  I've used this post [https://ubuntuforums.org/showthread.php?t=2399393](https://ubuntuforums.org/showthread.php?t=2399393) to get the BT working but I have to re run the following code after a reboot to get it working again? Is there a way to keep it working or do I just have to deal with it?
```
[COLOR=#000000][FONT=&amp]sudo modprobe -v rtbth[/FONT][/COLOR]
``` 
Thanks,

---

### Post by jeremy31 on 2019-01-04
you could try ```
sudo depmod -a
```
Reboot

---

### Post by gammonjosh on 2019-01-04
Sorry didn't work.  But I re run the modprobe and it worked after that reboot.

```
 sudo modprobe -v rtbth
insmod /lib/modules/4.15.0-43-generic/kernel/crypto/ecdh_generic.ko 
insmod /lib/modules/4.15.0-43-generic/kernel/net/bluetooth/bluetooth.ko 
install /sbin/modprobe --ignore-install rtbth; mknod /dev/rtbth c 192 0; /usr/bin/rtbt & 
insmod /lib/modules/4.15.0-43-generic/updates/dkms/rtbth.ko 
gammonjoshua@X550DP:~$ init complete


```

---

### Post by praseodym on 2019-01-05
Force the module to load every boot-up
```

echo rtbth | sudo tee -a /etc/modules
```

---

