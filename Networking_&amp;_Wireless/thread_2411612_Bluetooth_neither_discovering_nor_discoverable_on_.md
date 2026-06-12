---
title: "Bluetooth neither discovering nor discoverable on Ubuntu 18.04"
date: 2019-02-01
forum: Networking &amp; Wireless
---

### Post by vatsalgor on 2019-02-01
Hi all,

I have recently moved to Ubuntu 18.04 LTS from Windows. But I find an annoying problem in Ubuntu. My bluetooth is neither discovering nor discoverable to other bluetooth devices.
I have JBL 160BT earphone and they are pairing up with my mobile but not with my laptop. Even in my mobile phone the laptop is not discovered. 

Here is the result of following command for your reference:
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'

::::RESULTS::::

```
vatsal@Vatsal:~$ lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
06:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:0651]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 003: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    0.028077] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.052485] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   19.875411] Bluetooth: Core ver 2.22
[   19.875440] Bluetooth: HCI device and connection manager initialized
[   19.875446] Bluetooth: HCI socket layer initialized
[   19.875449] Bluetooth: L2CAP socket layer initialized
[   19.875457] Bluetooth: SCO socket layer initialized
[   20.142579] Bluetooth: hci0: BCM: chip id 70
[   20.143590] Bluetooth: hci0: BCM: features 0x06
[   20.159461] Bluetooth: hci0: Vatsal
[   20.159466] Bluetooth: hci0: BCM (001.001.011) build 0000
[   20.194178] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   20.194181] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   22.208061] Bluetooth: hci0: command 0x1003 tx timeout
[   26.773641] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.773643] Bluetooth: BNEP filters: protocol multicast
[   26.773647] Bluetooth: BNEP socket layer initialized
[   45.430654] Bluetooth: RFCOMM TTY layer initialized
[   45.430662] Bluetooth: RFCOMM socket layer initialized
[   45.430672] Bluetooth: RFCOMM ver 1.11
[   70.379684] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   86.253741] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  102.382658] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  118.255654] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  134.385678] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  150.258659] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  166.387786] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  182.260737] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  198.389803] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  214.261731] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  230.390812] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  246.263760] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  262.413775] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  278.305790] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  294.446827] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  310.328780] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  326.463863] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  342.341767] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  358.474882] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  374.350824] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  390.483891] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  406.359906] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  422.492977] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  438.367922] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  454.499903] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  470.374866] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  486.508948] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  502.383908] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  518.516901] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  534.391944] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  550.524952] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  566.399978] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  582.532909] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  598.407938] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  614.533940] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  630.399038] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  646.523036] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  662.390041] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  678.518012] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  694.387955] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  710.517058] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  726.388049] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  742.519058] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  758.392098] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  774.522106] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  790.393116] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  806.525122] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  822.398133] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  838.530140] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  854.404157] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  870.522160] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  886.371166] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  902.482161] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  918.341186] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  934.457190] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  950.321201] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  966.443204] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  982.309185] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  998.432195] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1014.301236] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1030.426239] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1046.295253] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1062.421259] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1078.291269] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1094.418276] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1110.288283] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1126.415304] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1142.285307] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1158.412295] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1174.284319] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1190.410328] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1206.282341] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1222.408347] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1238.279291] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1254.407330] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1270.278372] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1286.421261] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1297.010988] Bluetooth: hci0: BCM: chip id 70
[ 1297.011988] Bluetooth: hci0: BCM: features 0x06
[ 1297.028007] Bluetooth: hci0: BCM43142A
[ 1297.028013] Bluetooth: hci0: BCM (001.001.011) build 0000
[ 1297.028033] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[ 1297.028035] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[ 1299.052353] Bluetooth: hci0: command 0x1003 tx timeout
[ 1305.406161] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1321.299014] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1337.441104] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1353.323120] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1369.459046] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1385.337044] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1401.472061] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1417.348075] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1433.482056] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1449.358120] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1465.467204] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1481.317203] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1497.446117] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1513.322173] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1529.376228] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1545.116141] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1561.265135] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1577.248199] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1593.378147] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1609.169235] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1625.285183] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1641.166171] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1657.293199] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1673.162198] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1689.300215] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1705.418210] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1721.583314] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1737.148249] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1753.227317] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1769.317265] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1785.486299] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1801.383248] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1817.528360] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1833.410378] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1849.548303] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1865.428299] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1881.564407] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1897.445391] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1913.580426] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1929.460432] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1945.597438] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1961.476392] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1977.612458] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1993.492404] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2009.628475] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2025.508478] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2041.644482] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2057.525420] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2073.660507] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2089.509439] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2105.620497] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2121.483425] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2137.606537] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2153.477532] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2169.605470] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2185.478566] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2201.609476] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2217.437584] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2233.525589] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2249.372582] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2265.482507] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2281.347554] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2297.461596] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2313.325623] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2329.447646] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2345.347583] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2361.502552] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2377.391611] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2393.530572] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2409.409639] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2425.542791] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2441.421668] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2457.547619] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2473.229627] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2489.292648] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2505.225638] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2521.385643] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2537.126648] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2553.186718] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2569.230771] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2585.465775] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2601.366755] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2617.519706] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2633.409728] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2649.543825] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2665.425724] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2681.560835] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2697.440747] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2713.576753] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2729.456792] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2745.592860] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2761.472819] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2777.608786] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2793.488890] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2809.623803] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2825.504843] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2841.640842] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2857.521915] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2873.656929] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2889.536942] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2905.672849] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2921.571863] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2937.754901] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2953.651888] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2969.794895] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 2985.678899] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3001.827918] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3017.715968] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3033.854946] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3049.738953] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3065.880962] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3081.757993] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3097.897995] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3113.775961] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3129.958057] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3145.865011] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3162.018068] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3177.907104] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3194.048023] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3209.932060] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3226.070020] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3241.952062] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3258.037082] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 3273.884120] Bluetooth: hci0: last event is not cmd complete (0x0f)
```



Please help me with this one as I don't have any other wired earphones.

Thanks and regards,
Vatsal Gor

---

### Post by jeremy31 on 2019-02-01
In terminal try
```
sudo wget -O /lib/firmware/brcm/BCM.hcd https://github.com/winterheart/broadcom-bt-firmware/blob/master/brcm/BCM43142A0-0a5c-21d7.hcd
```
Shutdown and boot

---

### Post by vatsalgor on 2019-02-02
Hello Jeremy,

I tried the command you suggested.But the problem even got worse. I can't turn on my laptop's bluetooth device.

Here is the output of bluetoothctl and power on command: 

vatsal@Vatsal:~$ bluetoothctl
Agent registered
[bluetooth]# power on
No default controller available
[bluetooth]#


Also I am adding output of the ```
lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
``` command for your reference.

Thanks for prompt supprot. 

```

vatsal@Vatsal:~$ lspci -nnk | grep -iA2 net; lsusb; rfkill list all; dmesg | egrep -i 'blue|firm'
06:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: wl
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL810xE PCI Express Fast Ethernet controller [1028:0651]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0c45:6a04 Microdia 
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[    0.028110] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.052477] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[   21.870016] Bluetooth: Core ver 2.22
[   21.870039] Bluetooth: HCI device and connection manager initialized
[   21.870043] Bluetooth: HCI socket layer initialized
[   21.870045] Bluetooth: L2CAP socket layer initialized
[   21.870051] Bluetooth: SCO socket layer initialized
[   22.453924] Bluetooth: hci0: BCM: chip id 70
[   22.454878] Bluetooth: hci0: BCM: features 0x06
[   22.470901] Bluetooth: hci0: BCM43142A
[   22.470907] Bluetooth: hci0: BCM (001.001.011) build 0000
[   24.896022] Bluetooth: hci0: command 0x0a0a tx timeout
[   27.483464] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.483466] Bluetooth: BNEP filters: protocol multicast
[   27.483470] Bluetooth: BNEP socket layer initialized
[   32.992066] Bluetooth: hci0: BCM: Patch command 0a0a failed (-110)
[   35.104064] Bluetooth: hci0: command 0x1001 tx timeout
[   43.232128] Bluetooth: hci0: BCM: Reading local version info failed (-110)


```

---

