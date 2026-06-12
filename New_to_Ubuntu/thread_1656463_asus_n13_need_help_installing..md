---
title: "asus n13 need help installing."
date: 2010-12-30
forum: New to Ubuntu
---

### Post by creepy steve on 2010-12-30
i just bought an asus n13 because of it's shiny box stating "linux support" I have ndiswrapper installed. it doesnt read the disk and i have no evidence of it being on my system. take a look see. 

 steve@steve-M925:~$ lsmod | grep -e rt2 -e rt3
steve@steve-M925:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
steve@steve-M925:~$ 

can anyone help a super newb install from the start?

---

### Post by cariboo on 2010-12-30
Here's something to do that will help us help you solve your problem, First plug in the device, then open an Applications->Accessories->Terminal and type:

```
dmesg | tail -n15
```

paste the output of the above command in your next post.  If you don't have internet acces on the computer, you can create a text file using the following command:

```
dmesg | tail -n15 > dmesg.txt
```

you can then transfer the text file to a system with a working internet connection.

---

### Post by creepy steve on 2010-12-30
steve@steve-M925:~$ dmesg | tail -n15
[ 2647.043651]  [<c046d437>] ? hub_port_connect_change+0x587/0x8f0
[ 2647.043656]  [<c046a6b3>] ? hub_port_status+0xb3/0x110
[ 2647.043661]  [<c046e710>] ? hub_events+0x2b0/0x4f0
[ 2647.043668]  [<c0165f7f>] ? finish_wait+0x4f/0x70
[ 2647.043672]  [<c046e98a>] ? hub_thread+0x3a/0x140
[ 2647.043677]  [<c0165e10>] ? autoremove_wake_function+0x0/0x50
[ 2647.043682]  [<c046e950>] ? hub_thread+0x0/0x140
[ 2647.043686]  [<c01659e4>] ? kthread+0x74/0x80
[ 2647.043691]  [<c0165970>] ? kthread+0x0/0x80
[ 2647.043697]  [<c010363e>] ? kernel_thread_helper+0x6/0x10
[ 2647.043699] Code:  Bad EIP value.
[ 2647.043703] EIP: [<000adacc>] 0xadacc SS:ESP 0068:f70f7694
[ 2647.043709] CR2: 00000000000adacc
[ 2647.043714] ---[ end trace ae80724d712cc246 ]---
[ 2680.855380] usbcore: deregistering interface driver ndiswrapper

---

### Post by creepy steve on 2011-01-02
after talking to someone here is where i am at now. 


[ 4026.529126] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 4026.529139] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 4026.529153] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 4026.529166] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 4026.529183] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 4026.529196] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 4026.529213] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 4026.529222] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[ 4026.529231] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[ 4026.529240] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 4026.529245] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netr28u'
[ 4026.530895] ndiswrapper (load_wrap_driver:108): couldn't load driver netr28u; check system log for messages from 'loadndisdriver'
[ 4026.530981] usbcore: registered new interface driver ndiswrapper
[ 4573.932676] eth0: link down
[ 4585.340798] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

and...
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 002 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

