---
title: "Wifi Adaptor not found in Ubuntu 22.04 LTS"
date: 2022-09-15
forum: Networking &amp; Wireless
---

### Post by vaibhav05 on 2022-09-15
I have been using Ubuntu 22.04 for couple of days , the wifi was working fine, one fin day i noticed wifi adaptor not found working upon booting tried  various steps including re installing driver with no success

output of wireless info tool is [https://pastebin.ubuntu.com/p/tc77Rg4dgf/](https://pastebin.ubuntu.com/p/tc77Rg4dgf/)

the following output from nmlci shows "plugin missing"
> 
wlp13s0: unmanaged
        "Realtek RTL8723BE"
        wifi (rtl8723be), 44:1C:A8:03:A3:2F, plugin missing, hw, mtu 1500


then i checked the driver is installed , using lspci -nnk | grep 0280 -A3
> 0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be





nmcli d following output
> 
DEVICE   TYPE      STATE      CONNECTION 
enp7s0   ethernet  connected  Profile 1  
docker0  bridge    unmanaged  --         
lo       loopback  unmanaged  --         
wlp13s0  wifi      unmanaged  --  


lshw -v

> 0d:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 3000 [size=256]
    Memory at c3000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-23-b7-fe-ff-4c-e0-00
    Capabilities: [150] Latency Tolerance Reporting
    Capabilities: [158] L1 PM Substates
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be




i am getting following output when i run sudo iwlist wlp13s0 scan


> Cell 05 - Address: 42:9F:B2:58:A4:DB                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"vaibhav"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000011ef475d
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000776616962686176
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0A0017F206010103010000




> 
vaibhav@vaibhav-HP-Notebook:~$ sudo dmesg | grep rtl
[   82.899637] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_fw.bin
[   83.410237] Bluetooth: hci0: RTL: loading rtl_bt/rtl8723b_config.bin
[   83.410271] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
[   83.695596] rtl8723be: Using firmware rtlwifi/rtl8723befw_36.bin
[   83.699656] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   83.700442] rtlwifi: rtlwifi: wireless switch is on
[   83.731608] rtl8723be 0000:0d:00.0 wlp13s0: renamed from wlan0






Kindly Advise this can be resolved using any means , thank you

---

### Post by vaibhav05 on 2022-09-17
[COLOR=#232629][FONT=-apple-system]The solution to the problem is simple , after much research/circus and going through lots of solutions it was just 

> sudo apt-get reinstall network-manager :-D[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
Thanks for the amazing post [https://askubuntu.com/questions/1419194/no-wifi-adapter-found-in-ubuntu-20-04-ubuntu-22-04-lts](https://askubuntu.com/questions/1419194/no-wifi-adapter-found-in-ubuntu-20-04-ubuntu-22-04-lts)[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks @chilli555[/FONT][/COLOR]

---

