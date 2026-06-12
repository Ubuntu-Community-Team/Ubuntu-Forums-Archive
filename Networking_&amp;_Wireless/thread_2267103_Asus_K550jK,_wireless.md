---
title: "Asus K550jK, wireless"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by probebly on 2015-02-27
Hey guys...

I bought a new laptop (Asus K550jK) and the only OS I use is Ubuntu 14.10...
Everything is working fine except for the wireless. I can connect to my home network but it keeps disconnecting and the only way to connect it again is by restarting the computer.
It is driving me mad because when I'm downloading something for example it disconnects with no aparent cause.

Help me please.
Thanks

Wireless card: RTL8821AE 802.11ac PCIe Wireless Network Adapter
RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

---

### Post by jeremy31 on 2015-02-27
Try this first then restart computer ```
echo "options rtl8821ae fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```

If you see no improvement then ```
sudo rm /etc/modprobe.d/rtl8821ae.conf
```

And then try the backports, enter just one line at a time


```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz
tar -xf backports-3.18.1-1.tar.xz
cd ~/Desktop/backports-3.18-1
make defconfig-rtlwifi
make
sudo make install
```

Reboot

---

### Post by probebly on 2015-02-28
jeremy31, thank you for your reply... i tried the first command and saw no improvement.
then, i used the commands below and i got an error when i used this one "cd ~/Desktop/backports-3.18-1" saying that the directory wasn't found.

---

### Post by jeremy31 on 2015-02-28
> **probebly said:**
> jeremy31, thank you for your reply... i tried the first command and saw no improvement.
then, i used the commands below and i got an error when i used this one "cd ~/Desktop/backports-3.18-1" saying that the directory wasn't found.
Edited the other post to fix

---

