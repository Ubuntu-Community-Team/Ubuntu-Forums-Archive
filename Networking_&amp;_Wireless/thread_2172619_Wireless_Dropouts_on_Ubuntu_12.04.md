---
title: "Wireless Dropouts on Ubuntu 12.04"
date: 2013-09-05
forum: Networking &amp; Wireless
---

### Post by bavbat on 2013-09-05
Hey all,

I'm experiencing packet loss and high pings while connected to my wireless network. I don't experience this with Windows 7. Both OSs use the rtl8192ce driver.

Here is some data: [http://pastebin.com/VQ1173kW](http://pastebin.com/VQ1173kW)

---

### Post by varunendra on 2013-09-06
Welcome to the forums bavbat ! :)
> **bavbat said:**
> Here is some data: [http://pastebin.com/VQ1173kW](http://pastebin.com/VQ1173kW)

Can you change the encryption mode in the router to pure WPA2-PSK (AES) ? No WPA/WPA2 mixed mode, no TKIP, they don't work nicely with Linux.

In addition to above, please try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y
```

If that alone does not help, unload the driver again (the first command) and reload it with two more parameters - "ips=N" and "fwlps=N". That is -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=Y fwlps=N ips=N
```
Do not reboot after this. These changes are temporary and will be lost at the next boot. If they seem to help, we can make them permanent.

If none of these help improve the connectivity, please follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the detailed report the script generates.

---

