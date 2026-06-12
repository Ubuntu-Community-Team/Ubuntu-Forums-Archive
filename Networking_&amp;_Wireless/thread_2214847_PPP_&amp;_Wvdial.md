---
title: "PPP &amp; Wvdial"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by Steider on 2014-04-03
Hi,

[I](sorry for my poor english )

[/I]can alreadyI would like to have an internet connection with a 3G modem. This modem is linked with a RS485 port (device /dev/ttyRPC0) and i can already setup him with at commands.
Now, to have my 3G internet connection, i installed pppd and wvdial. I have some difficulties to run them correctly. When i run wvdial, i obtain :

```

sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","orange"
AT+CGDCONT=1,"IP","orange"
OK
--> Modem initialized.
--> Sending: ATD*99#
--> Waiting for carrier.
ATD*99#
CONNECT
~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Apr  3 13:32:11 2014
--> Pid of pppd: 2724
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> pppd: &#9618;[11]&#9618;[18]j|
--> Disconnecting at Thu Apr  3 13:32:11 2014
--> The PPP daemon has died: Serial port open failed (exit code = 7)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&!m=)}#}%B#}%OU~
NO CARRIER

```

Wvdial seems to run correctly but ppp always said : *Serial port open failed (exit code = 7)*

Here is my /etc/wvdial.conf file :
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 19200
New PPPD = yes
Modem =/dev/ttyRPC0
Stupid Mode = yes
ISDN = 0
Stupid mode = yes
Idle Seconds = 0
Init4 = AT+CGDCONT=1,"IP","orange"
Dial Command = ATD
Phone = *99#
Password = "orange"
Username = "orange"

```

My ISP is Orange (in france) and the APN informations are :
[LIST]
[*]APN : orange
[*]Login : orange
[*]Password : orange
[/LIST]

Thanks for your returns

---

### Post by GeorgeVita on 2014-04-06
Hi Steider, welcome to ubuntuforums!

From [http://assistance.orange.fr/configuration-manuelle-si-vous-etes-deja-equipe-d-une-cle-3g-718.php](http://assistance.orange.fr/configuration-manuelle-si-vous-etes-deja-equipe-d-une-cle-3g-718.php)
the apn is **orange.fr** so add ".fr" to init4 line and retry:
```
Init4 = AT+CGDCONT=1,"IP","orange.fr"
```

---

### Post by Steider on 2014-04-07
Thanks for your reply.

Indeed, it was a mistake. I fixed it and here is what it gives me now :
```

sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","orange.fr"
AT+CGDCONT=1,"IP","orange.fr"
OK
--> Modem initialized.
--> Sending: ATD*99#
--> Waiting for carrier.
ATD*99#
CONNECT
~[7f]}#@!}!}#} }9}"}&} }*} } }'}"}(}"}%}&C}9yN}#}%B#}%zw~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Apr  7 08:35:29 2014
--> Pid of pppd: 2499
--> pppd: &#9618;[11]&#9618;[18][1a][17][01][08][1a][17][01]
--> Disconnecting at Mon Apr  7 08:35:30 2014
--> The PPP daemon has died: Serial port open failed (exit code = 7)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds

```

---

### Post by GeorgeVita on 2014-04-07
1. Give us more data about your modem (manufacturer, type) and your system (whisch ubuntu version).
From terminal:
```
uname -a
```

2. Check your SIM with a mobile phone, remove PIN lock, connect to internet using the mobile phone.

3. Reboot your system, attach modem, open a terminal window and execute the following long command (without running wvdial):

```
sudo pppd ttyRPC0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','orange.fr'" OK "atdt*99#" CONNECT' user orange password orange
```
(copy all command and paste it to terminal, press enter, give your password, check and reply with results).

---

### Post by Steider on 2014-04-07
Here is some informations :

[LIST]
[*]Modem : Gemalto Cinteron BGS2T-RS485 ([Website]("http://m2m.gemalto.com/products/terminals/bgs2t.html"))
[*]System : Raspberry Pi B under Raspbian OS :[SIZE=2] [FONT=courier new]*Linux raspberrypi 3.6.11+ #474 PREEMPT Thu Jun 13 17:14:42 BST 2013 armv6l GNU/Linux*[/FONT][/SIZE]
[*]My sim is a USIM M2M and have no PIN (disabled). I tried to access to internet with my phone and the sim and its work. Then its surely my configurations that doesn't... :(
[/LIST]

And here is the result of the script you gave me :
```

sudo pppd ttyRPC0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','orange.fr'" OK "atdt*99#" CONNECT' user orange password orange
Connect script failed

```


_EDIT :_
After reboot (for the second time) i retried the script and it finaly answered :
```

sudo pppd ttyRPC0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','orange.fr'" OK "atdt*99#" CONNECT' user orange password orange
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyRPC0
CHAP authentication succeeded
CHAP authentication succeeded
LCP terminated by peer
Connection terminated.
Modem hangup

```

---

### Post by Lars Noodén on 2014-04-07
I have a Huawei 3g modem and to get it connecting automatically I had to add the following to /etc/modules

```

option 
usb_wan
usbserial
usb_storage

```

Those allow me to plug in the modem and the network manger finds it automatically and established the connection.  It only takes a few seconds to find it and connect.  Maybe that would work for your situation as well.

---

### Post by Steider on 2014-04-07
Thanks for your answer Lars Noodén,

After retry the last code with your solution, i had this :
```

sudo pppd ttyRPC0 nodetach defaultroute noipdefault lock usepeerdns connect 'chat "" "at" "" "at" "OK" "at&f" "OK" "atz" "OK" "at+cgdcont=1,'IP','orange.fr'" OK "atdt*99#" CONNECT' user orange password orange
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyRPC0
No response to 4 echo-requests
Serial link appears to be disconnected.
Connection terminated.
Modem hangup

```

I think its not better but before the "No response to 4 echo-requests", i had the time to do an ifconfig and i saw the ppp0 interface :
```

ppp0      Link encap:Point-to-Point Protocol
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I think the interface apear without your configuration but then, the script run too fast and i haven't the time to do an ifconfig.

---

### Post by GeorgeVita on 2014-04-07
> **Lars Noodén said:**
> I have a Huawei 3g modem ...
Hi Lars,
I think that this is a different situation, this is not USB modem. As you probably know, RS-485 is the industrial version of RS-232 serial port and there is no "auto-sensing" of peripherals.

As Steider noticed some differences, it may be due to setup done by option (or other) driver.

> **Steider said:**
> ...
_EDIT :_
After reboot (for the second time) i retried the script and it finaly answered :
...

From the first try, the modem got "CONNECTED" and after pppd got disconnected. This could be done from the provider side (unapproved, wrong parameters, timeout) or locally ex. cannot setup networking (IP addresses ?? minimal knowledge here!).
The direct use of a "single command" left wvdial out of the test (in case it blocks serial port), but the problem still exists.

To use network manager, we need a redirection (symlink?) or force it to use /dev/ttyRPC0".

Some other search terms into ubuntuforums: gnome-ppp, pppconfig, **lkraemer wvdial**
Old "8.04" wvdial info: [http://web.archive.org/web/20090208023824/http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://web.archive.org/web/20090208023824/http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

I don't thing it is a problem but try a higher baud rate (115200).

---

### Post by Steider on 2014-04-08
I am simultaneous on [this forum]("http://forums.debian.net/viewtopic.php?f=30&t=113122&p=536761#p536761").

I contacted my ISP (Orange in France), and he can't help me more. They still confirmed that "orange" and "orange.fr" are available as APN (with login and password to "orange").

I already tested to create a link between /dev/ttyRPC0 and /dev/ttyS0 : ln -s /dev/ttyRPC0 /dev/ttyS0
That doesn't work much, but some other soft like sakis3G can now detect my device but he "failed to connect".

I then tried the 115200 baud (its effectively advisable to use this rate), but nothing more. I think we improve the configuration but there is one little thing missing.

---

### Post by GeorgeVita on 2014-04-09
You have a custom OS (raspbian) with a rare modem (RS485) ...

I think you must search why "LCP terminated by peer".
Some instructions for debugging: [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_term_authentication](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_term_authentication)

Another idea is: try to connect using other modem or another provider (use your mobile phone's SIM instead the M2M one)

---

### Post by Steider on 2014-04-09
Hi !


I finally resolve a the largest part of the problem :D . I studied lot of links you gave me and analysed erros from /var/log/syslog.


Now pppd start well.It seems the problem came from ppp options and the chatscript. Here is theses files :


/etc/ppp/peers/generic-file (default configuration file lauch with pppd) :
```

# file: /etc/ppp/peers/generic-file
#
# Default modem (you better replace this with /dev/ttySx or /dev/ttyACM0 for usb!)
/dev/ttyRPC0 115200


# pppd options
noauth
persist
nodetach
crtscts
local
debug
noipdefault
netmask 255.255.255.0
defaultroute




# Logfile configuration "log will be stored into ppp-logfile
logfile /etc/ppp/ppp-logfile
record /etc/ppp/ppp-dumplog


connect "/usr/sbin/chat -v -T orange -f /etc/chatscripts/generic-connect"

```


And the /etc/chatscripts/generic-connect (called by the previous connect parameter) :
```

# File: /etc/chatscripts/generic-connect.
# APN is being passed from the configuration file to variable \T
#
TIMEOUT 10
ABORT BUSY
ABORT 'NO ANSWER'
ABORT "NO CARRIER"
ABORT VOICE
ABORT "NO DIALTONE"
ABORT 'ERROR'
SAY ' Starting GPRS connect script'
"" 'ATZ'
OK 'ate0v1'
SAY 'Setting APN\n'
OK 'at+cgdcont=1,"IP","\T"'
ABORT 'NO CARRIER'
SAY 'Dialing...'
OK 'ATD*99***1#'
CONNECT

```


Now i have some other little problems :
*My ppp0 interface looks like that :
```

ppp0      Link encap:Point-to-Point Protocol
          inet addr:10.69.176.104  P-t-P:192.168.254.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:2 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:40 (40.0 B)  TX bytes:77 (77.0 B)

```
But i need a public IP, i can't reach 10.69.176.104 through the web. How can i have a public IP ?


*Also, each time i execute ppp, i obtain my interface but when i disconnect (CTRL+C), the pppd command doesn't work without restarting the modem  :roll: . Is there a way to prevent this or maybe a "reboot" AT command ?

Edit :
 I can ping for exemple 8.8.8.8 but when i try to go on [www.google.com]("http://www.google.com") with a web browser, it doesn't work...  :shock:

---

### Post by GeorgeVita on 2014-04-09
> **Steider said:**
> ... Now pppd start well
... Edit :
 I can ping for exemple 8.8.8.8 but when i try to go on [www.google.com]("http://www.google.com") with a web browser, it doesn't work...  :shock:

Now you need to check/setup DNS: [http://www.dcaccess.net/welcome/linux/PPP-HOWTO-10.html](http://www.dcaccess.net/welcome/linux/PPP-HOWTO-10.html)
Also some info with terminal command: **man pppd**

Show us whole terminal procedure that managed the connection. It will be usefull by other readers and will drive us to find he proper disconnection.
You can "reset" a modem with AT&F (restore factory settings) and then ATZ (reset parameters):
```
AT&F
ATZ
```


***EDIT: this case solved as noted to debian forums:***
> **Steider said:**
> I am simultaneous on [this forum]("http://forums.debian.net/viewtopic.php?f=30&t=113122&p=536761#p536761")...> from [http://forums.debian.net/viewtopic.php?f=30&t=113122&p=536761#p537017](http://forums.debian.net/viewtopic.php?f=30&t=113122&p=536761#p537017)

Re: PPPD & Wvdial configuration
Postby Steider » 2014-04-10 08:59
**Finally, each SIM card can have several APN. In my case, "orange.fr" is a private IP APN. The ISP can provide a public IP APN that now work for me** :)
Now, there is only one tiny problem : the reset.
Indeed ATZ command work fine in normal mode, but once connected, i can't send AT commands. I think it must have a command to exit the connection and return in "AT mode", but i dont know which ?
Exept this last tiny thing, congratulation ! Problem solved ! :D

---

