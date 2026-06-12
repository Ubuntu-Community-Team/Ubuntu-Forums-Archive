---
title: "Problem in wireless connection"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by psundar on 2008-08-06
Hi,

I couldnt connect to my wireless. Only when I restart my windows and open xubuntu, I could connect. following are the output to the commands:
dmesg (Attached as a file)
lshw
lspci
lsusb

Output:

***_lshw_***
xubuntos@xubuntos-tinyos:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:61:bc:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 ip=192.168.230.128 latency=64 maxlatency=255 mingnt=6 multicast=yes
       resources: ioport:1400-147f irq:18

***_lspci_***
xubuntos@xubuntos-tinyos:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)

**_*lsusb*_**
xubuntos@xubuntos-tinyos:~$ lsusb
Bus 001 Device 001: ID 0000:0000  

Please help,
psundar

---

### Post by pytheas22 on 2008-08-06
So wireless doesn't work on Xubuntu, but if you boot into Windows and then restart back into Xubuntu, then it works?

If so, then I think what must be going on is that Windows is powering down your wireless card for some reason (is it internal or external?).  I don't see any wireless device mentioned in the output that you posted, and it should be there, unless Windows has powered it down and made it invisible to Xubuntu (Windows does stuff like that sometimes).

So please confirm that booting from Windows back into Linux makes the wireless work, and we can take it from there.

---

### Post by psundar on 2008-08-07
Yes. I restarted my windows; opened xubuntu and used it were able to connect to the internet. 
(note: but neither my iwlist scan nor iwconfig detects wireless extension.) 

Thanks,
psundar

---

### Post by pytheas22 on 2008-08-07
> Yes. I restarted my windows; opened xubuntu and used it were able to connect to the internet. 

Do you mean to the wireless Internet?  Just for clarity, please confirm: your wireless Internet works, but only sometimes.

When the wireless is working and connected, what is the output of:
```

lshw -C Network
iwlist scan
ifconfig
```

---

### Post by psundar on 2008-08-07
My wireless network works only sometimes. to be specific, to make it work I have to restart my windows then open xubuntu everytime I move to a new location(network). 
Now, the internet(with only wireless access) is working. The outputs are:

xubuntos@xubuntos-tinyos:~$ **_lshw -C Network**_
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 79c970 [PCnet32 LANCE]
       vendor: Advanced Micro Devices [AMD]
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth1
       version: 10
       serial: 00:0c:29:61:bc:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical logical
       configuration: broadcast=yes driver=pcnet32 driverversion=1.33 ip=192.168.230.128 latency=64 maxlatency=255 mingnt=6 multicast=yes
       resources: ioport:1400-147f irq:18
xubuntos@xubuntos-tinyos:~$ **_iwlist scan**_
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

xubuntos@xubuntos-tinyos:~$ **_ifconfig**_
eth1      Link encap:Ethernet  HWaddr 00:0C:29:61:BC:B6  
          inet addr:192.168.230.128  Bcast:192.168.230.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe61:bcb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67260110 (64.1 MiB)  TX bytes:1684064 (1.6 MiB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Thanks,
Psundar

---

### Post by pytheas22 on 2008-08-07
You appear to be connected on interface eth1, which is wired ethernet, according to lshw.  Are you sure that there is no wire plugged into your computer?  I don't see any wireless interfaces mentioned--even nonconfigured ones--so I'm not sure what's going on.  Unless the information about your hardware is being detected incorrectly, it doesn't appear that you have any wireless card in your computer at all.

---

### Post by psundar on 2008-08-08
There is no wired connection at all. Is it possible that xubuntu is wired by ethernet to the windows and connecting the internet?

---

### Post by pytheas22 on 2008-08-08
> There is no wired connection at all. Is it possible that xubuntu is wired by ethernet to the windows and connecting the internet?

I'm not sure what you mean.  Where is Windows in this equation?  Are you running Xubuntu in a virtual machine or something?  If so, then that changes everything...

Actually I just noticed that you probably are using a virtual machine, since your graphics card is listed as "VMware Inc [VMware SVGA II] PCI Display Adapter."  I don't have any experience with VMware so I'm not sure what could be going on, but probably the problem has to do with VMware, not Xubuntu.  In the output that you gave, you had an IP address, so your Internet connection should be working.

I think that VMware by default bridges a virtual ethernet connection between the host operating system, Windows, and the guest, Xubuntu.  Therefore you tell Xubuntu to connect using ethernet--you do not need to select any wireless network in Xubuntu.

If this doesn't clear up the problem, please let me know, but I think the issue is just understanding the virtualization stuff.  The bottom line is that you have an Internet connection in Xubuntu, right?

---

