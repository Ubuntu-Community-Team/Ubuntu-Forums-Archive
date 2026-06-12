---
title: "Wireless Broadcom pci 14e4:43ec on Ubuntu 18.04 not supported?"
date: 2018-05-07
forum: Networking &amp; Wireless
---

### Post by markie0425 on 2018-05-07
Hi all,

I'm new to Ubuntu/Linux world and i'll say i'm 4 days old in this environment. I wanted to play around with it more but I am having issues with my WiFi as my device is not able to detect the adapter.
It's been 3 days for me trying to troubleshoot it, learning and understanding the commands along the way, also reinstalling and switching between Windows and Ubuntu back and forth but no luck.
I've also search around the forums for similar problem but their solution doesn't seem to work for me. I'm not good at technical stuff and I need some assurance and or guidance if i'm doing this properly therefore no choice but to post a thread for assistance.

I've followed this [sticky thread ]("https://ubuntuforums.org/showthread.php?t=2214110")as it is related to my Broadcom and on the thread, it appears that my[COLOR=#b22222]* Broadcom pci.id 14e4:43ec (rev 02)*[/COLOR] is not listed, does that mean that there's no package for my Broadcom and no work around for it?

The device I'm using is Huawei Matebook and here are the info or command outputs

                 
```

lspci -vvnn | grep Network
01:00.0 Network controller [0280]: Broadcom Limited BCM4356 802.11ac Wireless Network Adapter [14e4:43ec] (rev 02)
    Subsystem: Huawei Technologies Co., Ltd. BCM4356 802.11ac Wireless Network Adapter [19e5:3100]

```

```

sudo lshw -C network
  *-network UNCLAIMED       
       description: Network controller
       product: BCM4356 802.11ac Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df800000-df807fff memory:df400000-df7fffff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enx00e04c6803e1
       serial: 00:e0:4c:68:03:e1
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=192.168.1.211 link=yes multicast=yes port=MII speed=1Gbit/s

```

```

iwconfig
lo        no wireless extensions.

enx00e04c6803e1  no wireless extensions.

```

My secure boot is disabled, I've done purging and reinstalling bcmwl-kernel-source or firmware-b43-installer process, rebooting the device everytime. Also tried installing windows driver with ndiswrapper but still no luck. Any help would be appreciated or just a link to any source.

Thank you.

---

### Post by praseodym on 2018-05-09
Unknown so far. Please run
```

modprobe -c | grep -i "14e4.*43ec"
```

Edit: Ok, it shows the module "brcmfmac". Lets try

```
sudo modprobe -v brcmfmac
dmesg | grep brcm
```

---

### Post by r3v4n2 on 2018-06-13
Hi, I also have problem with drivers for Wireless Broadcom pci 14e4:43ec on Ubuntu 18.04.

```

$ sudo modprobe -v brcm
$ dmesg | grep brcmfmac

[ 5487.896514] usbcore: registered new interface driver brcmfmac
[ 5488.005535] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac4356-pcie.bin for chip 0x004356(17238) rev 0x000002
[ 5488.011213] brcmfmac 0000:04:00.0: Direct firmware load for brcm/brcmfmac4356-pcie.txt failed with error -2
[ 5490.501082] brcmfmac: brcmf_msgbuf_query_dcmd: Timeout on response for query command
[ 5490.501099] brcmfmac: brcmf_c_preinit_dcmds: Retreiving cur_etheraddr failed, -5
[ 5490.501107] brcmfmac: brcmf_bus_started: failed: -5
[ 5490.501121] brcmfmac: brcmf_pcie_attach_bus: dongle is not responding

```

What should I do?

---

