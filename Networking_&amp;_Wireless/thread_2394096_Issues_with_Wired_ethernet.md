---
title: "Issues with Wired ethernet"
date: 2018-06-12
forum: Networking &amp; Wireless
---

### Post by plastic1flowers on 2018-06-12
Hi,
I was hoping you could help me. Since I upgraded to 18.04, I'm getting very strange network speeds from my ubuntu server which is acting as a NAS. When I copy a file FROM the NAS onto a linux or windows machine I get the normal transfer rate of around 50-60MB/s. But since the upgrade when I copy a file TO the NAS I'm only getting 10-15MB/s, it used to be around 80MB/s. 

Here is the pastebin of my system [http://paste.ubuntu.com/p/tQq3BYbfGd/](http://paste.ubuntu.com/p/tQq3BYbfGd/)

When the upgrade happened it installed the [COLOR=#000000]8169 network driver which was horrific, the connection was really bad. I managed to get the r8186 installed which improved it but it still isn't what it used to be.

I'm using the onboard wired ethernet card for [/COLOR]GA-G31M-ES2L which is the AR8131 chip (10/100/1000 Mbit) but I can't get a driver to install for that chipset.

[COLOR=#000000]I'm hoping you can help

[/COLOR]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
        Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
        Kernel driver in use: r8168
        Kernel modules: r8168

---

### Post by TheFu on 2018-06-12
I would put in a $25 Intel PRO/1000 NIC and be done. It isn't worth my time to deal with bad NICs.
Also avoid wifi  on any server(s).

NAS connection?  How? Which protocol?  How is the NAS storage mounted?  FUSE?  GIO?  or with a kernel-driver?  1 guess for which is the fastest. ;)   Avoid FUSE and gvfs if you want good performance.  If you are "browsing" to the NAS storage, this probably uses gvfs.  Not the fastest.

NFS is the native way Unix file systems should be used and it is more efficient than other methods.

Also, is IP name resolution setup and working between the NAS and all other systems?  If you use IPs, that should not matter.  

Welcome to the forums.

---

### Post by plastic1flowers on 2018-06-12
Thanks TheFu,
I'm using Samba but I get the same issue with other protocols like FTP, NNTP as well. The issue started with the upgrade to 18.04, it was working fine before that, I think it maybe because the wrong driver is being used like the initial issue with the 8169 driver that got loaded up when the upgrade occurred.
I've looked around for an ath8x driver like [https://wiki.linuxfoundation.org/networking/alx](https://wiki.linuxfoundation.org/networking/alx)
but I've failed miserably to get it to compile on 18.04 with this error
 "ERROR: compat-drivers by default supports kernels >= 2.6.24, try enabling only one driver though". Stop.

---

### Post by Autodave on 2018-06-12
This is probably what you do not want to hear, but I have never had any luck upgrading from one version to the next. I always find it quicker to just wipe what I have and do a clean install.

---

### Post by TheFu on 2018-06-12
Defaults for samba changed in 18.04.  The release notes have info.  Think it was mainly the authentication and protocol levels. They stopped supporting non-secure connections and terribly slow CIFS versions.

FTP? People still use that broken protocol?  Use sftp instead, please,please,please.  Broken protocols shouldn't be used.

NNTP? you run a news server?

If you believe it is just the network layer, use iperf3 to nail it down.  
File servers can have slow disk drivers, slow disk settings (not tuning the file system cache), bad cables forcing re-re-resending of the data and relocation of sectors. All those things can slow down transfers.

---

### Post by plastic1flowers on 2018-06-15
I've installed a new network card and that card is working fine

> **TheFu said:**
> Defaults for samba changed in 18.04.  The release notes have info.  Think it was mainly the authentication and protocol levels. They stopped supporting non-secure connections and terribly slow CIFS versions.

FTP? People still use that broken protocol?  Use sftp instead, please,please,please.  Broken protocols shouldn't be used.


NNTP? you run a news server?

If you believe it is just the network layer, use iperf3 to nail it down.  
File servers can have slow disk drivers, slow disk settings (not tuning the file system cache), bad cables forcing re-re-resending of the data and relocation of sectors. All those things can slow down transfers.

---

### Post by TheFu on 2018-06-15
Please mark the thread as solved if it is.
Also, the exact vendor/model of NIC you added would help others.

---

