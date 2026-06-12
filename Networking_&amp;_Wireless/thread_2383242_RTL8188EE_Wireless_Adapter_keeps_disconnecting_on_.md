---
title: "RTL8188EE Wireless Adapter keeps disconnecting on lubuntu 16.04"
date: 2018-01-22
forum: Networking &amp; Wireless
---

### Post by brandan13 on 2018-01-22
I was going to try this, but the github page says it doesn't support ubuntu. [https://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04](https://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04)

```

  *-network
       description: Wireless interface
       product: RTL8188EE Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 01
       serial: f0:03:8c:0d:e3:17
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8188ee driverversion=4.4.0-109-generic firmware=N/A ip=192.168.1.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:130 ioport:3000(size=256) memory:b1100000-b1103fff

```

---

### Post by chili555 on 2018-01-22
First of all, it's a bit tricky to use a 3 1/2 year old post to try to fix a problem today. Second, the github repo doesn't say it doesn't work with Ubuntu; it says:> This code will build on any kernel 4.2 and newer as long as the distro has not modified any of the kernel APIs. IF YOU RUN UBUNTU, YOU CAN BE ASSURED THAT THE APIs HAVE CHANGED. NO, I WILL NOT MODIFY THE SOURCE FOR YOU. YOU ARE ON YOUR OWN!!!!!The question isn't whether it will *work*; the question is whether it will _build._

It is easy enough to find out. It costs nothing to install the prerequisites, clone the repo and run 'make' to see what happens.```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
```What happened? Was there a train wreck of errors and warnings? Or did it build perfectly, as it did for me?```
<snip>
  LD [M]  /home/chili/rtlwifi_new/rtl8822be/rtl8822be.ko
  CC      /home/chili/rtlwifi_new/rtl_pci.mod.o
  LD [M]  /home/chili/rtlwifi_new/rtl_pci.ko
  CC      /home/chili/rtlwifi_new/rtl_usb.mod.o
  LD [M]  /home/chili/rtlwifi_new/rtl_usb.ko
  CC      /home/chili/rtlwifi_new/rtlwifi.mod.o
  LD [M]  /home/chili/rtlwifi_new/rtlwifi.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.13.0-25-generic'

```If it builds, then install it: ```
sudo make install
```Reboot and tell us if there is any improvement.

Chili's semi-annual rant:

It is remarkable to me that many Ubuntu users, when they encounter a problem, most often try to install a different driver. It is even more remarkable that many seek to install an OLDER driver. One smiling newbie asked about a driver written for kernel version 2.4! The last time I used kernel version 2.4, my beard wasn't even white yet!

I assure all of you gentle readers that slapping the wheel from a 1949 Ford on your sleek black 2018 BMW isn't going to make the ride smoother.

In fact, there are several reasons that our connections may drop and almost none of them are the fault of the driver. rtlwifi_new is the one driver I know of that might actually help.

End rant. I feel better now.

---

### Post by brandan13 on 2018-01-22
That made it so that wifi doesn't work. So I uninstalled and that made wifi work again. I had an external wifi adapter and that didn't disconnect all the time, but that broke.

---

### Post by brandan13 on 2018-01-22
maybe I should get a new external wifi adapter and the problem is just walls.

---

### Post by chili555 on 2018-01-22
> That made it so that wifi doesn't work.That's precious little to work on.

If you'd care to troubleshoot, reinstall it, reboot and run:```
sudo modprobe rtl8188ee && dmesg | grep rtl
```If not, we'll have other suggestions. In that case, post the diagnostic data from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by brandan13 on 2018-01-23
without the driver: [https://pastebin.com/1g2C9jvw](https://pastebin.com/1g2C9jvw)

when I ran: "sudo modprobe -v rtl8188ee" I got this

```

insmod /lib/modules/4.4.0-109-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8188ee': Required key not available

```

probably why it's not working. I'll figure out, when I wake up tomorrow.

---

### Post by chili555 on 2018-01-23
Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by brandan13 on 2018-01-26
Which directory would I sign?

---

### Post by chili555 on 2018-01-26
There is no way that I know of to sign the driver. I suggest that you disable Secure Boot.

---

