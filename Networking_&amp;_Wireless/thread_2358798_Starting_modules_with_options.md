---
title: "Starting modules with options"
date: 2017-04-17
forum: Networking &amp; Wireless
---

### Post by maxrpowell on 2017-04-17
To fix a wireless issue I built an updated version of a driver from source and am removing the driver and restarting with a parameter using:

```
sudo modprobe -rv rtl8723ae
```
```
sudo modprobe -v rtl8723ae ant_sel=2
```

This has solved my wireless issue but I have to manually enter this every time I reboot. I could probably find a way to do this automatically but I would like to do it the right way. What is the appropriate way to have this driver load with that option on boot?

---

### Post by wildmanne39 on 2017-04-17
```
echo "options rtl8723ae ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723ae.conf
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae

```

---

### Post by wildmanne39 on 2017-04-17
*Thread moved to **Networking & Wireless**.*

---

### Post by maxrpowell on 2017-04-17
Thank you wild man for all the help to me/others with these wireless issues. Really appreciate it.

---

### Post by wildmanne39 on 2017-04-17
I am glad I could help solve your wireless issue, and I am sorry I did not get back to you last night it was late and I was to tired.

Your welcome and enjoy!:)

---

