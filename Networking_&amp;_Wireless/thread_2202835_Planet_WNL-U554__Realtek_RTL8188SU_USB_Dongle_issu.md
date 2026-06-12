---
title: "Planet WNL-U554 / Realtek RTL8188SU USB Dongle issue, not connecting."
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by Ob1 on 2014-01-31
I got a Planet WNL-U554, its listed as a 8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter.

It works flawlessly in win8, you just pug it in. Under Linux I plug it in-- it does detect Access Points but it doesn't connect to them. Out of luck I once managed to connect to my router, I had no internet but I could telnet to the router settings. 

What could be wrong? It has native Linux support, it came with some driver that I couldn't compile and I've ordered it to ignore ipv6. But to no avail. My other on-board laptop wlan adapter works, so that can't be it.

---

### Post by praseodym on 2014-01-31
Which Ubuntu version is it?
```

uname -a
```

---

### Post by Ob1 on 2014-01-31
The newest, x86_64.

---

### Post by praseodym on 2014-01-31
Please show
```

lsusb
lsmod
```

---

### Post by Ob1 on 2014-01-31
> **praseodym said:**
> Please show
```

lsusb
lsmod
```

lsusb
Bus 003 Device 005: ID 0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

lsmod
r8712u                170834  0

---

### Post by praseodym on 2014-01-31
The driver should be ok. Check:
[LIST]
[*]
[*]encryption mode: WPA2-AES (CCMP)
[*]fixed channel
[*]network not "hidden"
[*]bandwidth 20MHz instead of 20/40MHz
[/LIST]
Router firmware is up to date?

---

### Post by Ob1 on 2014-02-01
> **praseodym said:**
> The driver should be ok. Check:
[LIST]
[*]
[*]encryption mode: WPA2-AES (CCMP)
[*]fixed channel
[*]network not "hidden"
[*]bandwidth 20MHz instead of 20/40MHz
[/LIST]
Router firmware is up to date?

Can't be any of that since my on-board adapter works like a charm. Could it be something with the driver included with Ubuntu? 
The driver released by the manufacturer was released back in 2011-08-19 and remains the only one so far, so is it a kernel thing then?

I'm having trouble compiling it, hangs shortly after make.

---

### Post by praseodym on 2014-02-01
Yes, this driver is pretty old...Maybe this one?!

[http://media.cdn.ubuntu-de.org/forum/attachments/28/22/2844083-RTL8191SU_usb_linux_v2.6.6.0.20101111.zip](http://media.cdn.ubuntu-de.org/forum/attachments/28/22/2844083-RTL8191SU_usb_linux_v2.6.6.0.20101111.zip)

---

### Post by praseodym on 2014-02-01
Forget that driver, try the backported ones:
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2014/01/24/backports-20140124.tar.gz 
tar -xvf backports-20140124.tar.gz 
cd backports-20140124
make defconfig-rtlwifi
make
sudo make install 
```
Reboot.

---

### Post by Ob1 on 2014-02-03
> **praseodym said:**
> Forget that driver, try the backported ones:
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2014/01/24/backports-20140124.tar.gz 
tar -xvf backports-20140124.tar.gz 
cd backports-20140124
make defconfig-rtlwifi
make
sudo make install 
```
Reboot.

Same result, still doesn't connect. By the way, how do I know that it's overriding the previous driver? 

Moreover, this prevents my on-board driver from working, how do I reverse that?

I don't get this-- the product clearly says "Linux support" on the packaging. Does this mean that it *was* supported on its initial release by an older kernel? Why is that an issue?

---

### Post by praseodym on 2014-02-03
Check which driver is loaded via:
```

modinfo r8712u | egrep 'versi|filen'
locate r8712u | grep lib
```


Uninstall it:```

cd backports-20140124
make clean
make defconfig-rtlwifi
make
sudo make uninstall
```
Compiling the driver worked pretty good with the LTS-kernel 3.2. Maybe the kernel development is faster than the driver development, which causes problems. Checked 12.04.1?

---

### Post by Ob1 on 2014-02-03
> **praseodym said:**
> Check which driver is loaded via:
```

modinfo r8712u | egrep 'versi|filen'
locate r8712u | grep lib
```


It's r8712u. Could they both be different versions of r8712u? 

> **praseodym said:**
> 
Compiling the driver worked pretty good with the LTS-kernel 3.2. Maybe the kernel development is faster than the driver development, which causes problems. Checked 12.04.1?


What does that mean in noobspeak? :)

btw thanks for the help

---

### Post by praseodym on 2014-02-03
Downgrade the kernel:
```

sudo apt-get install --reinstall linux-image-generic linux-headers-generic build-essential dkms linux-tools
```
Reboot, press SHIFT during boot-up and choose kernel 3.2 under "previous ubuntu versions". Try to compile there again.

If it works we can uninstall the other kernel or set 3.2 as default. Dont get nervous, 3.2 is the Long-Term-Support-kernel!

---

### Post by Utram on 2014-02-04
Same problems here. Did you actually manage to compile the driver yourself?

---

### Post by praseodym on 2014-02-04
Yes, but without hardware. Problems started with kernel 3.8.0-35

---

### Post by Utram on 2014-02-08
[http://pastebin.com/KhX8jZVD](http://pastebin.com/KhX8jZVD)

Here are the error messages from an attempt at compilation under 3.2.0-58-generic

What could be wrong?

---

### Post by praseodym on 2014-02-09
Try this one:

[http://media.cdn.ubuntu-de.org/forum/attachments/28/22/2844083-RTL8191SU_usb_linux_v2.6.6.0.20101111.zip](http://media.cdn.ubuntu-de.org/forum/attachments/28/22/2844083-RTL8191SU_usb_linux_v2.6.6.0.20101111.zip)
Its a bit older...

---

