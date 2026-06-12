---
title: "Killer 1525 (QCA6174) Preventing Ubuntu 18.04 from sleeping/suspend."
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by bpkenn on 2018-10-24
I'm unable to get Ubuntu to sleep/suspend (by clicking suspend in the menu) when i have my wireless enabled.  When I disable wireless i am able to sleep/suspend just fine.  My laptop is an MSI GS60 ghost pro.  If anyone could help I would appreciate it.  I've just converted from windows, and I'm using this as a primary work device.

>         Output of command lshw

*-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:dd200000-dd3fffff
           *-network DISABLED
                description: Wireless interface
                product: QCA6174 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 20
                serial: ac:d1:b8:8c:ab:a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-36-generic firmware=SW_RM.1.1.1-00157-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:136 memory:dd200000-dd3fffff


---

### Post by think.more on 2018-12-01
I have exact same problem with MSI GS60 2QE on 18.10 and 18.04, I searched for solution, but it appears, only solution for now is to disable wireless before going to sleep :( I already have asked this question earlier, but no solution was found... link: [https://ubuntuforums.org/showthread.php?t=2403466](https://ubuntuforums.org/showthread.php?t=2403466)

---

### Post by christian-va on 2019-10-10
Hi again,

after tearing my hair for 2 days, I was able to solve the problem with an older firmware qca6174 version.

I was not able to unload the ath10k_pci module before suspend automatically, not via a systemd Unit nor with a script in /lib/systemd/system/system-sleep.
Installing the newest qca6174 formware also did not help.

What helped was an older firmware version from 2016!
Now I have qca6174 hw2.1 version 141 installed, although my notebook runs on 18.04.3 with Kernel 5.

I got that tip from here: [https://askubuntu.com/a/978385/1004167](https://askubuntu.com/a/978385/1004167) so I got the firmware from there: [https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157](https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157) and copied the ath10k_pci/QCA6174/hw2.1 files (which my card is using) into my /lib/firmware/ath10k/QCA6174/hw2.1 folder.

After a reboot, I did not have to unload the driver before suspend (removed my scripts). Going to sleep and resume works for me now, as it did before upgrading from 16.04.

---

### Post by vassagou7 on 2020-06-05
> **christian-va said:**
> Hi again,

after tearing my hair for 2 days, I was able to solve the problem with an older firmware qca6174 version.

I was not able to unload the ath10k_pci module before suspend automatically, not via a systemd Unit nor with a script in /lib/systemd/system/system-sleep.
Installing the newest qca6174 formware also did not help.

What helped was an older firmware version from 2016!
Now I have qca6174 hw2.1 version 141 installed, although my notebook runs on 18.04.3 with Kernel 5.

I got that tip from here: [https://askubuntu.com/a/978385/1004167](https://askubuntu.com/a/978385/1004167) so I got the firmware from there: [https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157](https://launchpad.net/ubuntu/xenial/amd64/linux-firmware/1.157) and copied the ath10k_pci/QCA6174/hw2.1 files (which my card is using) into my /lib/firmware/ath10k/QCA6174/hw2.1 folder.

After a reboot, I did not have to unload the driver before suspend (removed my scripts). Going to sleep and resume works for me now, as it did before upgrading from 16.04.


I confirm your solution works in Ubuntu 20.04 too.  Mine is MSI GS60 2QE.    For me was more than 2 days tearing my hair until I found your solution.  Thanks

---

### Post by coffeecat on 2020-06-05
Back to sleep, ancient thread.

---

