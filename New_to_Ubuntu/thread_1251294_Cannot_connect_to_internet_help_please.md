---
title: "Cannot connect to internet help please"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by amarumayo on 2009-08-27
Hi all,  I just intalled ubuntu 9.04 on my compaq presario v5015.  I cannot connect to the internet and no wireless connections are shown on the list.  Help I don't know what to do.  I am trying to leave Windows but without internet I cannot continue.

Thanks

---

### Post by Liolikas on 2009-08-27
Post otput of **lspci** here.

---

### Post by amarumayo on 2009-08-27
Hi,

  	 	 	 	 	 	  octavia@octavia-laptop:~$ sudo lspci -v 
 00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: bus master, 66MHz, medium devsel, latency 64  
 	Kernel modules: ati-agp  
 

 00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge  
 	Flags: bus master, 66MHz, medium devsel, latency 64  
 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64  
 	I/O behind bridge: 00009000-00009fff  
 	Memory behind bridge: c0100000-c01fffff  
 	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff  
 	Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+  
 	Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 30ae  
 	Kernel modules: shpchp  
 

 00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0  
 	Capabilities: [50] Power Management version 3  
 	Capabilities: [58] Express Root Port (Slot-), MSI 00  
 	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Capabilities: [b0] Subsystem: ATI Technologies Inc Device 0050  
 	Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+  
 	Capabilities: [100] Advanced Error Reporting <?>  
 	Kernel driver in use: pcieport-driver  
 	Kernel modules: shpchp  
 

 00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)  
 	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller  
 	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19  
 	Memory at c0000000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: ohci_hcd  
 

 00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (prog-if 10)  
 	Subsystem: ATI Technologies Inc IXP SB400 USB Host Controller  
 	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19  
 	Memory at c0001000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: ohci_hcd  
 

 00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (prog-if 20)  
 	Subsystem: ATI Technologies Inc IXP SB400 USB2 Host Controller  
 	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19  
 	Memory at c0002000 (32-bit, non-prefetchable) [size=4K]  
 	Capabilities: [dc] Power Management version 2  
 	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: ehci_hcd  
 

 00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: 66MHz, medium devsel  
 	I/O ports at 8400 [size=16]  
 	Memory at c0003000 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+  
 	Kernel driver in use: piix4_smbus  
 	Kernel modules: i2c-piix4  
 

 00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16  
 	I/O ports at 01f0 [size=8]  
 	I/O ports at 03f4 [size=1]  
 	I/O ports at 0170 [size=8]  
 	I/O ports at 0374 [size=1]  
 	I/O ports at 8410 [size=16]  
 	Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: pata_atiixp  
 

 00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge  
 	Flags: bus master, 66MHz, medium devsel, latency 0  
 

 00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (prog-if 01)  
 	Flags: bus master, 66MHz, medium devsel, latency 64  
 	Bus: primary=00, secondary=06, subordinate=07, sec-latency=64  
 	I/O behind bridge: 0000a000-0000afff  
 	Memory behind bridge: c0200000-c02fffff  
 

 00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17  
 	Memory at c0003400 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: ATI IXP AC97 controller  
 	Kernel modules: snd-atiixp  
 

 00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17  
 	Memory at c0003800 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-  
 	Kernel driver in use: ATI IXP MC97 controller  
 	Kernel modules: snd-atiixp-modem  
 

 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
 	Flags: fast devsel  
 	Capabilities: [80] HyperTransport: Host or Secondary Interface  
 

 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map  
 	Flags: fast devsel  
 

 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller  
 	Flags: fast devsel  
 

 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control  
 	Flags: fast devsel  
 	Kernel driver in use: k8temp  
 	Kernel modules: k8temp  
 

 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)  
 	Subsystem: Hewlett-Packard Company Device 30ae  
 	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17  
 	Memory at c8000000 (32-bit, prefetchable) [size=128M]  
 	I/O ports at 9000 [size=256]  
 	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]  
 	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]  
 	Capabilities: [50] Power Management version 2  
 	Kernel modules: radeonfb  
 

 06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
 	Subsystem: Hewlett-Packard Company Device 1355  
 	Flags: bus master, fast devsel, latency 64, IRQ 21  
 	Memory at c0200000 (32-bit, non-prefetchable) [size=8K]  
 	Kernel driver in use: b43-pci-bridge  
 	Kernel modules: ssb  
 

 06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  
 	Subsystem: Hewlett-Packard Company Device 30a4  
 	Flags: bus master, medium devsel, latency 128, IRQ 22  
 	I/O ports at a000 [size=256]  
 	Memory at c0202000 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: [50] Power Management version 2  
 	Kernel driver in use: 8139too  
 	Kernel modules: 8139too, 8139cp  
 

 octavia@octavia-laptop:~$

---

### Post by zerhacke on 2009-08-27
Please see [THIS THREAD.]("http://ubuntuforums.org/showthread.php?t=1251170")

---

### Post by nimblfingrs on 2009-08-27
Hi,

I also cannot connect via wifi to the internet.  My wireless adapter is the same as amarumayo, the broad comm BCM4318.  I think I read elsewhere that broadcom adapters couldbe problematic.

Are there any specific instructions for broadcom owners?

THX

---

### Post by mvalviar on 2009-08-27
I'm no expert. But try looking under System>Hardware Drivers.

---

### Post by amarumayo on 2009-08-27
I followed the other thread mentioned above and I manually downlaoded nsidwrapper-common, ndisgtk_0.8.4-1_i386.deb, and ndiswrapper-utils.  I am trying to install them manually but I don't know how.  Can somebody please help.

---

### Post by Iowan on 2009-08-27
Haven't read it, but hope [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") help page might be of use.

---

### Post by nimblfingrs on 2009-08-28
Hi.

I found a method that worked for me.   It's in another post here.  Cut 'n pastedhere:

                                                                       [IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]             April 23rd, 2009                                                                       #[**2**]("http://ubuntuforums.org/showpost.php?p=7129618&postcount=2")                                                                                  [Andreasen1970]("http://ubuntuforums.org/member.php?u=817488")                                               
              First Cup of Ubuntu
             [IMG]http://ubuntuforums.org/images/rank_1.png[/IMG]
                                                           
                Join Date: Apr 2009
                                                             Beans: 1
                                                                                                        
             
                                                                                  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                 **Re: Acer Aspire 5020 BCM4318**             
                                                                I have just installed Ubuntu 9.04 on my Acer Aspire 5020.  
 Everything works the first time besides  my Wlan.  
 But it was very easy to get it to work.  

 I just clicked "System> Administration> Hardware drivers"  
 "Broadcom B43 wireless driver" was in the list and only needed to be activated.  

 Now everything works.

Nice:razz:

Kim A.
This worked for me as well, tho it took 2 shots... Not sure why not on 1st try...
Paul B

                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                             [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7129618")                                                                                         [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7129618")

---

### Post by lkraemer on 2009-08-28
Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use cat /etc/modprobe.d/blacklist.conf
iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

(You are looking for any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the
Hardware Drivers with a LAN connection there should have been folders 
created and files inserted for the Restricted Drivers to work.)

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.

Once you have the Manuf & Hardware info, use Search or Google for
"HOWTO: & 4318" or whatever your Broadcom model is to find a good guide.

Here is a link for you to read.  Post #3

It will be your decision on what to use.

For #2 above:
If you just need the Broadcom firmware for b43xx it can be found on
the internet. Are you using b43, b43xx, or ndiswrapper?

Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

#3 doesn't appear to be supported by 9.04 according to searches of the forum.

I just stuck with the windows drivers.

lkraemer

---

