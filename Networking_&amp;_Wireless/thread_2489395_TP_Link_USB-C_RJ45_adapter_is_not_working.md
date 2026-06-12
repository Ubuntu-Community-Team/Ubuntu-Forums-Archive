---
title: "TP Link USB-C RJ45 adapter is not working"
date: 2023-07-28
forum: Networking &amp; Wireless
---

### Post by tatianepires on 2023-07-28
I have an issue that is likely to be similar to [this]("https://ubuntuforums.org/showthread.php?t=2470874"), but the author marked it as solved without being able to provide specific steps on how to solve the issue.

I have an USB Type-C to RJ45 Gigabit adapter from tp-link, model UE300C ver 2.0. I tested it on my phone, and it worked, so it rules out that the problem could be the adapter itself.

I'm running Ubuntu 22.04. Here's what I have so far.

```
$ lsusb
Bus 004 Device 002: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
```

```
$ echo "$(uname -r)"
5.19.0-50-generic
```

```
$ sudo modprobe ax88179
modprobe: FATAL: Module ax88179 not found in directory /lib/modules/5.19.0-50-generic
```

```
$ ls -l /usr/lib/modules/$(uname -r)/kernel/drivers/net/usb/
-rw-r--r-- 1 root root  96697 jul 10 13:13 ax88179_178a.ko
```

```
$ lsmod | grep ax88
ax88179_178a           36864  0
usbnet                 53248  4 cdc_mbim,cdc_ncm,cdc_ether,ax88179_178a
mii                    20480  3 usbnet,r8152,ax88179_178a
```

```
$ sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
Status: install ok installed
```

```
$ sudo modprobe ax88179_178a
```
This doesn't have any output. But the adapter doesn't work.

```
$ sudo apt install linux-modules-extra-5.19.0-50-generic 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
linux-modules-extra-5.19.0-50-generic is already the newest version (5.19.0-50.50).
```

```
$ sudo dmesg | grep ax88
[13381.992686] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.003264] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.216861] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.330285] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[13382.330304] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): invalid MAC address, using random
[13382.342038] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[13382.352482] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[13382.362695] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.373330] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.383603] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.395339] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.405765] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.416172] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.426699] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.437213] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[13382.449170] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13382.459560] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[13382.469841] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[13382.480389] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[13382.490806] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13382.502675] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13382.513187] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13382.523458] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[13382.533875] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13382.544438] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13382.556263] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13382.566677] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13382.577137] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[13382.577824] ax88179_178a 4-1:2.0 eth0: register 'ax88179_178a' at usb-0000:00:0d.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet, ca:89:78:f4:0d:bc
[13382.718275] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.728765] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13382.940809] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.052429] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -32
[13383.052446] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): invalid MAC address, using random
[13383.062709] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[13383.073260] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32
[13383.085148] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.095498] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.105841] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.116206] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.126712] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13383.138651] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.149235] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -32
[13383.159649] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -32
[13383.170269] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -32
[13383.180530] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[13383.192666] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -32
[13383.203263] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -32
[13383.213667] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13383.224223] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13383.234711] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13383.246625] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -32
[13383.257186] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13383.267672] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13383.278176] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -32
[13383.288606] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -32
[13383.300377] ax88179_178a 4-1:2.1 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -32
[13383.300646] ax88179_178a 4-1:2.1 eth1: register 'ax88179_178a' at usb-0000:00:0d.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet, 56:c9:9f:9d:4e:a4
[13383.345213] usbcore: registered new interface driver ax88179_178a
[13383.397436] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -32
[13383.410496] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -32
[13383.625373] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.739153] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0001: -32
[13383.750744] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0006: -32
[13383.750748] ax88179_178a 4-1:2.0 eth0: invalid MAC address, using random
[13383.762506] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0006: -32
[13383.775573] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0005: -32
[13383.787145] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.798757] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.810518] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.822267] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.835340] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -32
[13383.846923] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.858521] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -32
[13383.870280] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0001: -32
[13383.881826] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -32
[13383.894949] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x001f: -32
[13383.906731] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0019: -32
[13383.918311] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x001f: -32
[13383.929833] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -32
[13383.941506] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -32
[13383.954538] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -32
[13383.966143] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x000e: -32
[13383.977687] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -32
[13383.989529] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -32
[13384.001268] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -32
[13384.014327] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -32
[13384.024664] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0000: -32
[13384.079341] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0002: -32
[13384.089687] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0002: -32
[13384.306202] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.422033] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x0001: -32
[13384.435208] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x0006: -32
[13384.435218] ax88179_178a 4-1:2.1 eth1: invalid MAC address, using random
[13384.446833] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0006: -32
[13384.458418] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0005: -32
[13384.469942] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.480368] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.493413] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.505161] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.516776] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0002: -32
[13384.528401] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.539940] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0002: -32
[13384.553097] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x0001: -32
[13384.563519] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0001: -32
[13384.575085] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x001f: -32
[13384.586640] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0019: -32
[13384.597057] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x001f: -32
[13384.610150] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000d: -32
[13384.621653] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000e: -32
[13384.632108] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000d: -32
[13384.643684] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x000e: -32
[13384.655444] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000d: -32
[13384.667423] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000e: -32
[13384.679167] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000d: -32
[13384.690754] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x000e: -32
[13384.702404] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x0000: -32
[15564.405988] usbcore: deregistering interface driver ax88179_178a
[15564.420622] ax88179_178a 4-1:2.1 eth1: unregister 'ax88179_178a' usb-0000:00:0d.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[15564.428241] ax88179_178a 4-1:2.1 eth1: Failed to read reg index 0x0002: -71
[15564.435470] ax88179_178a 4-1:2.1 eth1: Failed to write reg index 0x0002: -71
[15564.479672] ax88179_178a 4-1:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -71
[15564.486809] ax88179_178a 4-1:2.1 eth1 (unregistered): Failed to write reg index 0x0001: -71
[15564.493919] ax88179_178a 4-1:2.1 eth1 (unregistered): Failed to write reg index 0x0002: -71
[15564.515475] ax88179_178a 4-1:2.0 eth0: unregister 'ax88179_178a' usb-0000:00:0d.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet
[15564.522631] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0002: -71
[15564.529850] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -71
[15564.571846] ax88179_178a 4-1:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -71
[15564.578940] ax88179_178a 4-1:2.0 eth0 (unregistered): Failed to write reg index 0x0001: -71
[15564.585986] ax88179_178a 4-1:2.0 eth0 (unregistered): Failed to write reg index 0x0002: -71
[15607.092380] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -71
[15607.099641] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -71
[15607.311708] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.423469] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0006: -71
[15607.423492] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): invalid MAC address, using random
[15607.430550] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -71
[15607.437701] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -71
[15607.444679] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.451654] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.458876] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.465803] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.472972] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -71
[15607.479987] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.486929] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0002: -71
[15607.494101] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0001: -71
[15607.501119] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0001: -71
[15607.508173] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -71
[15607.515348] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0019: -71
[15607.522312] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x001f: -71
[15607.529466] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -71
[15607.536514] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -71
[15607.543823] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -71
[15607.550922] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x000e: -71
[15607.558055] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -71
[15607.565174] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -71
[15607.572296] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000d: -71
[15607.579432] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x000e: -71
[15607.586544] ax88179_178a 4-1:2.0 (unnamed net_device) (uninitialized): Failed to read reg index 0x0000: -71
[15607.587318] ax88179_178a 4-1:2.0 eth0: register 'ax88179_178a' at usb-0000:00:0d.0-1, ASIX AX88179 USB 3.0 Gigabit Ethernet, be:28:5a:28:50:3d
[15607.623434] ax88179_178a: probe of 4-1:2.1 failed with error -71
[15607.623575] usbcore: registered new interface driver ax88179_178a
[15607.643683] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -71
[15607.650734] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -71
[15607.863494] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15607.975535] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0001: -71
[15607.982660] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0006: -71
[15607.982662] ax88179_178a 4-1:2.0 eth0: invalid MAC address, using random
[15607.989726] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0006: -71
[15607.996913] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0005: -71
[15608.004043] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.011170] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.018294] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.025380] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.032441] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -71
[15608.039668] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.046807] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0002: -71
[15608.053922] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0001: -71
[15608.061056] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0001: -71
[15608.068181] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x001f: -71
[15608.075378] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x0019: -71
[15608.082436] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x001f: -71
[15608.089605] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -71
[15608.096788] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -71
[15608.103885] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -71
[15608.110866] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x000e: -71
[15608.117985] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -71
[15608.125182] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -71
[15608.132268] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000d: -71
[15608.139361] ax88179_178a 4-1:2.0 eth0: Failed to write reg index 0x000e: -71
[15608.146484] ax88179_178a 4-1:2.0 eth0: Failed to read reg index 0x0000: -71
```

I searched for "ubuntu 22.04 install axge driver" and got to this page [https://manpages.ubuntu.com/manpages/xenial/man4/axge.4freebsd.html](https://manpages.ubuntu.com/manpages/xenial/man4/axge.4freebsd.html) I've been using Ubuntu for some time now, but I never needed to do anything related to compile kernel. What if something goes wrong? I don't like the idea of "playing" with kernel stuff. That same manpage says to edit loader.conf, but it does not say where the file is, and I haven't found it yet.

> Alternatively, to load the driver as a module at boot time, place the following line in
     loader.conf(5):

           if_axge_load="YES"

I would really appreciate some help. Thanks!

---

### Post by chili555 on 2023-07-30
I've been unable to find the source code for axge; I have no idea how to build or install it. I suggest that you abandon that course.

I found this: [https://bugzilla.kernel.org/show_bug.cgi?id=212731](https://bugzilla.kernel.org/show_bug.cgi?id=212731) and I was very interested in comment #15:

> This issue is still present on Ubuntu 5.19.0-35-generic

[Fri Mar 24 10:21:15 2023] ax88179_178a 2-1.4:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0006: -32
[Fri Mar 24 10:21:15 2023] ax88179_178a 2-1.4:2.0 (unnamed net_device) (uninitialized): Failed to write reg index 0x0005: -32


Switching to the driver at [https://github.com/nothingstopsme/AX88179_178A_Linux_Driver](https://github.com/nothingstopsme/AX88179_178A_Linux_Driver) resolved the issue for meI suggest that you try that driver. With a temporary internet connection by ethernet, tethering or whatever means possible:

```
sudo apt update
sudo apt install build-essential git bc
git clone https://github.com/nothingstopsme/AX88179_178A_Linux_Driver.git
cd AX88179_178A_Linux_Driver/source
make
```This builds on my 23.04 system with a few possibly harmless warnings. If you run:

```
ls
```

...immediately after the build compiles and you see:

```
ax88179_178a.c   ax88179_178a.mod    ax88179_178a.o  Module.symvers
ax88179_178a.h   ax88179_178a.mod.c  Makefile        readme
[COLOR="#FF0000"]ax88179_178a.ko[/COLOR]  ax88179_178a.mod.o  modules.order
```...then you know that the module built successfully. Then do:

```
sudo make install
```

Reboot. Any improvement?

---

### Post by tatianepires on 2023-07-31
Thank you, chili555 for posting it in a detailed way. I tried this solution, but unfortunately it did not work here. I saved terminal output before I restarted the computer, so I'll post here the output of make and what change after make install.

I replaced my actual username with "username", other than that, the output is untouched:
```
$ make
make -C /lib/modules/5.19.0-50-generic/build M=/home/username/Downloads/AX88179_178A_Linux_Driver/source modules
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-50-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
  You are using:           gcc (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
  CC [M]  /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.o
In file included from ./include/linux/string.h:253,
                 from ./include/linux/bitmap.h:11,
                 from ./include/linux/cpumask.h:12,
                 from ./arch/x86/include/asm/cpumask.h:5,
                 from ./arch/x86/include/asm/msr.h:11,
                 from ./arch/x86/include/asm/processor.h:22,
                 from ./arch/x86/include/asm/timex.h:5,
                 from ./include/linux/timex.h:67,
                 from ./include/linux/time32.h:13,
                 from ./include/linux/time.h:60,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:13,
                 from /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:30:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c: In function &#8216;ax88179_set_mac_addr&#8217;:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1016:19: warning: passing argument 1 of &#8216;__builtin_memcpy&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 1016 |         memcpy(net->dev_addr, addr->sa_data, ETH_ALEN);
      |                ~~~^~~~~~~~~~
./include/linux/fortify-string.h:379:27: note: in definition of macro &#8216;__fortify_memcpy_chk&#8217;
  379 |         __underlying_##op(p, q, __fortify_size);                        \
      |                           ^
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1016:9: note: in expansion of macro &#8216;memcpy&#8217;
 1016 |         memcpy(net->dev_addr, addr->sa_data, ETH_ALEN);
      |         ^~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1016:19: note: expected &#8216;void *&#8217; but argument is of type &#8216;const unsigned char *&#8217;
 1016 |         memcpy(net->dev_addr, addr->sa_data, ETH_ALEN);
      |                ~~~^~~~~~~~~~
./include/linux/fortify-string.h:379:27: note: in definition of macro &#8216;__fortify_memcpy_chk&#8217;
  379 |         __underlying_##op(p, q, __fortify_size);                        \
      |                           ^
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1016:9: note: in expansion of macro &#8216;memcpy&#8217;
 1016 |         memcpy(net->dev_addr, addr->sa_data, ETH_ALEN);
      |         ^~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1020:47: warning: passing argument 6 of &#8216;ax88179_write_cmd&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 1020 |                                  ETH_ALEN, net->dev_addr);
      |                                            ~~~^~~~~~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:219:46: note: expected &#8216;void *&#8217; but argument is of type &#8216;const unsigned char *&#8217;
  219 |                              u16 size, void *data)
      |                                        ~~~~~~^~~~
In file included from ./include/linux/string.h:253,
                 from ./include/linux/bitmap.h:11,
                 from ./include/linux/cpumask.h:12,
                 from ./arch/x86/include/asm/cpumask.h:5,
                 from ./arch/x86/include/asm/msr.h:11,
                 from ./arch/x86/include/asm/processor.h:22,
                 from ./arch/x86/include/asm/timex.h:5,
                 from ./include/linux/timex.h:67,
                 from ./include/linux/time32.h:13,
                 from ./include/linux/time.h:60,
                 from ./include/linux/stat.h:19,
                 from ./include/linux/module.h:13,
                 from /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:30:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c: In function &#8216;access_eeprom_mac&#8217;:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1454:32: warning: passing argument 1 of &#8216;__builtin_memcpy&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 1454 |                 memcpy(dev->net->dev_addr, buf, ETH_ALEN);
      |                        ~~~~~~~~^~~~~~~~~~
./include/linux/fortify-string.h:379:27: note: in definition of macro &#8216;__fortify_memcpy_chk&#8217;
  379 |         __underlying_##op(p, q, __fortify_size);                        \
      |                           ^
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1454:17: note: in expansion of macro &#8216;memcpy&#8217;
 1454 |                 memcpy(dev->net->dev_addr, buf, ETH_ALEN);
      |                 ^~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1454:32: note: expected &#8216;void *&#8217; but argument is of type &#8216;const unsigned char *&#8217;
 1454 |                 memcpy(dev->net->dev_addr, buf, ETH_ALEN);
      |                        ~~~~~~~~^~~~~~~~~~
./include/linux/fortify-string.h:379:27: note: in definition of macro &#8216;__fortify_memcpy_chk&#8217;
  379 |         __underlying_##op(p, q, __fortify_size);                        \
      |                           ^
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1454:17: note: in expansion of macro &#8216;memcpy&#8217;
 1454 |                 memcpy(dev->net->dev_addr, buf, ETH_ALEN);
      |                 ^~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c: In function &#8216;ax88179_get_mac&#8217;:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1516:54: warning: passing argument 2 of &#8216;access_eeprom_mac&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 1516 |                 ret = access_eeprom_mac(dev, dev->net->dev_addr, 0x0, 1);
      |                                              ~~~~~~~~^~~~~~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1417:54: note: expected &#8216;u8 *&#8217; {aka &#8216;unsigned char *&#8217;} but argument is of type &#8216;const unsigned char *&#8217;
 1417 | static int access_eeprom_mac(struct usbnet *dev, u8 *buf, u8 offset, int wflag)
      |                                                  ~~~~^~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:1553:45: warning: passing argument 6 of &#8216;ax88179_write_cmd&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 1553 |                           ETH_ALEN, dev->net->dev_addr);
      |                                     ~~~~~~~~^~~~~~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:219:46: note: expected &#8216;void *&#8217; but argument is of type &#8216;const unsigned char *&#8217;
  219 |                              u16 size, void *data)
      |                                        ~~~~~~^~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c: In function &#8216;ax88179_reset&#8217;:
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:2283:45: warning: passing argument 6 of &#8216;ax88179_write_cmd&#8217; discards &#8216;const&#8217; qualifier from pointer target type [-Wdiscarded-qualifiers]
 2283 |                           ETH_ALEN, dev->net->dev_addr);
      |                                     ~~~~~~~~^~~~~~~~~~
/home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.c:219:46: note: expected &#8216;void *&#8217; but argument is of type &#8216;const unsigned char *&#8217;
  219 |                              u16 size, void *data)
      |                                        ~~~~~~^~~~
  MODPOST /home/username/Downloads/AX88179_178A_Linux_Driver/source/Module.symvers
  CC [M]  /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.mod.o
  LD [M]  /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.ko
  BTF [M] /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.ko
Skipping BTF generation for /home/username/Downloads/AX88179_178A_Linux_Driver/source/ax88179_178a.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-5.19.0-50-generic'
```

ls after running make:
```
$ ls
ax88179_178a.c  ax88179_178a.ko   ax88179_178a.mod.c  ax88179_178a.o  modules.order   readme
ax88179_178a.h  ax88179_178a.mod  ax88179_178a.mod.o  Makefile        Module.symvers
```

make install:
```
$ sudo make install
cp -v ax88179_178a.ko /lib/modules/5.19.0-50-generic/kernel/drivers/net/usb && /sbin/depmod -a
'ax88179_178a.ko' -> '/lib/modules/5.19.0-50-generic/kernel/drivers/net/usb/ax88179_178a.ko'
```

This changed from my previous post, there was no output for this modprobe before.
```
$ sudo modprobe ax88179_178a
modprobe: ERROR: could not insert 'ax88179_178a': Key was rejected by service
```

---

### Post by chili555 on 2023-07-31
> Key was rejected by servicePlease try turning off Secure Boot.

---

### Post by tatianepires on 2023-07-31
> **chili555 said:**
> Please try turning off Secure Boot.

Do you mean in the BIOS? I followed a tutorial to install Ubuntu 22.04 with UEFI Secure Boot and MOK enabled. I don't think that disable it is an option for me.

---

### Post by chili555 on 2023-07-31
Did you try it? What happens?

---

### Post by tatianepires on 2023-07-31
> **chili555 said:**
> Did you try it? What happens?

When Ubuntu did not have support for Secure Boot, then I had no choice but to disable it. I think it's about 10 years ago when I installed Ubuntu on my previous (by that time second) notebook (and the first I've ditched dual boot in favor of only using Ubuntu), but I digress. LOL

I'm all for every possible security measure one can use to protect devices. Security Boot exists for a reason. It can be disabled if someone needs/prefers, which is great. But in this matter I will choose not to disable it.

I did take a look at the actual code available [https://github.com/nothingstopsme/AX88179_178A_Linux_Driver](https://github.com/nothingstopsme/AX88179_178A_Linux_Driver) just for peace of mind. It's not like it's PHP doing something with a query from a database or CSS working it's "magic" to the frontend of a website, so I knew I wouldn't fully understand what's going on there. But what I saw didn't startle me.

I do consider that it's very likely the code there is harmless. I tried to install it after all. But, to me, it does create a precedent I don't want to: disable Secure Boot, install something, then (assuming it's possible, I guess probably would be) enable Security Boot again. Then why to use that in the first place, if one's going to approach it like this? LOL

Thank you very much, chili555, for your time and readiness to help!

I will continue looking for another solution that does not require going that way.

---

### Post by tatianepires on 2023-08-08
One interesting development to this story. Now the adapter worked. It's an Ugreen USB-C RJ45 Gigabit adapter, but lsusb has the same output that it did for TP-Link adapter, it uses the same driver, ASIX Electronics Corp. AX88179 Gigabit Ethernet.

I was facing [this issue]("https://askubuntu.com/questions/1481452/ubuntu-22-04-3-lts-wont-power-off") of not being able to restart/poweroff the computer with kernel 6.2.0-26-generic, so I followed [this guide]("https://www.groovypost.com/howto/how-to-downgrade-the-kernel-in-ubuntu/") to downgrade the kernel back to 5.19.0-50-generic that had no restart/power problems, which I happened to know because of this issue with the adapter.

Here's what I think might have happened: when Ubuntu "worked its magic" after I selected the kernel 5.19.0-50-generic on Grub Advanced Options, the new driver (the one from GitHub, that did not work before because of Secure Boot) was compiled by Ubuntu itself into the kernel.

Because now the adapter is recognized by the system and operates in gigabit.

---

### Post by chili555 on 2023-08-08
Awesome! Glad it's working.

I love a happy ending by whatever means.

---

