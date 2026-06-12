---
title: "Connecting to the internet via airtel usb modem"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by aby_fulcrum on 2008-09-04
hi, i am a newbie trying very hard to connect to the internet and am failing miserably. Looks like i'll have to switch back to windows.

I use:

Acer Aspire 4520 AMD Laptop
Ubuntu Hardy Heron 64 bit version

Airtel USB Modem manufactured by ZTE CORPORATION CHINA, MZ16 EDGE DATACARD (no linux support according to airtel customer support)

Has anyone succeeded connecting with the airtel usb modem card ?

Please let me know.

Thanks and regards

---

### Post by applegrew on 2008-10-05
Sorry but my reply could be not at all helpful to you, or it may provide some lead. I have a Airtel Micromax USB modem (looks  like a pen drive). I have been able to make it work in Kubuntu Hardy Heron. Some similar steps may help. The link to that post is [http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html](http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html)

---

### Post by aby_fulcrum on 2008-11-04
> **applegrew said:**
> Sorry but my reply could be not at all helpful to you, or it may provide some lead. I have a Airtel Micromax USB modem (looks  like a pen drive). I have been able to make it work in Kubuntu Hardy Heron. Some similar steps may help. The link to that post is [http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html](http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html)
hi, thanks for your reply. i tried and this is the error i am getting. pls help:

ab@ab-laptop:~$ ./connAir
[sudo] password for ab: 
CONNECTING TO Airtel...
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
ppp0: error fetching interface information: Device not found
YOUR CURRENT IP IS ''.
CONNECTION TO Airtel TIMED-OUT........ :(
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
ab@ab-laptop:~$

---

### Post by applegrew on 2008-11-04
> **aby_fulcrum said:**
> hi, thanks for your reply. i tried and this is the error i am getting. pls help:

ab@ab-laptop:~$ ./connAir
[sudo] password for ab: 
CONNECTING TO Airtel...
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
ppp0: error fetching interface information: Device not found
YOUR CURRENT IP IS ''.
CONNECTION TO Airtel TIMED-OUT........ :(
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
ab@ab-laptop:~$
Hi,

U will get this error when, as the error message says, the connection to Airtel takes too long. U can try running the ./connAir again... I once encountered this error myself. Re-running the script solved it.

---

### Post by aby_fulcrum on 2008-11-04
hi. i tried several times. but no luck. any idea if i m doing something wrong. if i can get this to work, i want to move to linux wholly. thanks

---

### Post by applegrew on 2008-11-05
> **aby_fulcrum said:**
> hi. i tried several times. but no luck. any idea if i m doing something wrong. if i can get this to work, i want to move to linux wholly. thanks
Can u pls post the output of **ifconfig** here, after running **connAir**?

---

### Post by aby_fulcrum on 2008-11-06
hi, first and foremost, thanks.my device is identified by $ lsusb as cygnal integrated products. rest of the commands gave the responses pasted below. thanks again

warm regards
aby



b@ab-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 10c4:ea60 Cygnal Integrated Products, Inc. 
Bus 003 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 064e:a101 Suyin Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ab@ab-laptop:~$ ./connAir
[sudo] password for ab: 
CONNECTING TO Airtel...
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
ppp0: error fetching interface information: Device not found
YOUR CURRENT IP IS ''.
CONNECTION TO Airtel TIMED-OUT........ :(
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported
ab@ab-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:2e:6d:8e  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe2e:6d8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1578217 (1.5 MB)  TX bytes:338086 (330.1 KB)
          Interrupt:252 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60595 (59.1 KB)  TX bytes:60595 (59.1 KB)

ab@ab-laptop:~$

---

### Post by applegrew on 2008-11-06
Hi,

Mine shows "Huawei Technologies Co., Ltd. E620 USB Modem", not "Cygnal Integrated Products, Inc.". Your modem is obviously different, hence it is possible that their could be some issues that ur modem is not getting detected, which is evident from the following message:-
> --> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory
--> Cannot open /dev/ttyACM0: No such file or directory

The only advice I can give is that make sure u plug-in ur device before booting your computer.

---

### Post by sohel1 on 2008-11-06
Airtel USB Modem manufactured by ZTE CORPORATION CHINA, MZ16 EDGE DATACARD (no linux support according to airtel customer support)

Has anyone succeeded connecting with the airtel usb modem card ?

---

### Post by GeorgeVita on 2008-11-09
Hi, you are both trying to use a modem installed as **/dev/ttyACM0** which is not there: "--> Cannot open /dev/ttyACM0: No such file or directory".

When  you first plug in the USB modem you can see it with the command **lsusb** (...Cygnal Integr... OR ...Huawei Techno...)
You must find the "device name" assigned by the system for your modem (**/dev/ttyXXXX**), so try the following:
**ls /dev/ttyU* /dev/ttyA***
**grep -e /dev/tty /var/log/messages**

The first one will show you if your modem is connected as /dev/ttyUSBx or /dev/ttyACMx. The second will list all system activity concerning /dev/ttyxxx (search for your modem).
Post any results to follow up.

Regards,
George

---

### Post by aby_fulcrum on 2009-03-11
finally solved connecting usb huawei 620 modem in ubuntu hardy:

i followed directions from 2 areas;

first follow instructions from [http://ubuntuforums.org/showthread.php?t=809220](http://ubuntuforums.org/showthread.php?t=809220)

next create connAir file as instructed in [http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html](http://applegrew.blogspot.com/2008/09/using-airtel-edgegprs-micromax-mmx-610u.html)

next open applications>terminal and type ab@ab-laptop:~$ ./connAir
CONNECTING TO Airtel...
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
ppp0: error fetching interface information: Device not found
YOUR CURRENT IP IS ''.
CONNECTION TO Airtel TIMED-OUT........ :(
Usage: inet_route [-vF] del {-host|-net} Target[/prefix] [gw Gw] [metric M] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [gw Gw] [metric M]
                              [netmask N] [mss Mss] [window W] [irtt I]
                              [mod] [dyn] [reinstate] [[dev] If]
       inet_route [-vF] add {-host|-net} Target[/prefix] [metric M] reject
       inet_route [-FC] flush      NOT supported


DON'T WORRY ABOUT THIS ERROR MESSAGE

NEXT type wvdial 3g in terminal. Here's my ubuntu's response:

ab@ab-laptop:~$ wvdial 3g
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Wed Mar 11 19:29:00 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6817
--> Using interface ppp0
--> local  IP address 117.97.141.33
--> remote IP address 10.64.64.64
--> primary   DNS address 202.56.250.5
--> secondary DNS address 202.56.240.5


HAPPY SURFING! if you want to disconnect press Control C

---

### Post by aby_fulcrum on 2009-06-12
i have a new issue which i am wondering if you know how to solve.

while roaming, the carrier is not detected. i have to login to windows, manually select network, register, reboot into ubuntu and then run ./connair and sudo wvdial to connect. which essentially means i still need windows. do you know how to autodetect and auto register the usb modem E620 Huawei to the existing network whether i am roaming or not.


Regards
aby_fulcrum

---

### Post by GeorgeVita on 2009-06-12
> **aby_fulcrum said:**
> ...while roaming, the carrier is not detected. i have to login to windows, manually select network, register, reboot into ubuntu and then run ./connair and **sudo wvdial** to connect...

Hi **aby_fulcrum**, an idea (I am not sure it will work) is to:

- remove the InitX line which sets the APN (Init5: AT+CGDCONT=1,"IP","internet")
and let the SIM use the default or the roaming set up.

- or ADD some lines with this Init line setting up more APNs from abroad, under [Dialler XYZ], etc.

If you cannot understand above, post your /etc/wvdial.conf and give an example of where to travel.

Regards,
George

---

### Post by aby_fulcrum on 2009-06-14
Thanks George. I \'ll try your suggestion and come back to you

---

### Post by redenex on 2009-11-30
On my laptop I did a clean Koala install and AirTel USB does not connect. But on the desktop, I did an upgrade from Intrepid and AirTel USB works fine! :mad:

---

### Post by ScrewBaxster on 2009-12-01
Hi. I have a Dell Inspiron 6400 running Karmic Koala 32-bit. Ubuntu's a charm, but I got a doubt. Can I have a USB modem work with it? It was provided by an Internet vendor herein my country. It is a Alcatel HSPA USB MODEM. When I plug it into the pc, I can access it and see the files in it. One is an executable for Windows. How can I put it the modem to work with Ubuntu?   Thanks a mil.

---

