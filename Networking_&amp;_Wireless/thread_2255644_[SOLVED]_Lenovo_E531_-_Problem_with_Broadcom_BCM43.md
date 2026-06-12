---
title: "[SOLVED] Lenovo E531 - Problem with Broadcom BCM43228 WiFi on 14.04"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by Laoch on 2014-12-06
I am having problems with the BCM43228 WiFi card. It was fine on the previous release of Ubuntu. 

I used [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers) as the basis of my work.


```

$ sudo lspci -nn |grep Broadcom
04:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

```


I therefore decided to use the bcmwl-kernel-source package.

```

$ sudo apt-get update
$ sudo apt-get install linux-headers-generic
$ sudo apt-get install bcmwl-kernel-source

```

However after a reboot, no wireless interface.

I then executed the following and the interface came up but after a reboot it was down again and I find myself having to run these modprobe commands each time to get the interface up.


```

$ sudo modprobe -r b43 ssb wl
$ sudo modprobe wl

```

---

### Post by carl4926 on 2014-12-06
```
sudo modprobe -v wl
```will insert the module
You may have to wait a min
Or just reboot

FYI
You device is supported with b43 from kernel 3.17+

---

### Post by Laoch on 2014-12-06
I figured it out. The /etc/modules file was causing the **b43** driver to load before the **wl** driver. By hashing out the **b43** driver in that file the **wl** driver loads successfully.

```

$ lspci -vvnn | grep -A 9 Network

Broadcom Corporation BCM43228 802.11a/b/g/n
Kernel driver in use: bcma-pci-bridge

```

```

$ sudo apt-get update
$ sudo apt-get install linux-headers-generic
$ sudo apt-get install bcmwl-kernel-source

```

Edit the file** /etc/modules**

Hash out the line **b43** and reboot.

```

$ sudo sed -i.bak 's/b43/#b43/g' /etc/modules
$ sudo reboot

```

---

### Post by Laoch on 2014-12-06
Having said all that I don't quite know why **b43** was loading in the first place as it was supposed to be blacklisted.

```

$ cat /etc/modprobe.d/blacklist-bcm43.conf |grep b43
blacklist b43
blacklist b43legacy

```

---

### Post by carl4926 on 2014-12-07
Correct
b43 should be blacklisted once wl has been installed
I didn't have any trouble myself

---

