---
title: "FATAL: Error inserting usbserial"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by ZALinuxDude on 2008-09-06
Hi all was wondering if any one could help me with this problem i'm getting...

I'm running xUbuntu 8.04 Hardy Heron and I'm trying to run the following commands (found in this forum)

 Re: Nokia PC Suite for Linux?
I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type

lsusb

now u will get the following output

owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones
Bus 001 Device 002: ID 046d:092f Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
owais@owais-desktop:~$


it is on my compter,ur will not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445

Now enter this command

wvdialconf create
u'll get a long output which will be like

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

sudo gedit /etc/wvdial.conf

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
Baud = ur max speed(460800 in my case)
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = username
Password = password
Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...

The problem is i keep getting to the part...:

sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

and it spits out a error message...:

FATAL: Error inserting usbserial (/lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko) : Operation not permitted

---

