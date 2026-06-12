---
title: "[Solved] ethernet stopped working. Wi-fi is ok"
date: 2021-01-07
forum: Networking &amp; Wireless
---

### Post by linerman on 2021-01-07
Hi,

After today system security update, my ethernet stopped working. I cannot connect.
Apart from that I have also wi-fi card, and that one works with no problem.

I do not know from where I should start looking for solution...(Ubuntu 20.04)

```
lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: d8:cb:8a:7c:6f:51
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-34-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:17 ioport:d000(size=256) memory:f7200000-f7200fff memory:e2800000-e2803fff
  *-network
       description: Wireless interface
       product: Broadcom Inc. and subsidiaries
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlp6s0
       version: 04
       serial: 34:97:f6:b6:c7:e4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=10.28.2 firmware=01-d2cbb8fd ip=192.168.88.252 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:35 memory:f7000000-f7007fff memory:f6800000-f6ffffff memory:e2400000-e27fffff

```

---

### Post by TheFu on 2021-01-07
Troubleshooting Networking: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by linerman on 2021-01-07
Thanks for the answer.
I did nothing on my computer except for updating. And I guess here is a problem.
Correct me, if I am wrong but I think there is a bug in a new kernel 5.8.0-34.
As far as I know, driver for my ethernet card is built in kernel.
So ufter upgrading the kernel, driver was updated also and that generate the error:

```

r8169 0000:03:00.0 enp3s0: rtl_rxtx_empty_cond == 0 (loop: 42, delay: 100).

```

I tried to remove the driver and install it again
```

sudo dkms remove r8168/8.048.00 -k "$(uname -r)/$(uname -p)"
sudo apt-get purge r8168-dkms
sudo modprobe -r r8168
sudo update-initramfs -u -k "$(uname -r)"

```

but it did not work either.

I've found solution anyway. I do not know, whether it is the simplest or correct one, but I did:



[LIST=1]
[*]sudo apt-get install build-essential linux-headers-$(uname -r) 
[*]sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf' 
[*]Download latest tar.gz from [https://github.com/mtorromeo/r8168/releases](https://github.com/mtorromeo/r8168/releases) 
[*]tar xfvz r8168-X.XXX.XX.tar.gz (replace XXs with name of file you downloaded) 
[*]cd r8168-8.XXX.XX 
[*]sudo ./autorun.sh 
[/LIST]


And after that, my ethernet is working like charm.
Anyway, I am not sure, if blacklisting r8169 is a good move...

---

### Post by TheFu on 2021-01-07
Do you personally know mtorromeo and trust him?
Pulling code that runs at the kernel level from unknown internet sources seems scary.
Perhaps mtorromeo is great, trustworthy, well-known?  IDK.

[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software) s the link on that github site. Perhaps a better source?  The choice is yours.

---

### Post by linerman on 2021-01-07
Realtek download site is kinda broken. Tuxbyte [https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://tuxbyte.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/) and others suggest to use mtorromeo mirror

---

### Post by alfredo-centinaro on 2021-08-26
> **linerman said:**
> Thanks for the answer.
I did nothing on my computer except for updating. And I guess here is a problem.
Correct me, if I am wrong but I think there is a bug in a new kernel 5.8.0-34.
As far as I know, driver for my ethernet card is built in kernel.
So ufter upgrading the kernel, driver was updated also and that generate the error:

```

r8169 0000:03:00.0 enp3s0: rtl_rxtx_empty_cond == 0 (loop: 42, delay: 100).

```

I tried to remove the driver and install it again
```

sudo dkms remove r8168/8.048.00 -k "$(uname -r)/$(uname -p)"
sudo apt-get purge r8168-dkms
sudo modprobe -r r8168
sudo update-initramfs -u -k "$(uname -r)"

```

but it did not work either.

I've found solution anyway. I do not know, whether it is the simplest or correct one, but I did:



[LIST=1]
[*]sudo apt-get install build-essential linux-headers-$(uname -r) 
[*]sudo sh -c 'echo blacklist r8169 >> /etc/modprobe.d/blacklist.conf' 
[*]Download latest tar.gz from [https://github.com/mtorromeo/r8168/releases](https://github.com/mtorromeo/r8168/releases) 
[*]tar xfvz r8168-X.XXX.XX.tar.gz (replace XXs with name of file you downloaded) 
[*]cd r8168-8.XXX.XX 
[*]sudo ./autorun.sh 
[/LIST]


And after that, my ethernet is working like charm.
Anyway, I am not sure, if blacklisting r8169 is a good move...

Confirm it works with fresh Ubuntu Studio 21.04 in august 2021 with 5.11.0 kernel

---

### Post by linerman on 2021-08-27
> **alfredo-centinaro said:**
> Confirm it works with fresh Ubuntu Studio 21.04 in august 2021 with 5.11.0 kernel

Great!
Have in mind, that if you blacklisted r8169 driver, then after kernel update you will not have an internet connection.
So you need to have an installation files [https://github.com/mtorromeo/r8168/releases](https://github.com/mtorromeo/r8168/releases) on your disk and after kernel upgrade, you will need to run the process with installation r8168 driver again.

---

### Post by quarksrus on 2021-09-13
Hi,

I'm a bit confused reading this thread! So going back to r8168 works in Ubuntu 21.04 (kernel 5.11) or no? It's not very clear from reading this thread.

---

### Post by linerman on 2021-09-15
> **quarksrus said:**
> Hi,

I'm a bit confused reading this thread! So going back to r8168 works in Ubuntu 21.04 (kernel 5.11) or no? It's not very clear from reading this thread.

r8169 driver works both in Ubuntu 20.04 and 21.04, but unfortunately it is not stable in a long term using (means: sudden disconnecting, sometimes low transfer bandwidth, dns problems).

r8168 driver which is available to download (step by step guide is in my post) is free from above errors (driver also works in Ubuntu 20.04 and 21.04)

Above of all , the important inconvenience is that sometimes NIC Realtek is not switching off during reboots. It affects all linux systems if you have Windows as a parallel installation. 
In such situation : user reboots windows 10 and log into linux, the Ethernet card is switched off and cannot be switched on.
So the user needs to log in again to Windows 10 and shutdown properly the system.
The next step is to wait 2 sec with machine been powered off, and then run linux. The Ethernet card would be visible and connection would be established.
That error may be fixed in Windows 10 configuration, but it is not always working.

If you have r8169 driver in your Ubuntu, than rebooting of Windows and lack of internet in Ubuntu would affects you sooner or later (7 times per 10 reboots - tested by me).
But if you have r8168 driver, that problem is existing only few times per 100 of reboots.

Summarizing. Realtek NIC card is not a good choice, but if you do not have any other options, then as you can see, the r8168 driver for that NIC is much better solution.
The only thing you need to remember is that blacklisting r8169 driver would leave you without internet after kernel update (it is due to the fact, that installation r8168 driver using my way equals installing the driver into kernel and blacklisting the faulty one). So the best way is to keep the installation file on the disk, and after kernel update, run the process of installation once again.

---

