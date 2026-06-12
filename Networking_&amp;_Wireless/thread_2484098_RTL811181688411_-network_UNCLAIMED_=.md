---
title: "RTL8111/8168/8411 *-network UNCLAIMED ="
date: 2023-02-17
forum: Networking &amp; Wireless
---

### Post by mustafejen on 2023-02-17
Hello!

I lost my network connection after updating Ubuntu the other day.

The network adapter used to work just fine with Ubuntu Jammy, and works on FreeBSD right now.

I think I have kernel 5.19.0-32-generic.

I don't recall which linux command scanned this network card
but I got the output below:

```
  *-network UNCLAIMED
       beskrivning: Ethernet controller
       produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       tillverkare: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 0c
       bredd: 64 bits
       klocka: 33MHz
       förmågor: pm msi pciexpress msix vpd bus_master cap_list
       konfiguration: latency=0
       resurser: ioport:e000(storlek=256) memory:fe300000-fe300fff memory:f2000000-f2003fff
```

[https://pastebin.com/iR74bZbL](https://pastebin.com/iR74bZbL) is a link to the old dmesg where things work.

Now after some editing of this post, here is a link to my new dmesg where I have no network: [https://pastebin.com/8WSUy50F](https://pastebin.com/8WSUy50F)

If you want more information, give me instructions and I think I will be back tomorrow.

---

### Post by slickymaster on 2023-02-17
Thread moved to **Networking & Wireless** for a better fit

---

### Post by #&amp;thj^% on 2023-02-17
```
inxi -Nz
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    **[COLOR="#FF0000"]driver: r8169[/COLOR]**
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi


```
Here where i'd start 
```
apt search iwlwifi
Sorting... Done
Full Text Search... Done
linux-firmware-iwlwifi/kaisen-rolling,now 20221109-1kaisen all [installed,automatic]
  Binary firmware for Intel Wireless Wifi


```
But you won't find this version as it should be.
```
/kaisen-rolling
```
It will have a Ubuntu naming to it.

---

### Post by jeremy31 on 2023-02-17
Any result from terminal for ```
dpkg -l | grep linux-modules-extra-$(uname -r)
```
If no result you will need to boot into an older kernel using Grub/Advanced Option for Ubuntu to reinstall the missing package

---

### Post by mustafejen on 2023-02-17
dpkg -l | grep linux-modules-extra-$(uname -r) returned no output.
Thanks for telling me how to find the older kernels in Grub.
I am typing this from Ubuntu with network on an old kernel.

Which missing package should I install?
I have found r8168-dkms but I am not sure it is the right one.

---

### Post by #&amp;thj^% on 2023-02-17
```
sudo lsmod | grep r8169
r8169                 118784  0

```

---

### Post by jeremy31 on 2023-02-17
Ok, post results for ```
dpkg -l | linux-image
```

---

### Post by mustafejen on 2023-02-17
sudo dpkg -l | linux-image
linux-image: kommandot hittades inte

sudo dpkg -l | grep linux-image
rc  linux-image-5.13.0-19-generic              5.13.0-19.19                            amd64        Signed kernel image generic
ii  linux-image-5.15.0-56-generic              5.15.0-56.62                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-57-generic              5.15.0-57.63                            amd64        Signed kernel image generic
rc  linux-image-5.15.0-58-generic              5.15.0-58.64                            amd64        Signed kernel image generic
ii  linux-image-5.15.0-60-generic              5.15.0-60.66                            amd64        Signed kernel image generic
ii  linux-image-5.19.0-32-generic              5.19.0-32.33~22.04.1                    amd64        Signed kernel image generic
ii  linux-image-generic

---

### Post by jeremy31 on 2023-02-17
Do this and reboot ```
sudo apt install --reinstall linux-modules-extra-5.19.0-32-generic
```

---

### Post by mustafejen on 2023-02-17
I did

sudo apt install --reinstall linux-modules-extra-5.19.0-32-generic

While installing the extra modules, apt suggested that I installed

linux-headers-5.19.0-32-generic

too.

I did so before rebooting, and in the process another package was installed.

Now I have rebooted.

per@konjak:~$ uname -a
Linux konjak 5.19.0-32-generic #33~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Jan 30 17:03:34 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

The network works :-)

Thanks for the help!

---

