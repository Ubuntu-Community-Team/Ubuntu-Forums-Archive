---
title: "qlogic cLOM8214 1/10GbE card has no optical info from ethtool"
date: 2023-04-09
forum: Networking &amp; Wireless
---

### Post by kallquk on 2023-04-09
Hello to all


I have this card qlogic cLOM8214 1/10GbE installed with ubuntu server 22.04, and working.

My problem is that I need ddm-info, because transceiver support it, using ethtool -m( this is the option for this purpose) I get:

```
:~$ sudo ethtool -m eth1
netlink error: Operation not supported
```

I need this info for everyday monitoring of this 10 km link, where another side is not managed by me, so it is important

analyzing more info below, I think it is using latest driver and firmware with kernel 5.19.38


```
:~$ lspci
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
01:00.0 Ethernet controller: QLogic Corp. cLOM8214 1/10GbE Controller (rev 54)
01:00.1 Ethernet controller: QLogic Corp. cLOM8214 1/10GbE Controller (rev 54)

```

```
:~$ sudo dmesg | grep qlcnic
[    3.080500] qlcnic 0000:01:00.0: 2048KB memory map
[    3.679129] qlcnic 0000:01:00.0: Default minidump capture mask 0x1f
[    3.685475] qlcnic 0000:01:00.0: FW dump enabled
[    3.690163] qlcnic 0000:01:00.0: Supports FW dump capability
[    3.695902] qlcnic 0000:01:00.0: Driver v5.3.66, firmware v4.20.1
[    3.740280] qlcnic: 28:80:23:41:c8:80: NC523SFP 10Gb 2-port Server Adapter Board Chip rev 0x54
[    3.897793] qlcnic 0000:01:00.0: using msi-x interrupts
[    3.976464] qlcnic 0000:01:00.0: eth0: XGbE port initialized
[    3.982301] qlcnic 0000:01:00.1: 2048KB memory map
[    4.022555] qlcnic 0000:01:00.1: Default minidump capture mask 0x1f
[    4.028902] qlcnic 0000:01:00.1: FW dump enabled
[    4.033593] qlcnic 0000:01:00.1: Supports FW dump capability
[    4.039330] qlcnic 0000:01:00.1: Driver v5.3.66, firmware v4.20.1
[    5.646145] qlcnic 0000:01:00.1: using msi-x interrupts
[    5.651561] qlcnic 0000:01:00.1: eth1: XGbE port initialized
[    6.316940] qlcnic 0000:01:00.1 e4: renamed from eth1
[    6.325670] qlcnic 0000:01:00.0 e3: renamed from eth0
[   42.959988] qlcnic 0000:01:00.0 eth1: renamed from e3
[   42.975714] qlcnic 0000:01:00.1 eth2: renamed from e4
[   49.754468] qlcnic 0000:01:00.1 eth2: Rx Context[1] Created, state 0x2
[   50.149781] qlcnic 0000:01:00.1 eth2: Tx Context[0x8001] Created, state 0x2
[   50.163831] qlcnic 0000:01:00.1 eth2: Tx Context[0x8009] Created, state 0x2
[   50.178885] qlcnic 0000:01:00.1 eth2: Tx Context[0x800b] Created, state 0x2
[   50.194942] qlcnic 0000:01:00.1 eth2: Tx Context[0x800d] Created, state 0x2
[   50.195643] qlcnic 0000:01:00.1 eth2: active nic func = 2, mac filter size=32
[   50.844813] qlcnic 0000:01:00.1 eth2: NIC Link is up
[   50.940553] qlcnic 0000:01:00.0 eth1: Rx Context[0] Created, state 0x2
[   51.122176] qlcnic 0000:01:00.0 eth1: Tx Context[0x8000] Created, state 0x2
[   51.136231] qlcnic 0000:01:00.0 eth1: Tx Context[0x8008] Created, state 0x2
[   51.152292] qlcnic 0000:01:00.0 eth1: Tx Context[0x800a] Created, state 0x2
[   51.168353] qlcnic 0000:01:00.0 eth1: Tx Context[0x800c] Created, state 0x2
[   51.169063] qlcnic 0000:01:00.0 eth1: active nic func = 2, mac filter size=32
[   52.845086] qlcnic 0000:01:00.0 eth1: NIC Link is up

```

```
:~$ sudo ethtool -i eth1
driver: qlcnic
version: 5.3.66
firmware-version: 4.20.1
expansion-rom-version:
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

```


is there another way than ethtool to do it?
is anything I can do ?

thanks in advance

---

