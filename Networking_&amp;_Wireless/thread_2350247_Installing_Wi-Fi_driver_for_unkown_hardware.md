---
title: "Installing Wi-Fi driver for unkown hardware"
date: 2017-01-22
forum: Networking &amp; Wireless
---

### Post by chuck202 on 2017-01-22
I've just purchased a new laptop and I don't know the specifics of my wi-fi hardware. I've run throgh the steps at [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-hardware-check.html) which provided the following:

sudo lshw -C network
```
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:df100000-df101fff

```

lspci
```
03:00.0 Network controller: Intel Corporation Device 24fd (rev 78)

```

After some searching, I've found that certain adapters aren't natively supported by linux, but can work with workarounds specific to the adaptor. Since my first command plainly describes my adaptor as 'product: Intel Corporation', I'm not sure how to progress. :confused:

Any assistance would be greatly appreciated.

---

### Post by howefield on 2017-01-22
Moved to the "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2017-01-22
If you are using Ubuntu 16.04 with a working ethernet connection do
```
sudo apt-get install linux-generic-hwe-16.04-edge
```
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161.1_all.deb
```
```
sudo dpkg -i linux-firmware_1.161.1_all.deb
```

Reboot and this will install the newer kernel and firmware needed

---

### Post by chuck202 on 2017-01-22
Worked like a charm.

Thank you very much, your help is appreciated. :)

---

