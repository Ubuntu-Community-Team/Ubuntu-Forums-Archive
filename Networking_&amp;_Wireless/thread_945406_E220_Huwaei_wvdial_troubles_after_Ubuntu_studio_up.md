---
title: "E220 Huwaei wvdial troubles after Ubuntu studio upgrade"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by theplasticbag on 2008-10-12
Hi,

Firstly I realise that this forum is here for those that have had issues and I have attempted to remedy this myself but still no luck.

I was using Ubuntu Studio 7.04 and had managed to set up internet for my E220 HUWAEI HSDPA USB Modem.  I am on Mobile Broadband and my carrier is Hutchinson 3.  I had issues getting it to work initially but it was working fine.

I believe that my problem may be to do with an error regarding usbserial but I'll leave the logs so that someone may be able to help me. 

It was working fine - but since upgrading to 8.10 I am now having problems.

Essentially the behaviour of WVDIAL is axactly the same for its output except that when I pop open Firefox I get the address not  found message after waiting a while on a page loading.

I should say that I am aware that the dongle works through windows xp as I am able to send you this message.  I realise that some commented that using network manager may be a better solution however my lack of knowledge of linux means that I am unsure of which depencies were the correct ones.  I don't mind going down this road if it were to work but I was happy with wvdial till the upgrade.

Help would be appreciated.

**WVDIAL.CONF**
[B][Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
stupid mode = 1
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = *99#
Modem = /dev/ttyUSB0
Username = Anything
Password = Anything
Dial Command = ATDT
Baud = 9600

[Dialer Three]
Init2 = ATZ
Init3 = ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
Init5 = AT+CGDCONT=1,"IP","3Internet"
ISDN = 0
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
Baud 460800
[/B]


**LSUSB**

[B]steveo@ubuntustudio:~$ lsusb
Bus 005 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 005 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 003: ID 03f0:2d17 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0b0c Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

[/B]


**WVDIAL TERMINAL**

[B]
steveo@ubuntustudio:~$ sudo wvdial defaults
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
--> Starting pppd at Sun Oct 12 12:45:18 2008
--> Pid of pppd: 6722
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 92.41.79.223
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 4.2.2.3
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 4.2.2.4
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
[/B]

---

### Post by GeorgeVita on 2008-10-12
Hi,
in your example you are using the "default" part of wvdial.conf which does not specifies the APN=internet for your provider. The result is the DNS numbers 4.2.2.3 and 4.2.2.4 which are not good (Domain Name Server number is used by firefox to find the specific address for web pages).

Try to dial using **wvdial Three** and post the results.

Regards,
George

---

### Post by theplasticbag on 2008-10-12
Thanks very much for replying to my query.

I had tried doing it under three configuration as well but only piped result for defaults. Anyway,  here is the output for three.

<B>WVDIAL three output

steveo@ubuntustudio:~$ sudo wdial three
sudo: wdial: command not found
steveo@ubuntustudio:~$ sudo wvdial three
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Oct 12 19:06:39 2008
--> Pid of pppd: 6356
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sun Oct 12 19:07:03 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Oct 12 19:07:17 2008
--> Pid of pppd: 6359
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sun Oct 12 19:07:52 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Oct 12 19:08:06 2008
--> Pid of pppd: 6362
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 92.41.118.14
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 4.2.2.4
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 4.2.2.3
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> Connect time 2.5 minutes.
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sun Oct 12 19:10:39 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
ATE0 V1 &D2 &C1 S0=0 +IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Oct 12 19:10:53 2008
--> Pid of pppd: 6407
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 92.41.147.209
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 4.2.2.3
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 4.2.2.4
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]</B>


<B>
/var/log/messages/

Oct 12 19:08:10 ubuntustudio pppd[6362]: local  IP address 92.41.118.14
Oct 12 19:08:10 ubuntustudio pppd[6362]: remote IP address 10.64.64.64
Oct 12 19:08:10 ubuntustudio pppd[6362]: primary   DNS address 4.2.2.4
Oct 12 19:08:10 ubuntustudio pppd[6362]: secondary DNS address 4.2.2.3
Oct 12 19:10:36 ubuntustudio pppd[6362]: No response to 4 echo-requests
Oct 12 19:10:36 ubuntustudio pppd[6362]: Serial link appears to be disconnected.
Oct 12 19:10:36 ubuntustudio pppd[6362]: Connect time 2.5 minutes.
Oct 12 19:10:36 ubuntustudio pppd[6362]: Sent 1932 bytes, received 0 bytes.
Oct 12 19:10:39 ubuntustudio pppd[6362]: Modem hangup
Oct 12 19:10:39 ubuntustudio pppd[6362]: Connection terminated.
Oct 12 19:10:39 ubuntustudio pppd[6362]: Exit.
Oct 12 19:10:53 ubuntustudio pppd[6407]: pppd 2.4.4 started by root, uid 0
Oct 12 19:10:53 ubuntustudio pppd[6407]: Using interface ppp0
Oct 12 19:10:53 ubuntustudio pppd[6407]: Connect: ppp0 <--> /dev/ttyUSB0
Oct 12 19:10:53 ubuntustudio pppd[6407]: CHAP authentication succeeded
Oct 12 19:10:53 ubuntustudio pppd[6407]: CHAP authentication succeeded
Oct 12 19:10:57 ubuntustudio pppd[6407]: Could not determine remote IP address: defaulting to 10.64.64.64
Oct 12 19:10:57 ubuntustudio pppd[6407]: local  IP address 92.41.147.209
Oct 12 19:10:57 ubuntustudio pppd[6407]: remote IP address 10.64.64.64
Oct 12 19:10:57 ubuntustudio pppd[6407]: primary   DNS address 4.2.2.3
Oct 12 19:10:57 ubuntustudio pppd[6407]: secondary DNS address 4.2.2.4
Oct 12 19:11:51 ubuntustudio pppd[6407]: Terminating on signal 15
Oct 12 19:11:51 ubuntustudio pppd[6407]: Connect time 0.9 minutes.
Oct 12 19:11:51 ubuntustudio pppd[6407]: Sent 0 bytes, received 0 bytes.
Oct 12 19:15:16 ubuntustudio kernel: [ 1643.263388] nautilus[6141]: segfault at 0000000c eip 08107388 esp bfb82460 error 4 </B>

---

### Post by GeorgeVita on 2008-10-12
From the wvdial.conf section [Dialler Three] remove lines Init2 and Init3 and retry. Also be careful with upper/lower case as ALL linux (unix) systems are case sensitive. In your example use **wvdial Three** and not wvdial three.

P.S. another question: do you have ethernet connected at the same time? If yes unplug it, reboot and test again. Do you know what is DHCP and how to enable it?

---

### Post by theplasticbag on 2008-10-13
I've removed the Init lines you have mentioned and still had the same result. Thanks for the note about case sensitivity - I hadn't notice I had done that.  'Three' has now been changed to 'three' if you look at the terminal wvdial output.

I have an ethernet connection but this isnt used so there is ethernet cable attached.

I know of DHCP but I wouldnt know how to enable it.  In the past access to this has normally been done by accessing router defaults.  Unfortunately as this is a USB dongle for a cellular/mobile broadband service I am lost as to how to do that through linux.  Although attempts at trying to use windows own network connections make me aware that a different IP address seems to be assigned to the device everytime I log on.

<B>Output of last attempt

teveo@ubuntustudio:~$ sudo wvdial three
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","3internet"
AT+CGDCONT=1,"IP","3internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Oct 13 21:23:55 2008
--> Pid of pppd: 6309
--> Using interface ppp0
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 92.41.90.109
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 4.2.2.3
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 4.2.2.4
--> pppd: &#548;[06][08]&#65533;&#65533;[06][08]


</B>

---

### Post by GeorgeVita on 2008-10-14
Hi again!
Now we have a better wvdial.conf but we are facing the same problem as in your first post. The DNS (4.2.2.3 & 4.2.2.4) are somewhere losted inside Hutchinson3 servers or locally to your PC!
**We need help from other readers of this thread!**

Till then ... lets try set the DNS manually. After connecting (sudo wvdial three), do the following:
(Menus and selections are from Ubuntu 8.04)
System > Administration > Network > Unlock > give password > DNS >
click on 4.2.2.3 > Delete > click on 4.2.2.4 > Delete > Add > 
212.73.32.3 > press ENTER > Add > 212.73.32.67 > press ENTER > Close

Be sure for correct numbers! (I test them and work in my PC)

Click Firefox icon, untick the Work Offline (from File menu), and try browsing.

Also let me know in which country is Hutchinson 3 (to search for proper DNS and APN) and what version of Network Manager do you have?

EDIT: another user says that E220 works directly with Network Manager 0.7
[http://ubuntuforums.org/showthread.php?t=941300](http://ubuntuforums.org/showthread.php?t=941300) (post#5)

---

### Post by pohl9876 on 2008-11-16
Hi,

Did you solve your problem in the meantime? I am using Hutchinson 3 Mobile internet in the UK with a HUAWAI E169G HSDPA modem under Debian Etch without any problems. The configuration should be identical for Ubuntu.

Here is my wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Modem Type = Analog Modem
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT+CGDCONT=1,"IP","3internet"
Dial Command = ATDT
Phone = *99#
Username = foo
Password = bar
Stupid Mode = yes

In /etc/network/interfaces I have put

#auto ppp0
iface ppp0 inet wvdial
  provider defaults

so I can control the connection with "ifup ppp0" and "ifdown ppp0" and could also easily make the connection autostart on bootup by uncommenting the "auto" line. I hope this helps.

You can check that the default route is set correctly with the route command:

Kernel IP routing table
Destination     Gateway      Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *            255.255.255.255 UH    0      0        0 ppp0
default         *            0.0.0.0         U     0      0        0 ppp0

Also, the DNS servers should be automatically written to /etc/resolv.conf:

nameserver 4.2.2.4
nameserver 4.2.2.3
search linux.lan

If you still have problems let me know and I will see if I can help.
Alexander

---

### Post by theplasticbag on 2008-11-25
I haven't been able to get the thing working.  My lack of knowledge isnt making this easier.  For the moment I am relying on XP for net usage and this is meaning that I am not using linux which isn't ideal.

One of the problems I am facing is that there is that the internet appears to be working - in that there appears to be a connection running if looking at wvdial report dialogue.  However, using linux, 3's service is so unreliable during peak periods that I have seen the google search screen but can't seem to get a page to load afterwards.

I will look at your suggestions and have a shot.

---

