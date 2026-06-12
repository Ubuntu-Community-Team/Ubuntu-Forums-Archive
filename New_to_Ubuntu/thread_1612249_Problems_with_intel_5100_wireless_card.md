---
title: "Problems with intel 5100 wireless card"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by PandoraJones on 2010-11-02
I have a Gateway NV78 series and I am running Ubuntu 10.04. this is my first time running a straight Linux operating system. My wireless is not functioning. I ran the following command and got this:


$ sudo lshw -C network
[sudo] password for gwen: 
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4600000-d4601fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:26:22:5f:7c:1b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v2.19 ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:d3500000-d350ffff


My question is how do I get the &#$%! thing to work. I have searched the forums and have found no clear solutions.  Help!

---

### Post by silbak04 on 2010-11-03
try downloading this:

[iwlwifi-5000-ucode-8.24.2.12.tgz]("http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz")

then open up a terminal (Application->Accessories->Terminal) and type:

```

$ sudo tar -zxvf filename.tgz

```

---

### Post by PandoraJones on 2010-11-03
And I get this:

Pandora:~$ sudo tar -zxvf filename.tgz
[sudo] password for gwen: 
tar: filename.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
Pandora:~$ 

Thanks for answering and so soon by the way.

-G-

---

### Post by PandoraJones on 2010-11-03
And I get this:

Pandora:~$ sudo tar -zxvf filename.tgz
[sudo] password for gwen: 
tar: filename.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
Pandora:~$ 

Thanks for answering and so soon by the way.

-G-

---

### Post by silbak04 on 2010-11-03
that's because you're supposed to download that file from my previous post and type in:

```

$ sudo tar -zxvf filename.tgz

```

filename.tgz being: [iwlwifi-5000-ucode-8.24.2.12.tgz]("http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz")

you're not supposed to actually type in "filename.tgz" which is what you did, which is why you get that error, because there's no such thing as "filename.tgz"

the filename.tgz is going to be the actual file you download from that link.

hope this helps

---

### Post by PandoraJones on 2010-11-10
And I get this:

pandora@pandora-laptop:~$ sudo tar -zxvf iwlwifi-5000-ucode-8.24.2.12.tgz
tar: iwlwifi-5000-ucode-8.24.2.12.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by PandoraJones on 2010-11-12
Is there something I have to do between downloading the file and untarring it?

---

