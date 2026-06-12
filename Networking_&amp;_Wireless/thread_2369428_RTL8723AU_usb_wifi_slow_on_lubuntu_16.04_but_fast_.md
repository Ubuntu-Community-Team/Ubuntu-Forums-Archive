---
title: "RTL8723AU usb wifi slow on lubuntu 16.04 but fast on windows 8.1"
date: 2017-08-23
forum: Networking &amp; Wireless
---

### Post by wuziq on 2017-08-23
From the same spot by my router, I get about 1-2Mbps down from Lubuntu, but about 40Mbps from Windows 8.1.  This is on a Lenovo Yoga 13, FWIW.

Here's the wireless-info output:  [http://paste.ubuntu.com/25374207/](http://paste.ubuntu.com/25374207/)

I've tried installing the rtl8723au driver from lwfinger ([https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)), which seems to be a solution at least for older versions of Ubuntu.  However, I'm not sure that I'm doing the correct thing.  I ran the commands provided on the github readme:

```

cd rtl8723au/
make
sudo make install
sudo modprobe 8723au

```

all of which succeeded, but I think the rtl8xxxu driver was still being used after reboot:

```

wuziq@wuziq-lubuntu:~/temp$ lsmod | grep rtl8xxxu
rtl8xxxu              126976  0
mac80211              782336  1 rtl8xxxu

wuziq@wuziq-lubuntu:~/temp$ lsmod | grep 8723
8723au                892928  0

```

I then tried blacklisting the rtl8xxxu driver:

```
echo "blacklist rtl8xxxu" >> /etc/modprobe.d/blacklist.conf
```

but then no wireless interface loaded after reboot, and NetworkManager just showed the two x's.

Assuming that I should be using the lwfinger driver, am I doing the right things, or is there something I'm missing?

If I shouldn't be using the lwfinger driver, what should I be doing instead?

I've also tried someone's suggestion of unloading and reloading the rtl8xxxu module, but that didn't help.

Does anyone have any ideas?  Is this just a known issue?

---

### Post by wuziq on 2017-08-25
bump..  let me know whether there's more information I should provide..

---

### Post by wuziq on 2017-08-29
any ideas for this one?

---

### Post by praseodym on 2017-08-31
Lets see
```

sudo modprobe -rfv rtl8xxxu 8723au
sudo modprobe -v 8723au
sudo depmod -a
sudo update-initramfs -u -k all
```
Reboot

---

