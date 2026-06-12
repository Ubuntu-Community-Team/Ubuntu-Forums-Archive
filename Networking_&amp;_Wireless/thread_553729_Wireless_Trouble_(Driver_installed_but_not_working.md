---
title: "Wireless Trouble (Driver installed but not working)"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Themodem on 2007-09-18
Hey all, ive got a slight problem getting my wireless online. I have a Medion MD96254 and i have no idea what wireless card it had in it. i have downloaded the latest drivers from the net and also tried the ones that came on the driver cd and used ndiswrapper.

The only ones that i got a response out of were the most recent downloaded ones

[COLOR="Red"]athrusbext.cat   athrusb.sys      athrxusbext.cat  athrxusb.sys     netathrusb.inf   netathrxusb.inf[/COLOR]

i ran the command
[COLOR="Red"]themodem@smooth-laptop:~$ ndiswrapper -i Driver/netathrusb.inf [/COLOR]
and the output was
[COLOR="Red"]installing netathrusb ...
themodem@smooth-laptop:~$ ndiswrapper -l
netathrusb : driver installed
        device (0ACE:1215) present (alternate driver: zd1211rw)[/COLOR]

so i then ran
[COLOR="Red"]themodem@smooth-laptop:~$ sudo depmod -a
themodem@smooth-laptop:~$ sudo modprobe ndiswrapper
themodem@smooth-laptop:~$ tail /var/log/messages[/COLOR]

and the output from tail was

[COLOR="Red"]Sep 18 10:43:02 smooth-laptop kernel: [  125.568000] SCSI device sdb: 503808 512-byte hdwr sectors (258 MB)
Sep 18 10:43:02 smooth-laptop kernel: [  125.568000] sdb: Write Protect is off
Sep 18 10:43:02 smooth-laptop kernel: [  125.568000]  sdb: sdb1
Sep 18 10:43:02 smooth-laptop kernel: [  125.568000] sd 2:0:0:0: Attached scsi removable disk sdb
Sep 18 10:43:02 smooth-laptop kernel: [  125.572000] sd 2:0:0:0: Attached scsi generic sg1 type 0
Sep 18 10:47:06 smooth-laptop syslogd 1.4.1#20ubuntu4: restart.
Sep 18 10:48:08 smooth-laptop kernel: [  431.968000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
Sep 18 10:48:08 smooth-laptop kernel: [  432.232000] usb 1-6: reset high speed USB device using ehci_hcd and address 2
Sep 18 10:48:09 smooth-laptop loadndisdriver: loadndisdriver: load_driver(359): couldn't load driver netathrusb 
Sep 18 10:48:09 smooth-laptop kernel: [  432.392000] usbcore: registered new interface driver ndiswrapper[/COLOR]


[COLOR="Red"]themodem@smooth-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.[/COLOR]

im pretty new to linux and im not sure what i did wrong, as far as i can tell the driver installed correctly.

Any ideas?

Thanks Lee

---

### Post by tturrisi on 2007-09-18
> I have a Medion MD96254 and i have no idea what wireless card it had in it. 
post results of these commands:

# lspci
# lsusb

---

### Post by Themodem on 2007-09-18
themodem@smooth-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
themodem@smooth-laptop:~$ 
themodem@smooth-laptop:~$ 
themodem@smooth-laptop:~$ 
themodem@smooth-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a16:2004 Trek Technology (S) PTE, Ltd 
Bus 001 Device 002: ID 0ace:1215 ZyDAS 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
themodem@smooth-laptop:~$

---

