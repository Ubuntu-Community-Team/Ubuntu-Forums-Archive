---
title: "Server release upgrade to 14 killed eth0"
date: 2015-08-09
forum: Networking &amp; Wireless
---

### Post by Someone1 on 2015-08-09
After the upgrade last night (eth0 still working) I noticed this morning that SSH was no longer working... The server no longer has internet so I'm copying those command outputs manually.

uname: 3.13.0-40 SMP x_86_64

ifconfig: lo Local loopback

lspci: Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10) Kernel modules: alx

lshw: *-network UNCLAIMED description: Ethernet controller product: AR8161 Gigabit Ethernet

lsmod only 10 modules - no alx!

modinfo alx not found

Please help me get our home server up again.

Edit: Network works on Live USB boot

---

### Post by TheFu on 2015-08-09
Server?

Please post the **/etc/network/interfaces** file. That is where wired network settings are placed for a server distro.
Also post **sudo lshw -C network**

---

### Post by Someone1 on 2015-08-09
Thanks for the response - got the answer from someone already.
Problem was that somehow linux-image-extra had not been installed during the upgrade. So I had to get that package manually including dependencies, copy them to the machine and install them with dpkg.

---

