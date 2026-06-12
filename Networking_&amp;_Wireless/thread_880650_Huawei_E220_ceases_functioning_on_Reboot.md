---
title: "Huawei E220 ceases functioning on Reboot"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by sqasl1! on 2008-08-05
Hi all

I'm bit a 'Nux n00b and have just recently (this weekend) installed Ubuntu 8.04.  I have Huawei E220 mobile broadband with provider three.co.uk (in the UK) and I've confirmed the following strange behaviour (when I say confirmed I mean I've installed Ubuntu 3 times in the past 2 days tyring to figure this out, and this happens on a fresh out-the-box install with no added software or updates).

1. When you install Ubuntu, plug the modem in and configure the wvdial.conf file, everything works.  You can unplug and replug the modem as many times are you want, everything is ok. The modem is picked up again soon after replugging and wvdial connects without problems.

2. If you then reboot Ubuntu LEAVING THE MODEM PLUGGED IN, something breaks.  The modem will work fine when you connect immediately after reboot.  However if you then unplug and replug it, wvdial is unable to see it.

This relates to the posts [http://ubuntuforums.org/showthread.php?p=5526904]("http://ubuntuforums.org/showthread.php?p=5526904")
and [http://ubuntuforums.org/showthread.php?t=823687&highlight=huawei+e220+problems]("http://ubuntuforums.org/showthread.php?t=823687&highlight=huawei+e220+problems")
 and others I've found on the web since I now have exactly the same problem as they do.

It seems as if something funny happens with detecting USB devices during the boot process.  Here is transcript from a Terminal after I had rebooted the pc with the modem plugged in.

```

jacques@jacques-desktop:~$ uname -r
2.6.24-19-generic

jacques@jacques-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 002 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 002 Device 002: ID 04e1:0201 Iiyama North America, Inc. Monitor Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 001: ID 0000:0000  

jacques@jacques-desktop:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB2  /dev/ttyUSB4  /dev/ttyUSB6  /dev/ttyUSB8
/dev/ttyUSB1  /dev/ttyUSB3  /dev/ttyUSB5  /dev/ttyUSB7

jacques@jacques-desktop:~$ sudo wvdial
[sudo] password for jacques: 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Aug  6 10:13:27 2008
--> Pid of pppd: 5925
--> Using interface ppp0
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> local  IP address 10.178.44.8
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> remote IP address 10.64.64.64
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> primary   DNS address 172.31.76.69
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> secondary DNS address 172.30.140.69
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> Connect time 0.1 minutes.
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> pppd: `ï¿½[06][08]ï¿½ï¿½[06][08]
--> Disconnecting at Wed Aug  6 10:13:36 2008


#Unplug the modem from USB port


jacques@jacques-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 002 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 002 Device 002: ID 04e1:0201 Iiyama North America, Inc. Monitor Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

jacques@jacques-desktop:~$ ls /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory


#Plug modem back into USB port


jacques@jacques-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 002 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 046d:c218 Logitech, Inc. Logitech RumblePad 2 USB
Bus 002 Device 002: ID 04e1:0201 Iiyama North America, Inc. Monitor Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 001 Device 001: ID 0000:0000  

jacques@jacques-desktop:~$ ls /dev/ttyU*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2

jacques@jacques-desktop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
jacques@jacques-desktop:~$ 

jacques@jacques-desktop:~$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
jacques@jacques-desktop:~$ 

```

As you can see, initially there are 9 USB devices labelled /dev/ttyUSBx, then upon unplug and replug there are only 3.  Also, immediately after the fresh install (when the modem was working fine) Ubuntu only detected the three devices /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2.

And on top of it all, I can now no longer connect to the internet at all, even if I reboot with the modem plugged in: something else seems to have happened and Ubuntu now only finds the devices /dev/ttyUSB0, /dev/ttyUSB1 and /dev/ttyUSB2 and not, like before, the devices /dev/ttyUSBx with x = 0, 1, ... 8


For completeness, here is my wvdial.conf file:
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Username = three
Password = three
Modem = /dev/ttyUSB0
Dial Command = ATDT
Baud = 9600

[Dialer three]
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
Init5 = AT+CGDCONT=1,"IP","3internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud = 460800

```

Any of you clever guys (and girls?) got any idea what might be going on?

Thanks

---

### Post by sqasl1! on 2008-08-08
I installed NetworkManager 0.7 and things seems to be a lot better now.  The modem appears to be detected correctly, regardless of whether it was plugged in during boot up.  I can even connect the three.co.uk network through the MobileBroadband tab.  To set that up, use the following options:

Number : *99#
Username: three
Password: three
APN: three.co.uk
Network:
Type: GSM
Band:
PIN:
PUK:

Under PPP, activate the following:
Use Authentication
Allow BSD Data Compression
Allow Deflate
Use TCP header compression

At least, this works for me.

---

### Post by TobyLL on 2008-09-30
I had a similar problem even after installing NetworkManager 0.7

/dev/ttyUSB2 to /dev/ttyUSB5 would appear, and would then disappear if the modem was unplugged and replugged.

I think this is caused by this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/241484](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/241484)

Adding the following line to /etc/modprobe.d/blacklist-modem solved the problem:
blacklist airprime

---

### Post by sqasl1! on 2008-10-01
Hi TobyLL

Thanks a lot for the info!  Actually I've had the same problems with NetworkManager 0.7 as I had with 0.6 - it worked immediately after the upgrade and then reverted to its old tricks.  I just didn't bother reporting it since no one seemed to be having similar problems.

I'll try blacklisting the airprime driver this evening and see if that works.  

By the way - what is the difference between the airprime and usbserial drivers?  I'm a bit confused ...

---

### Post by sqasl1! on 2008-10-05
Hi TobyLL

Yes, seems that has fixed it.  The modem works fine now.

Thanks a lot for the info - really appreciate it !!

---

### Post by brunolabs on 2008-10-05
Does NM 0.7 come with the latest updates or does it need to be manually installed?

What features does the new version have?

---

### Post by fallenstar on 2008-10-05
[I]
1. When you install Ubuntu, plug the modem in and configure the wvdial.conf file, everything works.  You can unplug and replug the modem as many times are you want, everything is ok. The modem is picked up again soon after replugging and wvdial connects without problems.

2. If you then reboot Ubuntu LEAVING THE MODEM PLUGGED IN, something breaks.  The modem will work fine when you connect immediately after reboot.  However if you then unplug and replug it, wvdial is unable to see it.
[/I]

Hey, I'm having a similar problem, reinstalled ubuntu studio last night because modem issues, just did wvdial.conf editing, worked grand, but today, it claimed there was no modem. Now wvdial can see it but won't connect.

Alt + F2 wvdial Defauts won't connect
I installed gnome-ppp, which hangs on "sending password" (left password box blank, tried sticking "Anything" in, same problem.
Blacklisted airprime, made no difference

Thanks :)

---

### Post by sqasl1! on 2008-10-06
> **brunolabs said:**
> Does NM 0.7 come with the latest updates or does it need to be manually installed?

What features does the new version have?

As far as I know, NM 0.7 has to be installed manually.  It is under (heavy) development with updates coming out about every second week.

It has several new GUI features (mainly new connectivity options such as VPN and WiFi), and I suspect some retooling under the hood.  Best to check out the website [http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/") 
for more info.

---

### Post by sqasl1! on 2008-10-06
> **fallenstar said:**
> [I]
1. When you install Ubuntu, plug the modem in and configure the wvdial.conf file, everything works.  You can unplug and replug the modem as many times are you want, everything is ok. The modem is picked up again soon after replugging and wvdial connects without problems.

2. If you then reboot Ubuntu LEAVING THE MODEM PLUGGED IN, something breaks.  The modem will work fine when you connect immediately after reboot.  However if you then unplug and replug it, wvdial is unable to see it.
[/I]

Hey, I'm having a similar problem, reinstalled ubuntu studio last night because modem issues, just did wvdial.conf editing, worked grand, but today, it claimed there was no modem. Now wvdial can see it but won't connect.

Alt + F2 wvdial Defauts won't connect
I installed gnome-ppp, which hangs on "sending password" (left password box blank, tried sticking "Anything" in, same problem.
Blacklisted airprime, made no difference

Thanks :)

That's really odd.  All I can suggest is installing NetworkManager 0.7 ([http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")) and then trying again.  This worked for me, although I admit that's not a very helpful comment :(.  I can't really think of anything else to try - I'm a bit new to the 'nux game myself...

---

