---
title: "Verizon PCMCIA card PC5750- Only root can use"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by DLinn on 2007-08-02
Hi All-

(writing as user)
So far I am underwhelmed w/ my Verizon PC5750 PCMCIA card.

Here is my setup:
- MOBO: Nforce 570 SLIT-A w/ Intel(R) Celeron(R) CPU 2.66GHz.
- VIDEO: Nvidia E-GEforce 7100 GS
- Verizon PCMCIA card (vendor-0x106c product=3702) plugs into
Addonics CardBus/PCMCIA controller card (vendor=0x104c product=0xac55) via 
PCI slot.

From Hardware Info:
MPC51 PCI Bridge
PCI1520 PC card Cardbus Controller
USB
OHCI Host Controller
USB Raw Device Access
PANTECH USB MODEM
USB Communications Interface
Serial Port
USB Data Interface
USB Vendor Specific Interface
USB Raw Device Access
USB Interface
USB
OHCI Host Controller
USB Hub Interface
USB Raw Device Access
PCI1520 PC card Cardbus Controller

I then followed installation instructions from [http://Linux.com/articles/52729](http://Linux.com/articles/52729).

All seemed right with the world until I began to use my machine as I usually do.

***That's when I found that I could not use the card as a regular user only as root!***

(continuing as user)

MY ACTIVITY: PCMCIA card unplugged. Cold boot log-in as user. Plug in card. Use terminal for wvdial.
TERMINAL OUTPUT:
dlinn@Desktop:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Aug  2 13:06:06 2007
--> Pid of pppd: 5766
--> Disconnecting at Thu Aug  2 13:06:06 2007
--> The PPP daemon has died: pppd options error (exit code = 2)
(My comment) EXIT STATUS 2 An error was detected in processing the options
             given, such as two mutually exclusive options being used.
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

MY ACTIVITY: Unplug card. Warm reboot. Log in as user. Plug in card. Use terminal for wvdial.
TERMINAL OUTPUT:
same as above.
***********************************************

My files- file info
ls -l /dev/ttyACM0
crw-rw---- 1 root dialout 166, 0 2007-08-02 13:35 /dev/ttyACM0
ls -l /etc/wvdial.conf
-rw-r--r-- 1 dlinn dialout 373 2007-08-02 13:45 /etc/wvdial.conf
ls -l /etc/ppp/chap-secrets
-rw-rw-rw- 1 dlinn dialout 275 2007-08-02 13:57 /etc/ppp/chap-secrets
ls -l /etc/ppp/pap-secrets
-rw-rw-rw- 1 dlinn dialout 1833 2007-08-02 13:55 /etc/ppp/pap-secrets

My files- file content
- - - - - - - - - - - - - - - - - - - - - - - 

# /etc/wvdial.conf

[Dialer Defaults] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 921600 
Init = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = #777 
Username = [email]xxxxxxxxxx@vzw3g.com[/email]
Password = vzw 
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 

[Dialer shh] 
Init3 = ATM0 

[Dialer pulse] 
Dial Command = ATDP
- - - - - - - - - - - - - - - - - - - - - - - 

# /etc/ppp/chap-secrets

"xxxxxxxxxx@vzw3g.com " * "vzw "  	#DLinn added
- - - - - - - - - - - - - - - - - - - - - - - 

# /etc/ppp/pap-secrets

# OUTBOUND connections
"xxxxxxxxxx@vzw3g.com " * "vzw "  	#DLinn added
- - - - - - - - - - - - - - - - - - - - - - - 
***********************************************

Some file outputs

lspci
06:06.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
06:06.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)

root@Desktop:~# lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation Unknown device [10de:0071] (rev a3)
00:00.1 RAM memory [0500]: nVidia Corporation Unknown device [10de:007f] (rev a1)
00:00.2 RAM memory [0500]: nVidia Corporation Unknown device [10de:0075] (rev a1)
00:00.3 RAM memory [0500]: nVidia Corporation Unknown device [10de:006f] (rev a1)
00:00.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:00b4] (rev a1)
00:01.0 RAM memory [0500]: nVidia Corporation Unknown device [10de:0076] (rev a1)
00:01.1 RAM memory [0500]: nVidia Corporation Unknown device [10de:0078] (rev a1)
00:01.2 RAM memory [0500]: nVidia Corporation Unknown device [10de:0079] (rev a1)
00:01.3 RAM memory [0500]: nVidia Corporation Unknown device [10de:007a] (rev a1)
00:01.4 RAM memory [0500]: nVidia Corporation Unknown device [10de:007b] (rev a1)
00:01.5 RAM memory [0500]: nVidia Corporation Unknown device [10de:007c] (rev a1)
00:01.6 RAM memory [0500]: nVidia Corporation Unknown device [10de:007d] (rev a1)
00:02.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:007e] (rev a2)
00:04.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:007e] (rev a2)
00:05.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:007e] (rev a2)
00:06.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:007e] (rev a2)
00:07.0 PCI bridge [0604]: nVidia Corporation Unknown device [10de:007e] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:016a] (rev a1)
06:06.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
06:06.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
06:07.0 Parallel controller [0701]: Lava Computer mfg Inc Lava Parallel [1407:8000]
07:00.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
07:00.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)

lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 106c:3702 Curitel Communications, Inc. (my PCMCIA card)
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04f9:000d Brother Industries, Ltd HL-1440 Laser Printer
Bus 001 Device 001: ID 0000:0000  
***********************************************
***********************************************
Now signed on as root

root@Desktop:~# groups root
root : root adm dialout fax cdrom floppy tape audio dip plugdev scanner admin fuse

root@Desktop:~# groups dlinn
dlinn : dlinn adm dialout fax cdrom floppy tape audio dip video plugdev scanner netdev lpadmin powerdev admin fuse
- - - - - - - - - - - - - - - - - - - - - - - 

MY ACTIVITY: PCMCIA card unplugged. Cold boot log-in as root . Plug in card. Use terminal for wvdial.
TERMINAL OUTPUT:
root@Desktop:~# wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Aug  2 14:34:48 2007
--> Pid of pppd: 5752
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> Using interface ppp0
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> pppd: &#65533;
--> [06][08]
--> [06][08]
...
--> local  IP address 75.218.48.42
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> remote IP address 66.174.161.6
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> primary   DNS address 66.174.95.44
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> secondary DNS address 66.174.92.14
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> pppd: &#65533;
--> [06][08]
--> [06][08]
--> Script /etc/ppp/ip-up run successful
--> Default route Ok.
--> Nameserver (DNS) Ok.
--> Connected... Press Ctrl-C to disconnect
--> pppd: &#65533;
--> [06][08]
--> [06][08]
- - - - - - - - - - - - - - - - - - - - - - - 

I'm all set and ready to go.

So what's the difference, why root but not user?

The world waits...

---

