---
title: "actiontec lucent modem connects but will not transfer data"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by ducttapeandzipties on 2008-11-01
I had an external USR modem that got hit by lightning so I picked up a used actiontec modem on ebay.  It was found by ubuntu and worked with wvdial, but even though it dials and connects, I can't browse, connect to gaim, or anything else.  It did randomly load one or two pages with the settings left over from the USR modem, but now it won't load anything at all.  It works with windows so I have to boot linux to tinker with the modem and boot windows to access the internet.  I am totally stumped.

here is my wvdial.conf with init strings reccomended by manufactuer:



[Dialer Defaults]
Init1 = ATZ
Init2 = at&fw2s109=2s38=1s37=14
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS2
ISDN = 0
Phone = 8042014335
Password = **************
Username = **************
Auto DNS = yes



wvdial output with this config:



--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: at&fw2s109=2s38=1s37=14
at&fw2s109=2s38=1s37=14
OK
--> Modem initialized.
--> Sending: ATDT8042014335
--> Waiting for carrier.
ATDT8042014335
CONNECT 21600 V42bis
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas5.rch1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: [login]
[email]**********@peoplepc.com[/email]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 4.152.222.142
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Sat Sep 13 13:03:53 2008
--> Pid of pppd: 5792
--> Using interface ppp0
--> pppd: ï¿½[0c][06][08]( [06][08]
--> pppd: ï¿½[0c][06][08]( [06][08]
--> pppd: ï¿½[0c][06][08]( [06][08]
--> pppd: ï¿½[0c][06][08]( [06][08]
--> local  IP address 4.152.222.142
--> pppd: ï¿½[0c][06][08]( [06][08]
--> remote IP address 63.215.28.120
--> pppd: ï¿½[0c][06][08]( [06][08]
--> primary   DNS address 209.244.0.3
--> pppd: ï¿½[0c][06][08]( [06][08]
--> secondary DNS address 209.244.0.4
--> pppd: ï¿½[0c][06][08]( [06][08]



wvdial.conf with init strings from USR modem:
(this worked to load a page or two but that's it)


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS2
ISDN = 0
Phone = 8042014335
Password = **********
Username = [email]**********@peoplepc.com[/email]
Auto DNS = yes


wvdial output with USR config:


--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT8042014335
--> Waiting for carrier.
ATDT8042014335
CONNECT 36000 V42bis
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas5.rch1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: [login]
[email]**********@peoplepc.com[/email]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 4.152.222.136
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Sat Sep 13 13:00:18 2008
--> Pid of pppd: 5592
--> Using interface ppp0
--> pppd: 0
--> [06][08]H [06][08]
--> pppd: 0
--> [06][08]H [06][08]
--> pppd: 0
--> [06][08]H [06][08]
--> pppd: 0
--> [06][08]H [06][08]
--> local  IP address 4.152.222.136
--> pppd: 0
--> [06][08]H [06][08]
--> remote IP address 63.215.28.120
--> pppd: 0
--> [06][08]H [06][08]
--> primary   DNS address 209.244.0.3
--> pppd: 0
--> [06][08]H [06][08]
--> secondary DNS address 209.244.0.4
--> pppd: 0
--> [06][08]H [06][08]



lspci -vv output:


00:0f.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
        Subsystem: Actiontec Electronics Inc Unknown device 0480
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (63000ns min, 3500ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at ef001000 (32-bit, non-prefetchable) [size=256]
        Region 1: I/O ports at 9c00 [size=256]
        Region 2: I/O ports at a000 [size=256]
        Region 3: I/O ports at a400 [size=8]
        Capabilities: [f8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-



setserial /dev/ttyS2 gives me:


/dev/ttyS2, UART: 16550A, Port: 0x9c00, IRQ: 10

---

### Post by ducttapeandzipties on 2008-11-04
Damn, no love for the modem users?  We aren't extinct yet!

---

### Post by ducttapeandzipties on 2008-11-10
Can anyone help me?  Is there anymore information I need to post?  Having to use win-doze is kiling me!

---

### Post by yepimrony on 2008-11-10
ever get this fixed? I'm having similar problems with a cellular phone tethered over usb. I have an ip and dns resolves fine... but no internet connection? tried adjusting routing tables with no luck..been looking all over the place and can't seem to find a solid solution. Everyone does a lot of guess work and eventually a command will solve their problem.

---

