---
title: "huawei e220 help please..."
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by sapmig on 2006-12-26
hello

I have tried to put this modem working in ubuntu by reading some tuturials and other stuff but i cannot do that, when i type in the console sudo ls -la /dev/ttyU* it dont find my modem when i plug my modem it dont create any /dev/ttyUSB0,USB1 or USB2

help me i dont no what do for make this work.


Sorry for the english, i am portuguese

---

### Post by daka on 2007-01-23
HOW TO Configure the Huawei 220 usb modem in Linux, (IN SPAIN - Vodafone)

(I don't know if these instructions work with other providers)
__________________________________________________________________

I tried to follow other Forum guidelines but they didn't work for me.  What did work was slightly less work, slightly less complicated so I thought I should put the "How To" in the forum also.



I use a Packard Bell EasyNote laptop with Kubuntu (Dapper) kernel 2.6.15-23-386 and Linux "Mint" (Bea)
(I have also configured this modem with these instructions in Ubuntu Dapper, Ubuntu Edgy, GNU Linex 2006, Linux Mint (Ubuntu based), Knoppix, and Mandriva.

(I read in a few places that the long cable doesn't work but this is NOT my experience... I use the long one with an extension of two metres and my connection then, (only then) has a strong and stable signal)

Create or edit the "wvdial.conf" file in /etc ... (see my wvdial.conf file below)

Disable pin by putting card in a phone and disabling (otherwise the nightmare is much worse..,.although it is possible... I eventually disabled the pin and this made me much happier.

Disable Wifi and Ethernet as these can interfere with Huawei.
Go to System Settings / Network Settings and disable Ethernet and Wireless.

Leave a blank cd in the cdrom (This can prevent the Huawei from being mis-identified as a cdrom or usb storage device)

Remove all usb storage devices

Start up with Huawei plugged in

IF the Huawei is identified initially as a CD "Connect_Box", right click it and "eject".  You MAY need to do this a few times to ensure that it is ejected (until the option to "eject" is no longer there



Open a terminal as root


modprobe usbserial vendor=0x12d1 product=0x1003
wait a few moments ( 5 seconds)

remove (unplug) the Huawei E220 and wait for maybe 2-3 seconds

re-insert huawei.. wait again 10 to 20 seconds before re-inserting
* (look at lights on Huawei and wait until the light changes from green to blue)


(OPTIONALLY, before trying to connect using wvdial you can enter:
ls -la /dev/ttyU* 
and you will probably see...   USB0  USB1  and USB2 .. 

then


wvdial hsdpa

You should be connected!
_________________________________________

Here is my wvdial.conf file:

/etc/wvdial.conf



[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","ac.vodafone.es";

_______________________________________________________



This is what my script looks like when I connect

Password:
root@kp-laptop:/home/daka# rmmod usb-storage
root@kp-laptop:/home/daka# modprobe usbserial vendor=0x12d1 product=0x1003
root@kp-laptop:/home/daka# ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2006-12-19 14:33 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2006-12-19 14:33 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2006-12-19 14:33 /dev/ttyUSB2
root@kp-laptop:/home/daka# wvdial hsdpa
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","ac.vodafone.es";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Dec 19 14:33:56 2006
--> Pid of pppd: 5550
--> Using interface ppp0
--> local  IP address 62.87.24.143
--> remote IP address 10.64.64.64
--> primary   DNS address 212.73.32.3
--> secondary DNS address 212.73.32.67
                                         
Good Luck... (I hope I haven't made any mistakes in this!!)

I know some people have dificulty configuring the modem in Ubuntu and I don't know why.  Maybe the "wvdial" program has to be recent

The distro that gives me the least problems is Linux Mint.(Bea)  It is Ubuntu Dapper with ALL the Multimedia codecs and other nice stuff!  I really like it!

Daka

---

### Post by mormor on 2008-03-04
[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19)

vodafones drivers works fine in norway

---

