---
title: "New dual-boot install of Ubuntu 18.04.3 with Win10 - wireless disabled"
date: 2019-08-29
forum: Networking &amp; Wireless
---

### Post by randomham on 2019-08-29
Hello,
I recently made my Dell Latitude E5470 dual-bootable with Win10/Ubuntu 18.04.3. In Windows, wireless works fine. In Ubuntu, the PCI card isn't recognized.

I ran the following script:
sudo lshw -C network

And received the below response.
  *-network DISABLED        
       description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 3a
       serial: 44:85:00:2b:84:3c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.0.0-25-generic firmware=36.e91976c0.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:e1100000-e1101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection I219-LM
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 84:7b:eb:21:52:4d
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-3 ip=192.168.0.41 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:127 memory:e1200000-e121ffff
Please help.

Thanks in advance,
Dave

---

### Post by jeremy31 on 2019-08-29
Please see the wireless script link in my signature and post results

---

### Post by randomham on 2019-08-31
I've posted the output from your wireless script, Jeremy31, to pastebin. It's a public file titled: Intel_8260_driver with a post date of 31 August.

Thanks!
Dave

---

### Post by chili555 on 2019-08-31
> **randomham said:**
> I've posted the output from your wireless script, Jeremy31, to pastebin. It's a public file titled: Intel_8260_driver with a post date of 31 August.

Thanks!
DavePlease give us the link. We and Google can't find it with the information provided.

---

### Post by randomham on 2019-08-31
My apologies!

Here it is:
[https://pastebin.com/FnpcsXQD](https://pastebin.com/FnpcsXQD)

Thank you!

---

### Post by chili555 on 2019-09-01
Please note: ```

1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```This suggests that the wireless key combination is set to disable the wireless radio.  According to the manual, the key combination is Fn+PrtScr. Reference: [https://topics-cdn.dell.com/pdf/latitude-e5470-laptop_owners-manual_en-us.pdf](https://topics-cdn.dell.com/pdf/latitude-e5470-laptop_owners-manual_en-us.pdf) Does the key combination now enable the wireless? 

If there is no change, does this help?```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
rfkill list all
```

---

### Post by randomham on 2019-09-01
The key stroke combination turned the wireless on. Thank you!

---

