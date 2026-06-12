---
title: "WiFi is disabled by hardware switch after suspend, on upgrading to 16.10"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by captaindavinci on 2017-02-23
I have searched all over the internet for a solution and have found none which works, 
I am desperately in need of some help in order to solve this problem.


[LIST]
[*]Tried pressing fn + f12 (which looks like it may be related to wifi).
[*]```
sudo modprobe hp_wmi
```.
[*]```
rfkill unblock all
```.
[*]resetting BIOS to default.
[/LIST]
However, whenever I restart my system, WiFi is enabled and I am able to connect to it. But after sometime or may be after I suspend and wake up the system, WiFi will be disabled by hardware switch.


 $ lspci -knn | grep Net -A2




```
    08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:804c]
    Kernel driver in use: rtl8723be
    Kernel modules: rtl8723be

```


$ iwconfig


```
    lo        no wireless extensions.

    eno1      no wireless extensions.

    wlo1      IEEE 802.11  ESSID:off/any  
              Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
              Retry short limit:7   RTS thr=2347 B   Fragment thr:off
              Power Management:off


```

$ lspci -k


    ```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
``````

        Subsystem: Hewlett-Packard Company Broadwell-U Host Bridge -OPI
        Kernel driver in use: bdw_uncore
    00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
        DeviceName: Intel(R) Graphics GT2
        Subsystem: Hewlett-Packard Company HD Graphics 5500
        Kernel driver in use: i915
        Kernel modules: i915
    00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
        Subsystem: Hewlett-Packard Company Broadwell-U Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
    00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
        Subsystem: Hewlett-Packard Company Broadwell-U Processor Thermal Subsystem
        Kernel driver in use: proc_thermal
        Kernel modules: processor_thermal_device
    00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP USB xHCI Controller
        Kernel driver in use: xhci_hcd
    00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP MEI Controller
        Kernel driver in use: mei_me
        Kernel modules: mei_me
    00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP High Definition Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
    00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
    00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP LPC Controller
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
    00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP SATA Controller [AHCI Mode]
        Kernel driver in use: ahci
        Kernel modules: ahci
    00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Wildcat Point-LP SMBus Controller
        Kernel modules: i2c_i801
    08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
        DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
        Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter
        Kernel driver in use: rtl8723be
        Kernel modules: rtl8723be
    09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 0a)
        DeviceName: Realtek PCIe FE Family Controller
        Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
        Kernel driver in use: r8169
        Kernel modules: r8169
    0a:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360] (rev 81)
        Subsystem: Hewlett-Packard Company Radeon R7 M360
        Kernel driver in use: amdgpu
        Kernel modules: amdgpu



```

$ rfkill list
```


    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes



```

NOTE There is no physical switch on my system. Ethernet also works perfectly. Also, WiFi was working perfectly before upgrading to 16.10.

---

### Post by jeremy31 on 2017-02-25
*Thread moved to **Networking & Wireless**.*

---

