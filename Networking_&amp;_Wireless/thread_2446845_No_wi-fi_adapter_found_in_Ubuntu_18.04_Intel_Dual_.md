---
title: "No wi-fi adapter found in Ubuntu 18.04 Intel Dual band wireless 8260."
date: 2020-07-07
forum: Networking &amp; Wireless
---

### Post by cristianoarbex on 2020-07-07
I've had this PC for 3 years (Asus Zenbook). It is a dual boot, it used to be Windows 10 and Ubuntu 16.04, 3 months ago I upgraded to Ubuntu 18.04. Everything was working fine. **Wifi in Windows 10 is working fine.**

My laptop is an Asus Zenbook UX330UA, bios version 315. In Ubuntu I am getting the message "No wi-fi adapter found" in the settings. Secure boot  was enabled (I had disabled it when I first installed dual boot, not  sure why and when it was back to enabled). Even though in Asus Zenbook  the option to disable secure boot is grayed out, I could disable it by  disabling Fast Boot.

The problem began yesterday, (apparently) out of nowhere. **I also tried rebooting with a USB live stick containing Ubuntu 20.04 - and wifi was not detected**. But in Windows it always work.

Most of the times the network adapter is not found by Ubuntu. For instance, lshw shows no wireless card:

```

sudo lshw -C network: 

 *-network:0               
       description: Ethernet interface
       physical id: 1
       ...
  *-network:1
       description: Ethernet interface
       ...
  *-network:2
       description: Ethernet interface
       ...

```

Both ```
lspci -nnk | grep 0280 -A3
``` and  ```
sudo modprobe iwlwifi && dmesg | grep iwl
``` return nothing. Also, rfkill shows only bluetooth:

```

sudo rfkill list all 
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no


```


The firmware seems to be there:

```

ls /lib/firmware | grep 8000

iwlwifi-8000C-13.ucode
iwlwifi-8000C-16.ucode
iwlwifi-8000C-21.ucode
iwlwifi-8000C-22.ucode
iwlwifi-8000C-27.ucode
iwlwifi-8000C-31.ucode
iwlwifi-8000C-34.ucode
iwlwifi-8000C-36.ucode

```

Very rarely, when I reboot my computer, Ubuntu finds the wireless card, but wifi still does not work. When this is the case, I get this:

```

sudo lshw -C network
  *-network                 
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:127 memory:ef000000-ef001fff

```

```

lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:0110]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

```

sudo modprobe iwlwifi && dmesg | grep iwl
[    3.141197] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.159278] iwlwifi 0000:02:00.0: iwlwifi transaction failed, dumping registers
[    3.159282] iwlwifi 0000:02:00.0: iwlwifi device config registers:
[    3.159326] iwlwifi 0000:02:00.0: 00000000: 24f38086 00100006 0280003a 00000000 00000004 00000000 00000000 00000000
[    3.159327] iwlwifi 0000:02:00.0: 00000020: 00000000 00000000 00000000 01108086 00000000 000000c8 00000000 00000100
[    3.159329] iwlwifi 0000:02:00.0: iwlwifi device memory mapped registers:
[    3.159362] iwlwifi 0000:02:00.0: 00000000: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
[    3.159364] iwlwifi 0000:02:00.0: 00000020: ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff
[    3.159368] iwlwifi 0000:02:00.0: iwlwifi device AER capability structure:
[    3.159392] iwlwifi 0000:02:00.0: 00000000: 14010001 00100000 00000000 00462031 00002000 00000000 00000014 40000001
[    3.159393] iwlwifi 0000:02:00.0: 00000020: 0000000f ef00000c 00000000
[    3.159394] iwlwifi 0000:02:00.0: iwlwifi parent port (0000:00:1c.6) config registers:
[    3.159408] iwlwifi 0000:00:1c.6: 00000000: 9d168086 00100407 060400f1 00810010 00000000 00000000 00020200 200000f0
[    3.159409] iwlwifi 0000:00:1c.6: 00000020: ef00ef00 0001fff1 00000000 00000000 00000000 00000040 00000000 001003ff
[    3.159411] iwlwifi 0000:02:00.0: iwlwifi root port (0000:00:1c.6) AER cap structure:
[    3.159420] iwlwifi 0000:00:1c.6: 00000000: 14010001 00000000 00010000 00060011 00000000 00000000 0000000e 34000000
[    3.159422] iwlwifi 0000:00:1c.6: 00000020: 02001f10 00000000 00000000 00000007 00000000 000000e6
[    3.159461] WARNING: CPU: 3 PID: 347 at /build/linux-PK0ghA/linux-4.15.0/drivers/net/wireless/intel/iwlwifi/pcie/trans.c:1985 iwl_trans_pcie_grab_nic_access+0xea/0xf0 [iwlwifi]
[    3.159462] Modules linked in: iwlwifi(+) videobuf2_v4l2 videobuf2_core bluetooth i2c_algo_bit input_leds sr9700 fb_sys_fops serio_raw idma64 soundcore fjes(-) cfg80211 virt_dma videodev syscopyarea ecdh_generic sysfillrect joydev dm9601 media sysimgblt intel_lpss_pci(+) mei_me usbnet mii intel_lpss shpchp mei processor_thermal_device intel_pch_thermal intel_soc_dts_iosf wmi int3403_thermal int340x_thermal_zone acpi_als kfifo_buf video industrialio int3400_thermal acpi_thermal_rel asus_wireless mac_hid acpi_pad sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid i2c_hid ahci libahci hid
[    3.159491] RIP: 0010:iwl_trans_pcie_grab_nic_access+0xea/0xf0 [iwlwifi]
[    3.159508]  iwl_trans_pcie_alloc+0x98b/0xcb0 [iwlwifi]
[    3.159516]  iwl_pci_probe+0x1d/0x1d0 [iwlwifi]
[    3.159540]  iwl_pci_register_driver+0x24/0x40 [iwlwifi]
[    3.159549]  iwl_drv_init+0x89/0x8b [iwlwifi]
[    3.195121] iwlwifi 0000:02:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[    3.269650] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0xFFFC
[    3.269665] iwlwifi 0000:02:00.0: Error, can not clear persistence bit

```

Thanks in advance for any possible help in dealing with this matter. I run the diagnostics script and the file **wireless-info.tar.gz** is attached.

---

### Post by cristianoarbex on 2020-07-08
There has been new developments in my problem. When I initially  installed dual boot, I had initially disabled secure boot, but as  mentioned before for some reason it was enabled again. In the Asus  Zenbook BIOS, however, there was another option called **Secure Boot Control**, which was enabled. I don't know what it means, but I disabled it.

This  changed the behaviour a bit. The erratic behaviour is gone, now  everytime I restart the laptop in Ubuntu I see the following message:

```

  *-network UNCLAIMED       
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:ef000000-ef001fff

```

I the Update manager, I saw this:


[IMG]https://i.imgur.com/C75PAYc.png[/IMG]


The commands below show the following output:

```

lspci -nnk | grep 0280 -A3
02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:0110]
    Kernel modules: iwlwifi

```

```

sudo modprobe iwlwifi && dmesg | grep iwl
[    3.626468] iwlwifi 0000:02:00.0: Refused to change power state, currently in D3
[    3.626772] iwlwifi 0000:02:00.0: HW_REV=0xFFFFFFFF, PCI issues?
[    3.651088] iwlwifi: probe of 0000:02:00.0 failed with error -5

```


I tried installing:

```
 
 sudo apt install backport-iwlwifi-dkms

```

After rebooting, nothing changed, only the image below:

[IMG]https://ci5.googleusercontent.com/proxy/dpSdphg0jA5eGQlrTcfFSZ5GbHNRyruVYosV7N-LkxqTC1IeXdj1xOTSJMVgmEe_Djk=s0-d-e1-ft#https://i.imgur.com/XkwxWgd.png[/IMG]


Since then I purged the installation of backport-iwlwifi-dkms. Any help is greatly appreciated.

Edit: attached is the latest diagnostics file:
[ATTACH]286418[/ATTACH]

---

