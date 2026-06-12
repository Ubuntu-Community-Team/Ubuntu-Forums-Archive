---
title: "detect modem on /dev/modem port with wvdialconf"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by ale_login on 2007-06-01
Hi!
I'm a newbie and I have a problem configuring a PCI modem (Intel 536ep) with wvdialconf on Linux Ubuntu 7.04.
_Basically, the modem's port is /dev/536ep0 and using udev I created a symlink to /dev/modem. It works fine under "Network Connection" but not with wvdialconf, which just looks for /dev/ttyS* ports._

**How can I make wvdialconf look for /dev/modem port??**

Here are some more details:
Wvdialconf output:
[I]Scanning your serial ports for a modem.
WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3  
Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?[/I]

Modem location:
[I]...@...:~$ ls -l /dev/536ep0
crw-rw---- 1 root dialout 240, 1 2007-05-31 19:05 /dev/536ep0
...@...:~$ ls -l /dev/modem
lrwxrwxrwx 1 root root 6 2007-05-31 19:05 /dev/modem -> 536ep0[/I]

OS: Linux UBUNTU 7.04 freshly installed.
       Wvdial version: 1.56-1.1ubuntu2

Modem (scanmodem output):
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 01:0b.0    8086:1040    8086:1000    Communication controller: Intel Corporation 536EP Data Fax Modem

 Modem interrupt assignment and sharing:
 10:          0    XT-PIC-XT        uhci_hcd:usb2

System: Intel Celeron 700 on Intel D815EEA motherboard (video & audio integrated), 256 Mb RAM, Intel PCI modem 536EP. That's all!

Modem drivers: I installed the drivers following instructions at [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto).
Then I created a rule (/etc/udev/rules.d/10-local.rules) to link /dev/536ep0 to /dev/modem.


THANKS!!!!
cheers

---

### Post by Sepero on 2007-06-12
It'll never detect you modem. You have to edit the configuration file with an editor.
```

[Dialer Defaults]
#Modem = /dev/modem
Modem = /dev/536ep0
Baud = 115200
Init = ATZ
New PPPD = yes
Stupid Mode = 1
Auto Reconnect = off
#Carrier Check = no
Dial Attempts = 1

# MODIFY THE FOLLOWING 3 SECTIONS FOR YOUR CONNECTION
Phone = 1234567
Username = ExampleName
Password = ExamplePassword

```
Copy this script to the file /etc/wvdial.conf. Replace the bottom three sections with your info. wvdial should work fine after that.

If you want to customize /etc/wvdial.conf more, have a look at the manpage:
man wvdial.conf

---

