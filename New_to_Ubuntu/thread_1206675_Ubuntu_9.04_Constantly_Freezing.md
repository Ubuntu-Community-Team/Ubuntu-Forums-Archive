---
title: "Ubuntu 9.04 Constantly Freezing"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Booky on 2009-07-07
I just got this computer a few days ago, and the system constantly freezes (every 30 sec- 20 min). The longer I use it, the oftener it freezes. Ctrl-Alt-Backspace doesn't do anything, so I have to manually restart it. I put Vista on it for a bit, and there was no freezing there. 

The computer's pieced together from parts, the "major" ones are

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813123005](http://www.newegg.com/Product/Product.aspx?Item=N82E16813123005) - Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103747](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103747) - Processor
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16820145590](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145590) - Memory
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371005](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371005) - Power Supply
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130097](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130097) - Graphics Card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075) - Hard Drive

Also, I don't have the LiveCD, so I can't do anything that involves that.

I'd appreciate any help, thanks in advance.

---

### Post by x3roconf on 2009-07-07
Have you tested memory with memtest86 or similiar utility? Check for overheating too. It's also possible that your motherboard is broken.

---

### Post by LewRockwell on 2009-07-07
> **Booky said:**
> I just got this computer a few days ago, and the system constantly freezes (every 30 sec- 20 min). The longer I use it, the oftener it freezes. Ctrl-Alt-Backspace doesn't do anything, so I have to manually restart it. I put Vista on it for a bit, and there was no freezing there. 

The computer's pieced together from parts, the "major" ones are

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813123005](http://www.newegg.com/Product/Product.aspx?Item=N82E16813123005) - Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103747](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103747) - Processor
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16820145590](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145590) - Memory
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817371005](http://www.newegg.com/Product/Product.aspx?Item=N82E16817371005) - Power Supply
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130097](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130097) - Graphics Card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136075) - Hard Drive

Also, I don't have the LiveCD, so I can't do anything that involves that.

I'd appreciate any help, thanks in advance.

was there something wrong with your first thread on this problem?

[http://ubuntuforums.org/showthread.php?t=1204903](http://ubuntuforums.org/showthread.php?t=1204903)

.

---

### Post by philinux on 2009-07-07
If it freezes again use this.

Alt and Sysrq(printscreen key) hold both down and press k.

This will take you back to the login screen.

When your system is running use the command 

```
top
```

in a terminal to see if anything hogging resources.

---

### Post by Booky on 2009-07-07
x3roconf: Yes, I think someone ran a test on everything for six hours, seemed all right. Temperature's fine, too.

philinux:

  	 	 	 	 	 	  myname@myname-desktop:~$ top 
  
 top - 18:25:29 up 4 min,  2 users,  load average: 0.35, 0.31, 0.14 
 Tasks: 133 total,   1 running, 132 sleeping,   0 stopped,   0 zombie 
 Cpu(s):  4.3%us,  1.8%sy,  0.0%ni, 93.7%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st 
 Mem:   3097176k total,   567328k used,  2529848k free,    19152k buffers 
 Swap:  6385796k total,        0k used,  6385796k free,   232808k cached 
  
   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
  2736 root      20   0  102m  38m  10m S    6  1.3   0:09.79 Xorg                
  3433 myname   20   0  214m  96m  25m S    4  3.2   0:20.76 firefox             
  3300 myname   20   0 37160  19m  13m S    1  0.7   0:01.41 gnome-panel         
  3401 myname   20   0 20036  10m 7504 S    1  0.3   0:00.49 gtk-window-deco     
  3299 myname   20   0 70916  38m  12m S    1  1.3   0:02.61 compiz.real         
  3506 myname   20   0 33784  14m 9548 S    0  0.5   0:00.31 gnome-terminal      
       1 root      20   0  3084 1884  564 S    0  0.1   0:01.22 init                
       2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd            
       3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0         
        4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0         
       5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0          
       6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1         
       7 root      15  -5     0    0    0 S    0  0.0   0:00.03 ksoftirqd/1         
       8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1          
       9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0    
 
Does that look normal?


Also, I was told to download monitoring facilities- any suggestions?

---

### Post by Booky on 2009-07-07
And plilinux- I tried that command just now when it froze, nothing happened.

---

### Post by WinterWeaver on 2009-07-07
I've noticed freezes because of Compiz + certain gtk themes O.o.

Try turning off your desktop effects, and see if it still freezes.

---

### Post by nhasian on 2009-07-07
you need to get yourself a liveCD.  that way you can boot off of it and run it for several hours to see if it also freezes up or only your installed version?

do you have gnome sensors applet installed so you can see the temperatures of your CPU, CPU, Hard Disk, etc?

are you using the open source or restricted nvidia drivers?  also try disabling compiz to see if that resolves your problem.

---

### Post by Booky on 2009-07-07
My CPU's doing 32 degrees celcius, 65 is the max. My hard drive's doing 75 fahrenheit, should be anywhere between 41 and 131.


I don't think I have any desktop effects or compiz or anything installed. As to the other questions, I have no clue, sent an email to the person who assembled the computer.

---

### Post by sdbrogan on 2009-07-08
It might be the problem in this thread :
[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)
You could try an Intrepid live CD & see if you get the same problem there

---

### Post by WinterWeaver on 2009-07-08
> **Booky said:**
> x3roconf: Yes, I think someone ran a test on everything for six hours, seemed all right. Temperature's fine, too.


  3299 myname   20   0 70916  38m  12m S    1  1.3   0:02.61 compiz.real         
  


looks to me like you do have compiz running.
Right-Click your desktop >> Change Desktop Background >> Visual Effects Tab >> None

---

### Post by ukripper on 2009-07-08
Can you post output of the following commands:

```
lspci -v
```

```
lsusb -v
```

```
cat /var/log/messages | grep error
```

```
cat /proc/interrupts
```

---

### Post by Booky on 2009-07-08
ukripper:
> 
 00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0
    Kernel modules: ck804xrom

00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at fc00 [size=64]
    I/O ports at f800 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f695:1026
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    I/O ports at 09e0 [size=8]
    I/O ports at 0be0 [size=4]
    I/O ports at 0960 [size=8]
    I/O ports at 0b60 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at c800 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at bc00 [size=4]
    I/O ports at b800 [size=16]
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fde00000-fdefffff
    Capabilities: <access denied>

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2297
    Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b400 [size=8]
    Memory at fe029000 (32-bit, non-prefetchable) [size=256]
    Memory at fe028000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
    Subsystem: EPoX Computer Co., Ltd. Device 1026
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2298
    Memory at fe027000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at b000 [size=8]
    Memory at fe026000 (32-bit, non-prefetchable) [size=256]
    Memory at fe025000 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00007000-00008fff
    Memory behind bridge: fda00000-fdafffff
    Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: fd800000-fd8fffff
    Prefetchable memory behind bridge: 00000000fd700000-00000000fd7fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: fd600000-fd6fffff
    Prefetchable memory behind bridge: 00000000fd500000-00000000fd5fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: fa000000-fcffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
    Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fdafe000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at fd900000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 8c00 [size=8]
    I/O ports at 8800 [size=4]
    I/O ports at 8400 [size=8]
    I/O ports at 8000 [size=4]
    I/O ports at 7c00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron

06:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
    Subsystem: eVga.com. Corp. Device c428
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

**myname@myname-desktop:~$ lsusb -v**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x045e Microsoft Corp.
  idProduct          0x0040 Wheel Mouse Optical
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                3 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      72
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 002 Device 002: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05af Jing-Mold Enterprise Co., Ltd
  idProduct          0x0802 
  bcdDevice            1.30
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      62
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      99
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
[B]myname@myname-desktop:~$ cat /var/log/messages | grep error
myname@myname-desktop:~$ cat /proc/interrupts[/B]
           CPU0       CPU1       
  0:        110          0   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  4:          0          2   IO-APIC-edge    
  6:          0          4   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          0          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 14:         15       2420   IO-APIC-edge      pata_amd
 15:          0          0   IO-APIC-edge      pata_amd
 16:         68      14191   IO-APIC-fasteoi   ahci, pata_jmicron, nvidia
 20:         25       3101   IO-APIC-fasteoi   ehci_hcd:usb1, HDA Intel
 21:          0          0   IO-APIC-fasteoi   sata_nv
 22:          0          0   IO-APIC-fasteoi   sata_nv
 23:        111      53271   IO-APIC-fasteoi   sata_nv, ohci_hcd:usb2
2297:        115      25028   PCI-MSI-edge      eth0
2298:        107      22075   PCI-MSI-edge      eth1
NMI:          0          0   Non-maskable interrupts
LOC:      24707      22398   Local timer interrupts
RES:      13664       9063   Rescheduling interrupts
CAL:       4307       3996   Function call interrupts
TLB:        685        354   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0


---

### Post by Booky on 2009-07-08
WinterWeaver: I did what you said, it froze anyway.
Nhasian: No gnome sensors applet, restricted drivers. How do I get a LiveCD?
Sdbrogan: So what did the problem in that thread turn out to be?

Thanks for all the help so far!

---

### Post by Booky on 2009-07-08
And one more thing: at startup, the computer always gives this error:

"AP-BIOS bug: 8254 timer not connected to IO-APIC"

I'm not sure whether that's at all important, though.

---

### Post by nhasian on 2009-07-10
you can either update the bios of your motherboard or you can disable APIC in your bios.

> **Booky said:**
> And one more thing: at startup, the computer always gives this error:

"AP-BIOS bug: 8254 timer not connected to IO-APIC"

as for getting a liveCD, follow these instructions:

[http://www.psychocats.net/ubuntu/getting](http://www.psychocats.net/ubuntu/getting)

---

