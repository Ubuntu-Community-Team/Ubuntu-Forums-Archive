---
title: "[SOLVED] How to Compile MADWIFI driver from source?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by rdawg on 2008-08-28
Hello,

I wanted to install the latest madwifi driver for my TRENDNET TEW-441PC card. It has the atheros chip AR5212. I wanted to know how to compile it from source if I download the driver from the madwifi website. What prerequisites do I need to meet to do this? I checked other forums and they all have different ways to do it. Im just confused now.:confused: Any help will be truly appreciated. Any questions please feel free to ask me.

Thanks,
RDAWG

---

### Post by DemonBob on 2008-08-28
Open up a terminal. 

```

wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo make
sudo make install

```

Reboot.

---

### Post by rdawg on 2008-08-28
Will this be able to be patched with aircrack-ng patch?

---

### Post by DemonBob on 2008-08-28
That i do not know, i don't use aircrack.

---

