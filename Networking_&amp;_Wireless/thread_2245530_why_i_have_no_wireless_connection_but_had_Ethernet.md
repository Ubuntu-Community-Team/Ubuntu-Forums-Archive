---
title: "why i have no wireless connection but had Ethernet on my lubuntu 14.04"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by rovski on 2014-09-24
[IMG]http://www.imagesup.net/?di=914115648637[/IMG]

Someone held pls. I using old laptop though.

---

### Post by praseodym on 2014-09-24
Please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
rfkill list
iwconfig
```

---

### Post by rovski on 2014-09-24
> **praseodym said:**
> Please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
rfkill list
iwconfig
```

[http://www.datafilehost.com/d/04788de7](http://www.datafilehost.com/d/04788de7)

---

### Post by praseodym on 2014-09-24
Your InProComm device only works with the Windows driver. Please run:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```
Download the driver from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz)

Unpack it and install the 32bit *.INF file with the Windows wireless tool.

---

### Post by rovski on 2014-09-25
> **praseodym said:**
> Your InProComm device only works with the Windows driver. Please run:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```
Download the driver from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/43/03/1774535-ipn2220_32_64_all_mod.tar.gz)

Unpack it and install the 32bit *.INF file with the Windows wireless tool.

I need to download 88.7 mb of achives. And my Ethernet network speed is really show. 128kbps only. I think i need to solves my internet speed first before i doing it. Wait for me . I need your help. Thanks.

---

### Post by rovski on 2014-09-25
But can i use this procedure?
 Without an Internet connection, you can still
install ndiswrapper-utils from the Desktop CD.
If you installed from that, the repository in
which ndiswrapper-utils is found is on the CD,
but not within the live session. You need to
boot into your new Ubuntu installation and
then reinsert the Desktop CD. You will be asked
if you want to add the packages on the CD to
your list of repositories. Put the CD into the
drive, click System > Administration >
Synaptic Package Manager and search for
ndis. I

---

### Post by rovski on 2014-09-25
Its working now. Thanks.

---

### Post by praseodym on 2014-09-25
Glad its working. What about the spped? Is it an ISP problem?

---

