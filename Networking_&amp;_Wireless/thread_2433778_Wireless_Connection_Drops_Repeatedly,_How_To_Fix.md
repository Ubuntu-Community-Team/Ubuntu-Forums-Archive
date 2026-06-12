---
title: "Wireless Connection Drops Repeatedly, How To Fix?"
date: 2019-12-25
forum: Networking &amp; Wireless
---

### Post by soundchaser59 on 2019-12-25
My wireless connection works fine for a short time, but I've noticed it will eventually drop, usually within an hour or less. Doesn't seem to matter what I'm doing, sometimes I'm in Firefox when it drops, sometimes I'm in Chromium, sometimes it drops during software download and install, during updates, etc. meaning it seems to be unpredictable. And it will not reconnect, no matter what I do. The only way I can get it back is to reboot. Then rinse and repeat. 

I have two hard drives. one is 64 bit Ubuntu 18.04 and the other is 64 bit Mint 19. Not trying to be prickly, but I do want to note that I have been using Mint for a couple years on this same machine and I've never had this problem in Mint. It just stays connected all the time. I guess that observation makes me believe that the problem is not my hardware or my wireless router. Everything else in the house works fine, only my Ubuntu system drops the connection. After working so long in Mint with no issues I have gotten to where I forget to copy my posts and messages to a text editor so I don't lose any work. I've lost quite a bit of work in the last few days because of this glitch biting my rear end in Ubuntu. 

Other than giving up on Ubuntu and staying exclusively with Mint, what can I do to fix it and stop this maddening quirk from happening?

```
rootbeer@SC59:~$ lshw
WARNING: you should run this program as super-user.
sc59                        
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 3942MiB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl cpuid extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:e000(size=64) ioport:1c00(size=64) ioport:c400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fa007000-fa007fff
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fa006000-fa0060ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fa000000-fa003fff
     *-ide
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:26 memory:fa004000-fa004fff ioport:c800(size=8)
     *-storage
          description: RAID bus controller
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fa005000-fa005fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0 ioport:b000(size=4096) memory:f8000000-f9ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: Redwood XT [Radeon HD 5670/5690/5730]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:25 memory:e0000000-efffffff memory:f9000000-f901ffff ioport:b000(size=256) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Redwood HDMI Audio [Radeon HD 5000 Series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:24 memory:f9020000-f9023fff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: b
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4120B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlx00e04c082948
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.81 multicast=yes wireless=IEEE 802.11bgn
rootbeer@SC59:~$ 

```

---

### Post by jeremy31 on 2019-12-25
See the wireless script link in my signature and post results.  I really doubt there is something special in Mint that prevents the connection drop

---

### Post by soundchaser59 on 2019-12-25
> **jeremy31 said:**
> See the wireless script link in my signature and post results.  I really doubt there is something special in Mint that prevents the connection dropI am called away, but I will return soon to post the results. Thanks!

---

### Post by soundchaser59 on 2019-12-25
> **jeremy31 said:**
> See the wireless script link in my signature and post results.

I posted/pasted at pastebin, hope I did it correctly. Interesting to see the nearby ssid's in the report, with their speeds listed. 

[https://pastebin.com/itLRHu9e](https://pastebin.com/itLRHu9e)

---

### Post by jeremy31 on 2019-12-26
That is a private paste, how can we see it?

---

### Post by soundchaser59 on 2019-12-26
> **jeremy31 said:**
> That is a private paste, how can we see it?
I figured logged in pastebin users would see it. Let me see if I can change it to public or else re-upload it. 

Try it now. Seems like it was just a matter of edit and set it to public and save.

---

### Post by jeremy31 on 2019-12-26
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
See if that helps, it might help to go into Network Manager settings for the connection and set IPv6 to ignore/disable

---

### Post by soundchaser59 on 2019-12-26
> **jeremy31 said:**
> ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
See if that helps, it might help to go into Network Manager settings for the connection and set IPv6 to ignore/disable

Thank You. I think it is much more reliable now. As long as I don't change any wireless settings it keeps working, it has not dropped for quite some time now. If I look at wireless settings and change anything at all, then click "apply changes" it drops the connection and it will NOT reconnect without rebooting, no matter what I do. If I look at settings but do not change anything then the connection holds. As long as I let it work and leave it alone it stays connected. 

I just switched my usb wireless adapter to a usb port on this (new to me) pcie x1 adapter card I installed. So not only is the connection stable now, it is also much, much faster. Downloads that took minutes yesterday now complete in seconds or just one minute. 

I appreciate your time. The help I have received on this forum has been first rate!

---

