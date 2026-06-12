---
title: "Networking on my EeePC"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by Koobelakahn on 2009-09-17
Hello
I am having a bit of an issue concerning Xubuntu, and the lack of network drivers for my netbook

I have a Eeepc Model 1005HA netbook, and for some reason, the networking doesnt work on it. the WLAN isnt showing up, and neither is the regular corded lan. So i used an open wireless adapter (USB) to do a system update, to see if maybe the wireless proprietary driver would be downloaded.

It wasnt.

So here i am, on my new netbook (Eee PC model 1005HA) that is dual booting Xubuntu and Windows XP Home edition SP3, but i cannot get online with Xubuntu

can anyone help me at all?

---

### Post by jrlii on 2009-09-17
I don't know about the Eee, but for my Acer Aspire, I've had to compile the latest drivers from Madwifi to get it to work.

You will need to download and install the "build-essential linux-headers" as well as getting the the driver tar file from Madwifi.

There are detailed instructions for Ubuntu 8.04 at: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

This is making the very large assumption that the Eee uses the Atheros wireless chip.

---

### Post by Koobelakahn on 2009-09-17
How can you tell what wireless chip a computer uses?

---

### Post by mapes12 on 2009-09-18
> **Koobelakahn said:**
> How can you tell what wireless chip a computer uses?If it's built into your machine in Terminal ```
lspci
``` If it's USB ```
lsusb
```

---

### Post by Koobelakahn on 2009-09-22
> **jrlii said:**
> I don't know about the Eee, but for my Acer Aspire, I've had to compile the latest drivers from Madwifi to get it to work.

You will need to download and install the "build-essential linux-headers" as well as getting the the driver tar file from Madwifi.

There are detailed instructions for Ubuntu 8.04 at: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

This is making the very large assumption that the Eee uses the Atheros wireless chip.

You arent gonne believe this, but it DOES use the same chip. Thank you for helping me!

---

