---
title: "how an mDSL USB work in ubuntu please"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-11
I have just finished installing ubuntu but can not make my mDSL work it was working in wondows what should I do please??

---

### Post by fatharraxman on 2010-11-12
***_[COLOR="Red"]please some kind help[/COLOR]_***
:confused:

---

### Post by dineshs on 2010-11-12
Did you search google?Is [this]("http://ubuntuforums.org/showthread.php?t=942873") related?
OR
[http://pa.ubuntuforums.org/showthread.php?t=1353849](http://pa.ubuntuforums.org/showthread.php?t=1353849)

---

### Post by fatharraxman on 2010-11-12
yes it is related but didn't fixed my problem I googled the internet but still the problem is standing

---

### Post by fatharraxman on 2010-11-12
I tried the link above but am not able to work  my mDSL   what should I do it say in root what I dont understand ***_[COLOR=Red]please help[/COLOR]_***

> [sudo] password for abdulbaagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-ppp is already the newest version.
0 upgradabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo apt-get install gnome-ppp
[sudo] password for abdulbaagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-ppp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wvdial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ pool/main/w/wvstreams
interface ppp0
--> local  IP address 10.12.250.112
--> remote IP address 192.168.50.22
 --> primary   DNS address 212.0.138.12
 --> secondary DNS address 212.0.138.11
 abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
 Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo apt-get install gnome-ppp
 [sudo] password for abdlbaagi: 
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 gnome-ppp is already the newest version.
 0 upgradabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
 Bus 002 Device 004: ID 19d2:fff1 ONDA Communicati
--> local  IP address 10.12.250.112
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo apt-get install gnome-ppp
[sudo] password for abdlbaagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-ppp is already the newest version.
0 upgradabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
Bus 002 Device 004: ID 19d2:fff1 ONDA Communicati[/QUOTE]
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
Bus 002 Device 004: ID 19d2:fff1 ONDA Communication S.p.A. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo apt-get install gnome-ppp
[sudo] password for abdlbaagi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-ppp is already the newest version.
0 upgradabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ lsusb
Bus 002 Device 004: ID 19d2:fff1 ONDA Communicati[/QUOTE]

---

### Post by fatharraxman on 2010-11-12
what next please

> [COLOR=Red]abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
aiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
aiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
aiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
--> secondary DNS address 212.0.138.11abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
--> Sending: ATDT#777
--> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11
aiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
--> PPP negotiation detected.
--> Starting pppd at Fri Nov 12 15:42:20 2010
--> Pid of pppd: 4223
--> Using interface ppp0
--> local  IP address 10.12.221.251
--> remote IP address 192.168.50.22
--> primary   DNS address 212.0.138.12
--> secondary DNS address 212.0.138.11abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
  --> Sending: ATDT#777
  --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
  --> Sending: ATDT#777
  --> Waiting for carrier.
  ATDT#777
  CONNECT
  --> Carrier detected.  Waiting for prompt.
 ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
 --> PPP negotiation detected.
 --> Starting pppd at Fri Nov 12 15:42:20 2010
 --> Pid of pppd: 4223
 --> Using interface ppp0
 --> local  IP address 10.12.221.251
 --> remote IP address 192.168.50.22
 --> primary   DNS address 212.0.138.12
 --> secondary DNS address 212.0.138.11
 aiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
 ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
 --> PPP negotiation detected.
 --> Starting pppd at Fri Nov 12 15:42:20 2010
 --> Pid of pppd: 4223
 --> Using interface ppp0
 --> local  IP address 10.12.221.251
 --> remote IP address 192.168.50.22
 --> primary   DNS address 212.0.138.12abdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
 --> Sending: ATDT#777
 --> Waiting fabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
  --> Sending: ATDT#777
  --> Waiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detectabdulbaagi@abdulbaagi-HP-530-Notebook-PC-KP476AA-ABV:~$ sudo wvdial
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
  --> Sending: ATDT#777
  --> Waiting for carrier.
  ATDT#777
  CONNECT
  --> Carrier detected.  Waiting for prompt.
 ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
 --> PPP negotiation detected.
 --> Starting pppd at Fri Nov 12 15:42:20 2010
 --> Pid of pppd: 4223
 --> Using interface ppp0
 --> local  IP address 10.12.221.251
 --> remote IP address 192.168.50.22
 --> primary   DNS address 212.0.138.12
 --> secondary DNS address 212.0.138.11
 aiting for carrier.
 ATDT#777
 CONNECT
 --> Carrier detected.  Waiting for prompt.
 ~[7f]}#@!}!}!} }9}"}&} } } } }#}%B#}%}%}&} [11][11]}/}'}"}(}"JP~
 --> PPP negotiation detected.
 --> Starting pppd at Fri Nov 12 15:42:20 2010
 --> Pid of pppd: 4223
 --> Using interface ppp0
 --> local  IP address 10.12.221.251
 --> remote IP address 192.168.50.22
 --> primary   DNS address 212.0.138.12
 --> secondary DNS address 212.0.138.11
 --> secondary DNS address 212.0.138.11[/COLOR]


---

### Post by fatharraxman on 2010-11-12
how to get my mdsl work after all this it say connected and it is not connected where is the problem???

---

### Post by dineshs on 2010-11-12
If you are using gnome-ppp,in  options 
[COLOR="Red"]Untick[/COLOR] check carrier line and [COLOR="Red"]tick [/COLOR]stupid mode and see if there is any progress

If you are using wvdial try```
sudo gedit /etc/wvdial.conf
```
> 
add [COLOR="Red"]Carrier Check = no[/COLOR] as a new line (useful for Smartlink modems)
add [COLOR="Red"]Stupid mode = on[/COLOR] as a new line (will start pppd immediately--required by some ISPs)  and try
Also read > Upon connection, it will spit out some information about your connection (local IP, remote IP, DNS address, etc.). Do not  close the terminal where wvdial is running. Leave it alone until you want the connection to be terminated, and hit CTRL+C on that terminal once you want to end the connection.

If you lose the connection a short time after connecting (30 sec - 3 min), you might need to edit options for pppd:

gksudo gedit /etc/ppp/options

Find lcp-echo-interval30 and lcp-echo-failure4. Comment out these options by adding a '#' at the start of these lines, eg. # lcp-echo-interval30 and # lcp-echo-failure4.

If you connect successfully but your Internet applications do not function (eg. web pages do not load in Firefox), you might need to add replacedefaultroute as a new line in the pppd option file. 
ref  [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)
If you still have problem,please post the output of```
ping 4.2.2.1 -c3
```after connecting

---

### Post by fatharraxman on 2010-11-12
thak you very much it is working fully by now am really talking to you through it now
***_[COLOR=DarkRed]thank you again ubuntu scholar[/COLOR]_***
:popcorn::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

