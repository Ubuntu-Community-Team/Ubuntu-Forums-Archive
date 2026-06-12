---
title: "USB internet connection with Sony Ericsson W810"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by faizkhan on 2008-05-31
Hi, 
I am trying to connect to Internet using Sony Ericsson W810i phone. I created the connection by editing the wvdial.conf as 
[Dialer Defaults]
Modem = /dev/ttyACM0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = On
Modem Type = USB Modem
Phone = *99***1#
New PPPD = yes
ISDN = 0
Username = b
Carrier Check = No
Password = a
Baud = 460800

but once I dial the phone shows the connection is made but nothing actually happens as far as internet in concerned on the laptop. I can ping a certain URL using terminal but cant connect to internet. This is the output I get when I try to connect
faiz@Faiz-l-1420:~$ wvdial
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
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!}!} }8}#}$@#}(}"}'}"}"}&} } } } }%}&n>}/qiA~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jun  1 03:44:59 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 8343
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 117.96.72.78
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 202.56.250.5
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 202.56.250.6
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]

Also these settings work perfectly fine with Sony Ericsson W580i which my friend has. My w810i works fine with Windows Vista but I am unable to figure out why it is not working with Ubuntu:(
Plz help.

---

### Post by tech_cheetah on 2008-06-01
thats quite weird .. these are common settings which work in most of the cases ..

---

### Post by safe357 on 2008-06-01
which connection u r using if u r using airtel try this 



1. Install wvdial.
2. Open terminal and type wvdialconf. This searches for the modem and writes a config file to the /etc/wvdial.conf.
3. fire up kate /etc/wvdial.conf and paste the following code replacing the orginal code.

[Dialer Defaults]
Init1 = AT+CGDCONT=1,”IP”,”airtelgprs.com”,”",0,0
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
stupid mode = 1
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = a
Username = a
4. save and exit kate.
5. type wvdial on the terminal to connect to the net.(the following code is obtained)

cyriac@T3rminal0:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: AT+CGDCONT=1,”IP”,”airtelgprs.com”,”",0,0
WvDial Modem<*1>: AT+CGDCONT=1,”IP”,”airtelgprs.com”,”",0,0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}”}&} }*} } g}%~
WvDial<*1>: Carrier detected. Starting PPP immediately.
WvDial<Notice>: Starting pppd at Wed Dec 19 22:18:53 2007
WvDial<Err>: Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
WvDial<Err>: –> PAP (Password Authentication Protocol) may be flaky.
WvDial<Err>: Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
WvDial<Err>: –> CHAP (Challenge Handshake) may be flaky.
WvDial<Notice>: Pid of pppd: 7870
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: local IP address 117.97.47.9
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: primary DNS address 202.56.250.5
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: secondary DNS address 202.56.250.6
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]

5. to disconnect press Ctrl+c

Caught signal 2: Attempting to exit gracefully...
WvDial<*1>: Terminating on signal 15
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: Connect time 632.4 minutes.
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: pppd: (&#65533;[06][08]&#65533;&#65533;[06][08]
WvDial<*1>: Disconnecting at Thu Dec 20 08:51:18 2007

---

### Post by Kevbert on 2008-06-01
What network are you using (Cingular)?  and it which country (US) ? Is GPRS/Edge/3G activated on your SIM card ?  Username and Password are network and subscription specific.

---

### Post by faizkhan on 2008-06-03
Thanks for your replies but it worked only after I manually configured the network connections as IPV4.

Its airtel network. If I get any further problems i'll try the settings for airtel as you have suggested.

---

### Post by kumarkrishnan on 2008-06-12
Hi,
  Just check with following link. This is how I got connected with wvdial.

[http://ubuntuforums.org/showthread.php?t=756777&highlight=w810i](http://ubuntuforums.org/showthread.php?t=756777&highlight=w810i)

KK

---

