---
title: "10Ge SFP+ DAC link issues mlx4_en: enp5s0: Link Down - Link Up"
date: 2019-10-19
forum: Networking &amp; Wireless
---

### Post by yer on 2019-10-19
Hello everyone. I have a strange networking issue. I've got a 'QNAP QSW-308-1C'  10Gbe sfp+ switch, a Mellanox MT26448 card, and a belkin 'F2CX036-10M' DAC cable.


I'm running Ubuntu 18.04.3 LTS, kernel 4.15.0-65-generic. The card is detected, the 'mlx4_en' module is loaded, and `ip link show` gives me the 'enp5s0' device. However `lshw -C network` shows 'link=no'. The indicator lights on the SPF+ port on the switch blink on and off. Link status light on the card came on briefly once. There is a repeating message in `dmsg`.

```

[21789.056195] mlx4_en: Mellanox ConnectX HCA Ethernet driver v4.0-0
[21789.056427] mlx4_en 0000:05:00.0: Activating port:1
[21789.056504] mlx4_en: 0000:05:00.0: Port 1: enabling only PFC DCB ops
[21789.058980] mlx4_en: 0000:05:00.0: Port 1: Using 8 TX rings
[21789.058981] mlx4_en: 0000:05:00.0: Port 1: Using 8 RX rings
[21789.059180] mlx4_en: 0000:05:00.0: Port 1: Initializing port
[21789.063402] mlx4_core 0000:05:00.0 enp5s0: renamed from eth1
[21789.110495] <mlx4_ib> mlx4_ib_add: mlx4_ib: Mellanox ConnectX InfiniBand driver v4.0-0
[21789.110864] <mlx4_ib> mlx4_ib_add: counter index 1 for port 1 allocated 1
[21802.388306] mlx4_en: enp5s0: Link Up
[21802.438230] mlx4_en: enp5s0: Link Down
[21821.670500] mlx4_en: enp5s0: Link Up
[21821.725437] mlx4_en: enp5s0: Link Down
[21943.956062] mlx4_en: enp5s0: Link Up
[21944.005986] mlx4_en: enp5s0: Link Down
[22058.549736] mlx4_en: enp5s0: Link Up
[22058.599698] mlx4_en: enp5s0: Link Down
[22089.342298] mlx4_en: enp5s0: Link Up
[22089.397239] mlx4_en: enp5s0: Link Down

```
Link Up / Link Down repeats forever unless I modprobe -r the driver. I'm fairly sure that the link led on the switch blinks in time to the dmesg notification.
Anyone have a clue where I should start troubleshooting?

More info below.  
```

root@redacted:~# lspci |grep Mel;ip link show enp5s0;lsmod |grep mlx;echo -ne "dmseg link errors : ";dmesg |egrep "Up|Down"|wc -l
05:00.0 Ethernet controller: Mellanox Technologies MT26448 [ConnectX EN 10GigE, PCIe 2.0 5GT/s] (rev b0)
7: enp5s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:02:c9:51:a7:8e brd ff:ff:ff:ff:ff:ff
mlx4_ib               180224  0
ib_core               225280  1 mlx4_ib
mlx4_en               114688  0
mlx4_core             294912  2 mlx4_ib,mlx4_en
devlink                45056  3 mlx4_core,mlx4_ib,mlx4_en
ptp                    20480  1 mlx4_en
dmseg link errors : 698


```


:biggrin:And before anyone asks, yes, both ends of the cable are plugged in. :biggrin:

---

### Post by yer on 2019-10-23
It was the cable. 10m DAC was to long for the Mellanox card, it likes a 7m DAC a lot better. Getting 8.8Gbps throughput.

---

