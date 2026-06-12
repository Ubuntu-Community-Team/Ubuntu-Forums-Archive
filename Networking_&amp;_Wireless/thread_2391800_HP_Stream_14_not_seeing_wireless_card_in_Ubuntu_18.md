---
title: "HP Stream 14 not seeing wireless card in Ubuntu 18.4"
date: 2018-05-13
forum: Networking &amp; Wireless
---

### Post by tornadoaftermath on 2018-05-13
Hello and thank you to everyone who takes the time to give me a hand with this issue.

I recently installed Ubuntu 18.4 from a flash drive, and setup for everything except the wireless card went very smoothly.  I am currently able to connect to the internet using a USB to ethernet adapter, and I have attempted (as far as I know) to take all of the steps outlined in the most closely-related thread to my problem: "[SOLVED] wifi not working ubuntu and ubuntu mate on hp stream 11," [https://ubuntuforums.org/showthread.php?t=2319153](https://ubuntuforums.org/showthread.php?t=2319153).

I have installed pastebinit, and ndiswrapper and my laptop's output can be found at: [http://paste.ubuntu.com/p/G68gTNnnMg/](http://paste.ubuntu.com/p/G68gTNnnMg/)

I can't seem to turn on or otherwise enable my wireless card using a keyboard shortcut, or various terminal commands.  

"lspci -vnn" gave the following output:
 mike@Phantom-HP-Stream-Laptop-14-ax0XX:~$ lspci -vvnn00:00.0 Host bridge [0600]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [8086:2280] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register [103c:82bd]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel driver in use: iosf_mbi_pci


00:02.0 VGA compatible controller [0300]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller [8086:22b1] (rev 35) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller [103c:82bd]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 117
    Region 0: Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
    Region 2: Memory at 80000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 2000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915


00:0b.0 Signal processing controller [1180]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller [8086:22dc] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller [103c:82bd]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 120
    Region 0: Memory at 91414000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device


00:14.0 USB controller [0c03]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [8086:22b5] (rev 35) (prog-if 30 [XHCI])
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller [103c:82bd]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 115
    Region 0: Memory at 91400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:1a.0 Encryption controller [1080]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [8086:2298] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine [103c:82bd]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 119
    Region 0: Memory at 91300000 (32-bit, non-prefetchable) [size=1M]
    Region 1: Memory at 91200000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: mei_txe
    Kernel modules: mei_txe


00:1b.0 Audio device [0403]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller [8086:2284] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller [103c:82bd]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 121
    Region 0: Memory at 91410000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


00:1c.0 PCI bridge [0604]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 [8086:22c8] (rev 35) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: 91100000-911fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1c.3 PCI bridge [0604]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #4 [8086:22ce] (rev 35) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin D routed to IRQ 19
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 91000000-910fffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:1f.0 ISA bridge [0601]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [8086:229c] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU [103c:82bd]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich


00:1f.3 SMBus [0c05]: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller [8086:2292] (rev 35)
    Subsystem: Hewlett-Packard Company Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller [103c:82bd]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 255
    Region 0: Memory at 91415000 (32-bit, non-prefetchable) [size=32]
    Region 4: I/O ports at 2040 [size=32]
    Capabilities: <access denied>
    Kernel modules: i2c_i801


01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
    Subsystem: Hewlett-Packard Company RTS5229 PCI Express Card Reader [103c:82bd]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 116
    Region 0: Memory at 91100000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
    Subsystem: Hewlett-Packard Company Device [103c:831b]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: I/O ports at 1000 [size=256]
    Region 2: Memory at 91000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: r8822be, wl

Also:

mike@Phantom-HP-Stream-Laptop-14-ax0XX:~$ lspci | grep Network
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device b822


My apologies for the formatting of this post not being correct; it has been a while since I've posted.

---

### Post by praseodym on 2018-05-13
[https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Driver installation. Uninstall the Broadcom-STA and blacklist r8822be

---

### Post by ush2018 on 2018-05-13
> **praseodym said:**
> [https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836](https://ubuntuforums.org/showthread.php?t=2367097&p=13669836#post13669836)

Driver installation. Uninstall the Broadcom-STA and blacklist r8822be

How would one uninstall the Broadcom-STA and what does "blacklist r8822be" mean?

---

### Post by tornadoaftermath on 2018-05-14
I downloaded Synaptic Package Manager from the Software center, and it didn't show that I had any Broadcom-STA drivers installed.  I should mention though that I am currently using a Netgear USB wifi antenna on the problem laptop in question without issue, so I am even more confused as to why the onboard hardware is being so problematic.  I also do currently have bcmwl-kernel-source installed for the Netgear adapter.

---

### Post by chili555 on 2018-05-14
>  I also do currently have bcmwl-kernel-source installed for the Netgear adapter.bcmwl-kernel-source is a driver for Broadcom chipsets; your is this:> 0bda:8152 [COLOR="#FF0000"]Realtek [/COLOR]Semiconductor Corp. It's not a Broadcom and its driver is shown in your paste:> GENERAL.DRIVER:                         r8152Please remove bcmwl-kernel-source:```
sudo apt purge bcmwl-kernel-source
```Remove the USB wireless, reboot and show us:```
sudo modprobe r8822be
dmesg | grep 8822
```

---

### Post by tornadoaftermath on 2018-05-14
Thanks for the response chili555.

The output for your requested commands was as follows:

```
mike@Phantom-HP-Stream-Laptop-14-ax0XX:~$ sudo modprobe r8822be
[sudo] password for mike: 
modprobe: ERROR: could not insert 'r8822be': Required key not available
mike@Phantom-HP-Stream-Laptop-14-ax0XX:~$ dmesg | grep 8822
[    5.159825] Bluetooth: hci0: rtl: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822
[    5.159830] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_config.bin
[    5.165271] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_fw.bin
```

---

### Post by chili555 on 2018-05-15
> ERROR: could not insert 'r8822be': Required key not availableAh, haaaa!! 

Please see: [https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

In short, turn off Secure Boot and you should be all set.

---

### Post by tornadoaftermath on 2018-05-15
Thanks a million chili555!

I turned off Secure Boot, and after restarting and removing my Netgear USB antenna my laptop started using the on-board wireless card with no issue!

The command that I ended up using was :

```
sudo mokutil --disable-validation
```

as described in the article that chili555 linked in the above comment.

Happy to report that my laptop is now running smoothly and using all of the built-in hardware!

---

