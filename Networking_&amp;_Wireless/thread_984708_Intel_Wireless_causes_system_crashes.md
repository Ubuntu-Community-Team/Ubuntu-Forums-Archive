---
title: "Intel Wireless causes system crashes"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by elfdude on 2008-11-16
Hello, I'm a newb to posting to support forums, but familiar with using Linux.  The problem I'm having is that my Acer Aspire 5610 with Ubuntu 8.10 installed randomly freezes up with the caps lock led blinking, requiring a hard reboot to recover.  It usually happens after 30 - 60 minutes after a startup when I'm using my wireless connection (browsing, downloading, etc.)  The only way I've been able to avoid the problem is to use the hardware switch to turn off the wireless card or when I boot the laptop into Vista (oh, the pain.)

Over a year ago I installed a version of Ubuntu (7.something, sorry I don't remember the exact ver num) and didn't have a problem at all.  Then later I upgraded it to a newer version and started having this very problem.  I don't often have much time to spend troubleshooting, so I've just been using Vista.  But I recently had a chance to install Ubuntu 8.10 hoping that would solve the problem, but unfortunately not.

Last week I read through several forums following their suggestions, but none appear to solve my problem, including installing the linux-backports-modules-intrepid package.  I've seen it often requested to include the results of lspci, so I'll proactively include that as an attachment in case it's helpful.  Also I've included a couple of log files from a few crashes that have happened as I'm writing this (times of crash shown here by the results of running 'last')

------------------------------------------------------------------------
reboot   system boot  2.6.27-7-generic Sun Nov 16 20:52 - 20:55  (00:03)    
elfdude  pts/0        :0.0             Sun Nov 16 20:45 - crash  (00:07)    
elfdude  tty7         :0               Sun Nov 16 20:42 - crash  (00:09)    
reboot   system boot  2.6.27-7-generic Sun Nov 16 20:41 - 20:55  (00:14)    
elfdude  pts/0        :0.0             Sun Nov 16 20:09 - crash  (00:32)    
------------------------------------------------------------------------

Can someone please let me know what else I can look at or do to help me avoid the issue?  I'd really love to avoid booting into Vista. :)  Thanks.

---

### Post by SaintDanBert on 2009-12-17
There are numerous launchpad bugs that speak to this and similar failures **... and it has been months if not years without solution ...** in spite of new releases.  **What gives?**

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1202307.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1202307.html)

[https://launchpad.net/bugs/289808](https://launchpad.net/bugs/289808)

[https://lists.ubuntu.com/archives/kernel-bugs/2009-February/047384.html](https://lists.ubuntu.com/archives/kernel-bugs/2009-February/047384.html)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300693 ](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/300693 )

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303276)

[https://bugzilla.redhat.com/show_bug.cgi?id=514033](https://bugzilla.redhat.com/show_bug.cgi?id=514033)

Do I really need to keep this going?

Someone reported that they had solved this:
[http://ubuntuforums.org/showthread.php?t=968792](http://ubuntuforums.org/showthread.php?t=968792)
However, the problem persists throughout the releases since Hardy (v8.04.3 LTS).

I don't know what someone needs to know to fix this.

My **sudo lshw** reports
```

    *-network
        description: Wireless interface
        product: PRO/Wireless 4965 AG or AGN Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:03:00.0
        logical name: wmaster0
        version: 61
        serial: 00:21:5c:03:39:07
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list 
            logical ethernet physical wireless
        configuration: broadcast=yes driver=iwl4965 latency=0
            module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

My **sudo lspci** reports
```

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
    Subsystem: Intel Corporation Lenovo ThinkPad T51
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- 
    VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast 
        >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 219
    Region 0: Memory at f7f00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA 
        PME (D0+,D1-,D2-,D3hot+,D3cold+)
    Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+
        Queue=0/0 Enable+
    Address: 00000000fee0300c  Data: 4133
    Capabilities: [e0] Express Endpoint IRQ 0
    Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
    Device: Latency L0s <512ns, L1 unlimited
    Device: AtnBtn- AtnInd- PwrInd-
    Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
    Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
    Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
    Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
    Link: Latency L0s <128ns, L1 <64us
    Link: ASPM L0s Enabled RCB 64 bytes CommClk+ ExtSynch-
    Link: Speed 2.5Gb/s, Width x1
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 07-39-03-ff-ff-5c-21-00

```

My access point is a D-Link DIR-655. My ISP is Time-Warner cable.

My workstation is an EmperorLinux Raven Tablet (Lenovo Thinkpad X61 Tablet) running Ubuntu Hardy (v8.04.3 LTS) with all updates appropriate for the LTS distribution. The workstation runs wired networking without trouble through this same access point.
The workstation dual-boots with Windows(tm) XP/Pro Tablet PC Edition and runs type-N networking without any troubles so this is not a hardware issue.

Sorry for the venting, but I'm pretty frustrated.
~~~ 0;-/ Dan

---

