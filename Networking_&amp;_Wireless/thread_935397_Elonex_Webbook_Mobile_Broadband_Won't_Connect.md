---
title: "Elonex Webbook Mobile Broadband Won't Connect"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by webbooknovice on 2008-10-01
The mobile broadband programme was working fine until tonight and for some reason now it wont connect. Have tried T-Mobile and 3 USB dongles.  Any suggestions as to how I fix this. Thanks in advance. Andy

---

### Post by pytheas22 on 2008-10-02
Which mobile-broadband program were you using?  Also, please plug your modem in and post the output of these commands:
```

lshw -C Network
lsusb
```

---

### Post by webbooknovice on 2008-10-02
> **pytheas22 said:**
> Which mobile-broadband program were you using?  Also, please plug your modem in and post the output of these commands:
```

lshw -C Network
lsusb
```
Thanks for the quick response.  Mobile Broadband program is wader-gtk

Command outputs as below:-

lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth5
       version: 05
       serial: 00:16:6f:cc:d9:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth4
       version: 10
       serial: 00:e0:4e:77:11:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

_______________________________________________________________________________________________________________________

 lsusb
Bus 004 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 004 Device 002: ID 0bda:0156 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

_____________________________________________________________________________

When I plug the modem in it is showing '3 Registered UMTS' but when I click on the connect button it shows 'connecting' and then just reverts to the connect screen again.

Many thanks for your help in trying to resolve this.

Andy

---

### Post by pytheas22 on 2008-10-02
Please try running these commands, then connecting:
```

sudo rmmod airprime
sudo rmmod usbserial
sudo modprobe usbserial
```

Can you connect now?

If not, please post the output of:

```

cat /etc/wvdial.conf
sudo wvdial
```

---

### Post by webbooknovice on 2008-10-03
> **pytheas22 said:**
> Please try running these commands, then connecting:
```

sudo rmmod airprime
sudo rmmod usbserial
sudo modprobe usbserial
```

Can you connect now?

If not, please post the output of:

```

cat /etc/wvdial.conf
sudo wvdial
```
Still not working, printouts as follows:-

andy@ubuntu:~$ sudo rmmod airprime
andy@ubuntu:~$ 
andy@ubuntu:~$ sudo rmmod airprime
ERROR: Module airprime does not exist in /proc/modules
andy@ubuntu:~$ sudo rmmod usbserial
ERROR: Module usbserial is in use by option
andy@ubuntu:~$ sudo modprobe usbserial
andy@ubuntu:~$ sudo rmmod airprime
ERROR: Module airprime does not exist in /proc/modules
andy@ubuntu:~$ sudo rmmod usbserial
ERROR: Module usbserial is in use by option
andy@ubuntu:~$ sudo modprobe usbserial
______________________________________________________________________________________________--
andy@ubuntu:~$ cat /etc/wvdial.conf
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
andy@ubuntu:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
andy@ubuntu:~$

---

### Post by pytheas22 on 2008-10-03
It seems like the computer isn't recognizing your modem and/or it's not configured properly.  I'm not sure why a regression would have occurred (since you say it worked before), but please try following [these instructions]("http://ph.ubuntuforums.com/showthread.php?t=595064") to get the modem installed properly.  Please let me know how it goes.

Also, do you remember which instructions you followed when you first installed the device?

---

### Post by webbooknovice on 2008-10-03
> **pytheas22 said:**
> It seems like the computer isn't recognizing your modem and/or it's not configured properly.  I'm not sure why a regression would have occurred (since you say it worked before), but please try following [these instructions]("http://ph.ubuntuforums.com/showthread.php?t=595064") to get the modem installed properly.  Please let me know how it goes.

Also, do you remember which instructions you followed when you first installed the device?
Thanks for your continued support with this, I'm still struggling I'm afraid.  Managed step 1, but when trying step 2 got the following response:-

andy@ubuntu:~$ wget [http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c](http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c)
--22:59:48--  [http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c](http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c)
           => `huaweiAktBbo.c'
Resolving [www.kanoistika.sk](www.kanoistika.sk)... 82.119.237.5
Connecting to [www.kanoistika.sk|82.119.237.5|:80](www.kanoistika.sk|82.119.237.5|:80)... failed: No route to host.
andy@ubuntu:~$ wget [http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c](http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c)
--23:00:11--  [http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c](http://www.kanoistika.sk/bobovsky/archiv/umts/huaweiAktBbo.c)
           => `huaweiAktBbo.c'
Resolving [www.kanoistika.sk](www.kanoistika.sk)... 82.119.237.5
Connecting to [www.kanoistika.sk|82.119.237.5|:80](www.kanoistika.sk|82.119.237.5|:80)... failed: No route to host.

________________________________________________________________________________

When I purchased the Webbook, I just plugged in the USB modem and it worked straight away.

---

### Post by pytheas22 on 2008-10-03
Seems like a broken link.  Try substituting the following in for step 2.  Everything else should still work as instructed in the tutorial:
```

wget linux.frankenberger.at/dat/huaweiAktBbo.c
```

This will download the file from a different website--hopefully it's the same file (I just found it through Google).

---

### Post by webbooknovice on 2008-10-04
> **pytheas22 said:**
> Seems like a broken link.  Try substituting the following in for step 2.  Everything else should still work as instructed in the tutorial:
```

wget linux.frankenberger.at/dat/huaweiAktBbo.c
```

This will download the file from a different website--hopefully it's the same file (I just found it through Google).
Thanks. Managed to get a connection via Gnome PPP using the instructions on the following link [http://ubuntuforums.org/showthread.php?p=5569939](http://ubuntuforums.org/showthread.php?p=5569939)  Many thanks for your support and assistance, much appreciated. Kind regards. Andy

---

### Post by razpaz on 2009-09-21
Hi I have an elonex webbook on ubuntu, and cant get my new vodafone usb modem to work.
its a huwaei k3565 prepay modem
i have followed the instructions in the terminal and if i type sudo wvdialconf i get:

sudo wvdialconf
rachel@ubuntu:~$ 
rachel@ubuntu:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
rachel@ubuntu:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


and if i then type sudo gedit /etc/wvdial 

the screen comes up with no text so i cant edit the phone number username and password

CAN ANYONE PLEASE HELP!!!!!???????

---

### Post by pytheas22 on 2009-09-21
razpaz: try typing:

```
sudo gedit /etc/wvdial.conf

```
Note the '.conf' part.  This should bring up the file you're looking for and allow you to specify the phone number, etc. Does this solve the problem?

---

