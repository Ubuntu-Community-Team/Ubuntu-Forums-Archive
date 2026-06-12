---
title: "can't make wired connection from USB stick"
date: 2019-12-06
forum: Networking &amp; Wireless
---

### Post by whimbrel on 2019-12-06
I'm trying to install ubuntu 18.04  on an intel NUC8i3BEH.
While running ubuntu from the USB stick  it's unable to  make 
a wired connection. 
I tried  changing the line in  /etc/NetworkManager/NetworkManager.conf
managed=false  to  managed=true (as suggested in some posts) but it didn't 
work. My /etc/netplan/01-network-manager-all.yaml already contains the
line: renderer: NetworkManager (also as suggested to add).

I've attached  some screen shots of NetworkManager.conf,  xxxx.yaml and
am re-posting the output of lshw -C network and  lspci  as text (I'm posting
from another computer and didn't think of saving them as text files at first).

```

root@ubuntu:~# lshw  -C  network
  *-network:0               
       description: Wireless interface
       product: Cannon Point-LP CNVi [Wireless-AC]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlp0s20f3
       version: 30
       serial: 04:ea:56:49:d2:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-18-generic firmware=46.6bf1df06.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: iomemory:400-3ff irq:16 memory:404ac10000-404ac13fff
  *-network:1
       description: Ethernet interface
       product: Ethernet Connection (6) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 30
       serial: 1c:69:7a:08:4d:2f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.4-4 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:128 memory:c0a00000-c0a1ffff   
```

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 3ecc (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Iris Plus Graphics 655 (rev 01)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Point-LP Thermal Controller (rev 30)
00:14.0 USB controller: Intel Corporation Cannon Point-LP USB 3.1 xHCI Controller (rev 30)
00:14.2 RAM memory: Intel Corporation Cannon Point-LP Shared SRAM (rev 30)
00:14.3 Network controller: Intel Corporation Cannon Point-LP CNVi [Wireless-AC] (rev 30)
00:16.0 Communication controller: Intel Corporation Cannon Point-LP MEI Controller #1 (rev 30)
00:17.0 SATA controller: Intel Corporation Cannon Point-LP SATA Controller [AHCI Mode] (rev 30)
00:1c.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #1 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #5 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #9 (rev f0)
00:1d.6 PCI bridge: Intel Corporation Cannon Point-LP PCI Express Root Port #15 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Cannon Point-LP LPC Controller (rev 30)
00:1f.3 Audio device: Intel Corporation Cannon Point-LP High Definition Audio Controller (rev 30)
00:1f.4 SMBus: Intel Corporation Cannon Point-LP SMBus Controller (rev 30)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Point-LP SPI Controller (rev 30)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (6) I219-V (rev 30)
6e:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
ubuntu@ubuntu:~$   
```

Thanks for any help.

---

### Post by mörgæs on 2019-12-07
It's best to paste the text from terminal output in CODE tags rather than as an image which can't be found by the search function.

How does 19.10 work?

---

### Post by whimbrel on 2019-12-07
That computer can't connect to the internet so I had to make screen shots and 
post from another computer.  (I was trying to install ubuntu 18.04 on that computer.)

---

### Post by mörgæs on 2019-12-07
It would be interesting to see how 19.10 performs in comparison.

---

### Post by hk42 on 2019-12-08
I found that having a spare USB to 100Mb Ethernet dongle is handy for this kind of situation.
They are supported by quite old OS installation disks.

---

### Post by whimbrel on 2019-12-09
Thanks, I think this is some sort of driver problem.

---

### Post by him610 on 2019-12-09
FWIW, the bottom half of your 3rd thumbnail from the left looks similar to mine,
```

  *-network
       description: Ethernet interface
       product: Ethernet Connection (2) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 00
       serial: 70:85:c2:3b:46:73
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.2-4 ip=10.0.0.21 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:122 memory:df300000-df31ffff

```
Same device= I-219-V, same driver= e1000e, driverversion=3.2.6-k
Maybe you have a faulty cable.

---

### Post by whimbrel on 2019-12-09
Thanks, but the same ethernet cable works fine on my older computer.  

Under ubuntu 18.04 ubuntu didn't detect the ssd, under 19.10 it did,  but it
still couldn't connect. Maybe it needs some type of newer driver?

---

### Post by tea for one on 2019-12-10
I have the same device and wired ethernet connection has always worked automagically, not only with Ubuntu (live and installed) but also other live distros such as MX Linux, Peppermint and Xubuntu.

There are a few more things to check:-

Open up Intel Visual Bios (F2 during the boot process) > Advanced > Onboard Devices.

LAN and WLAN - are the boxes ticked?

The device also has wireless - does that work?

Did you check the 18.04 image file (md5sum or similar) before trying it?

Lastly, you may consider asking the mods to move the thread to Networking & Wireless because there are some very knowledgeable and helpful people there.

---

### Post by whimbrel on 2019-12-10
Thanks,  yes  the  LAN and WLAN   boxes are  checked  and a list of wireless 
networks do show up in Settings (I don't have the password for any of them).  
I don't think anything was wrong with the 18.04 image file, I used it 
to install on the computer I'm using now which connects and works fine.
I tried  ubuntu 19.10 from the USB and it has the same problem (wired  connection failed).

If 18.04  works  on your NUC maybe it has something to do with the modem.
(I asked them if they'd  move the post to  Networking & Wireless.)

---

### Post by tea for one on 2019-12-10
> **whimbrel said:**
> Thanks,  yes  the  LAN and WLAN   boxes are  checked  and a list of wireless 
networks do show up in Settings (I don't have the password for any of them).  
I don't think anything was wrong with the 18.04 image file, I used it 
to install on the computer I'm using now which connects and works fine.
I tried  ubuntu 19.10 from the USB and it has the same problem (wired  connection failed).

If 18.04  works  on your NUC maybe it has something to do with the modem.
(I asked them if they'd  move the post to  Networking & Wireless.)

It is unfortunate that you are unable to use the wireless network because there is a small possibility that installing the Hardware Enablement Stack may help.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

```
sudo apt-get install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04 
```

However, when I purchased my NUC8i3BEH in January 2019, all the services were recognised by Ubuntu 18.04 (although I installed the HWE a few months later, just for fun)

I don't suspect that Ubuntu network software is the roadblock and I hope that somebody in Networking & Wireless can offer some help.

Also, in one of your earlier posts, you mentioned that Ubuntu 18.04 did not detect your SSD.

That is also a bit unusual and it may be that the internal connections in your NUC are compromised.

Finally, perhaps try a live session with another Linux distro?

Good luck

---

### Post by slickymaster on 2019-12-11
*Thread moved to **Networking & Wireless**.*

---

### Post by odee2 on 2019-12-12
Try to force it down to 100M from 1G on both sides

---

### Post by whimbrel on 2019-12-12
This problem had nothing to do with Ubuntu. The modem I 
have (Arris model: TM3402A) seems to register whatever 
device is connected to it when it is rebooted, and then 
won't let anything else connect. The solution was just
to reboot the modem with the NUC plugged in.

---

