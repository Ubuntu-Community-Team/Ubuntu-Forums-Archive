---
title: "Modem issues w another ubuntu newbie"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by hd79 on 2007-08-30
Hi All:
I know there are numerous issues with getting a dial-up modem to work with ubuntu, but it seems like I should be fairly close to having this working, but its going to take a little more expertise than what I possess. 

First, I installed ubuntu 7.0.4 ( Feisty) on my computer, running a 2.04 ghz AMD processor with 1 gig of ram. I also purchased a US Robotics internal modem, a USR5660A model.

I found a post that someone very helpfully included detailed instructions, but it seems I am not getting any response from the first part. the person who posted this set of instructions said to first try typing in wvdialconf on the terminal.

When I type in wvdialconf this is what I get:
Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

So, I am not getting the modem to be recognized at any of the default ttyS serial ports.

When I type in the next command, lspci -v, I get this:

00:09.0 Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)
        Subsystem: U.S. Robotics Unknown device 010a
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at bc00 [size=8]
        Capabilities: [40] Power Management version 2

so, from this command, it seems that the modem is being found in the system, but I am not certain what the 00:09.0 means----I know that it is found on the PCI serial bus 0, but does this mean it should be ttyS9?

I tried to use the setserial command for ttyS9, but I received an error message that said no such file or directory:

z@paz-desktop:~$ sudo setserial /dev/ttyS9 uart 16550A port 0xbc00 irq 10 baud_base 115200 spd_vhi skip_test
Password:
/dev/ttyS9: No such file or directory


I also ran the Scanmodem tool, and this is the output I received from that:

Ubuntu 7.04 
 on System with processor: i686
 currently under kernel:   2.6.20-15-generic
 assembled with compiler:  4.1.2
 with current System compiler GCC=4.1.2
    /usr/bin/gcc -> gcc-4.1

Checking for kernel-headers needed for compiling.

 A /dev/modem symbolic link is not set.

Modem candidates are at PCI_buses:  00:09.0
    
Providing detail for device at PCI_bus 00:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 16ec:2f00   Communication controller: U.S. Robotics USR5660A (USR265660A, USR5660A-BP) 56K PCI Faxmodem (rev 01)
  SubSystem 16ec:010a   U.S. Robotics Unknown device 010a
00:09.0 0780: 16ec:2f00 (rev 01)
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at febe0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]

Sorry for the length of this. I did not know how much detail to provide. It seems that the modem is being recognized as being  a part of  my system, but is not being recognized fully or enough for me to get a connection going.

I am at a loss as to what to do next or how to proceed? I assume I need to use some other form or syntax of the setserial command?

any help you may be able to provide will be much appreicated.

thanks,
hd79

---

