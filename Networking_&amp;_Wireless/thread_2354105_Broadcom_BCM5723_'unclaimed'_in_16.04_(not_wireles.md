---
title: "Broadcom BCM5723 'unclaimed' in 16.04 (not wireless, not in sticky post)"
date: 2017-02-28
forum: Networking &amp; Wireless
---

### Post by iwaharu on 2017-02-28
I upgraded yesterday from Ubuntu 14.04 to 16.04, everything seems to have gone smoothly, except that I my network doesn't seem to work, my ethernet card is now unclaimed.

When i run a lshw i get the following:

[http://i66.tinypic.com/21bprx2.jpg](http://i66.tinypic.com/21bprx2.jpg)

I also had a look at the sticky post, about broadcom, but mine is not in the list: 14e4:165b (rev 10)

My suspicion is that I have to install a driver somehow, but I'm not sure how. Any help is appreciated.

---

### Post by wildmanne39 on 2017-02-28
Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
by clicking on new reply and click # then paste the information between the brackets.
Thank you
```

---

### Post by wildmanne39 on 2017-02-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by iwaharu on 2017-02-28
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
Linux server 4.4.0-64-generic #85-Ubuntu SMP Mon Feb 20 11:50:30 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)
    Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter [103c:705d]

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    24576  0
usb_storage            69632  2 uas
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 24576  2 nf_nat_ipv4,nf_nat_masquerade_ipv4
nf_conntrack_ipv4      16384  2
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          106496  5 nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_ipv4
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                126976  0
stp                    16384  1 bridge
llc                    16384  2 stp,bridge
ebtable_filter         16384  0
ebtables               36864  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
ip_tables              24576  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               36864  11 ip6table_filter,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_conntrack,iptable_filter,ebtables,ipt_REJECT,iptable_mangle,ip6_tables
zfs                  2813952  0
zunicode              331776  1 zfs
zcommon                57344  1 zfs
znvpair                90112  2 zfs,zcommon
spl                   102400  3 zfs,zcommon,znvpair
zavl                   16384  1 zfs
binfmt_misc            20480  1
joydev                 20480  0
input_leds             16384  0
kvm_amd                65536  0
kvm                   544768  1 kvm_amd
irqbypass              16384  1 kvm
lp                     20480  0
parport                49152  1 lp
autofs4                40960  2
btrfs                 987136  1
xor                    24576  1 btrfs
raid6_pq              102400  1 btrfs
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
ahci                   36864  5
libahci                32768  1 ahci


```

I can't run 
rfkill list all

because rfkill is not available.

---

### Post by wildmanne39 on 2017-02-28
Please do:
```
sudo modprobe -v tg3
```
does wired connection come on?

---

### Post by iwaharu on 2017-02-28
```
modprobe: FATAL: Module tg3 not found in directory /lib/modules/4.4.0-64-generic
```

---

### Post by iwaharu on 2017-02-28
I created a bootable usb with Ubuntu Desktop and there my ethernet works. I copied the files from /lib/modules/4.8.0-46-generic/kernel/drivers/net/ethernet/broadcom from the ubuntu live, to /lib/modules/4.4.0-64-generic/kernel/drivers/net/ethernet/broadcom, in the hopes of getting it to work. However when i run ```
sudo modprobe -v tg3
``` I still the same error as above. Do I need to register them? Can it work anyway because there is a version mismatch?

---

### Post by cariboo on 2017-02-28
Make sure the driver is installed, it should be located in:

```
/lib/modules/4.4.0-64-generic/kernel/drivers/net/ethernet/broadcom
```

You may want to have a look at [this page]("https://www.cyberciti.biz/faq/linux-broadcom-ethernet-card-driver-installation/")

---

### Post by iwaharu on 2017-03-01
The steps explained in [this page]("https://www.cyberciti.biz/faq/linux-broadcom-ethernet-card-driver-installation/") don't seem to be different from what wildmanne39 suggested. The modprobe does not recognize or notice the files I copied from the Ubuntu Live into my 4.4.0-64 kernel. 

I installed a fresh Ubuntu server in a virtual machine and noticed it had a 4.4.0-62 kernel as default, in which broadcom drivers are supplied. Following steps in [this page]("http://www.wikihow.com/Update-Ubuntu-Kernel") I installed 4.4.0-64 kernel and there are no broadcom drivers available anymore.

Could it be that broadcom drivers are missing in the 4.4.0-64 kernel? And how would I add those?

---

### Post by iwaharu on 2017-03-01
I've given up and reinstalled Ubuntu on my machine. Still I would like to thank you guys for trying to help me out!

---

