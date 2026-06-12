---
title: "Network PCI Adapter doesn't work (WG311v3)"
date: 2018-02-02
forum: Networking &amp; Wireless
---

### Post by msabate on 2018-02-02
Hi,

I'm working on it  for 2 days annd I'm not able to find the solution. I have a PC with Ubuntu 16.04 LTS (32 bits) and I have installed a network card (WG311v3 PCI adapter).

I have done a lot of things (ndiswrapper, firmware...) but it doesn't work. When I type ndiswrapper -l the results are correct but in iwconfig there is any interface of this device.

What can I do to fix it?

---- SOME INFORMATION ----

lspci | grep -i net:
```
03:01.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

iwconfig: (No wlan0 shown)
```
enp3s8    no wireless extensions.

lo        no wireless extensions.

```

ndiswrapper -l:
```
wg311v3 : driver installed
    device (11AB:1FAA) present
```

sudo lshw -C network:
```
*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:dfce0000-dfceffff memory:dfcf0000-dfcfffff

```
-------------------------------------------

Thanks!

---

### Post by jeremy31 on 2018-02-02
See the wireless script link in my signature and post results

---

### Post by msabate on 2018-02-05
Sorry jeremy31, I have not been able to connect until now.

Here are the results: [URL="http://paste.ubuntu.com/26523553/"]http://paste.ubuntu.com/26523553/
[/URL]
Thanks!

---

### Post by praseodym on 2018-02-05
[https://media-cdn.ubuntu-de.org/forum/attachments/19/38/1888522-marvel_8335_X32.tar.gz](https://media-cdn.ubuntu-de.org/forum/attachments/19/38/1888522-marvel_8335_X32.tar.gz)

Try this driver instead with ndiswrapper

---

### Post by msabate on 2018-02-06
Hi praseodym, I installed this driver too and it didn't work. I have tried to install the other driver called mod8335.inf, just for casuality, but it hasn't worked.

What can I do? How can I solve it?

---

### Post by praseodym on 2018-02-06
Please check
```

sudo modprobe -v ndiswrapper
dmesg | grep ndis
```

---

### Post by msabate on 2018-02-07
sudo modprobe -v ndiswrapper:
```
insmod /lib/modules/4.13.0-32-generic/updates/dkms/ndiswrapper.ko
```

dmesg | grep ndis:
```
[  179.446101] ndiswrapper: loading out-of-tree module taints kernel.
[  179.446369] ndiswrapper: module verification failed: signature and/or required key missing - tainting kernel
[  179.446387] ndiswrapper: module license taints kernel.
[  179.447562] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[  179.672575] usbcore: registered new interface driver ndiswrapper
```

---

### Post by captionopen2 on 2018-03-23
I'm having a similar issue (Lubuntu 16.04 w/ WG311v3 driver) - [https://ubuntuforums.org/showthread.php?t=2387252](https://ubuntuforums.org/showthread.php?t=2387252)
My wireless network shows up, but when I connect, it keeps asking for pw even when I correctly enter it.

I got my driver from here - [http://www.driverguide.com/driver/detail.php?driverid=757524&action=filfo](http://www.driverguide.com/driver/detail.php?driverid=757524&action=filfo)
and I'm using the xp driver.

Did you ever find out what the problem was or get it worked out?

---

