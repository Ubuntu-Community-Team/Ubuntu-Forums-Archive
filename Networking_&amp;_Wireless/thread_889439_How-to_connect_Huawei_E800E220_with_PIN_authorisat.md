---
title: "How-to: connect Huawei E800/E220 with PIN authorisation"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Krzysztof on 2008-08-14
This is my very first how-to, so any improvements are welcomed :).

This a result of my googling for HUAWEI E800 gprs modem dial-up connection. The difference to other solutions is that here we have sim card PIN authorization which needs additional attention. This is also why simple solutions based on gnome-ppp or Network Manager do not work... or perhaps if you know how to make them working give me a note.

This solution may also work for HUAWEI E220 USB since I've been taking from their scripts. 

HUAWEI E800 uses an express card connector which is inserted via additional interface to your PCMCIA slot. If you are using kernel >2.6.20 then you just insert it and the system recognizes it perfectly as /dev/ttyUSB0 modem device. Otherwise you need a workaround from here:
[http://oozie.fm.interia.pl/pro/huawei-e220/]("http://oozie.fm.interia.pl/pro/huawei-e220/")

There are three simple steps:

1. define the new peer by creating the peer file:
```
sudo gedit /etc/ppp/peers/hui
```
paste the following code and save:
```
# usbserial device, some options:
/dev/ttyUSB0
460800
idle 7200
lock
crtscts
modem
noauth
# dns, routing
usepeerdns
replacedefaultroute
defaultroute
noipdefault
# avoid compression:
noccp
nobsdcomp
novj
# usually doesnt matter for GPRS/UMTS connections:
user "anyuser"
password "anypassword"
# connect script
connect "/usr/local/bin/hui-connect.sh"
# disconnect script
disconnect "/usr/local/bin/hui-disconnect.sh"
# t-mobile specific?
ipcp-restart 8
ipcp-max-configure 50
ipcp-accept-local
ipcp-accept-remote
```

You may change anypassword and anyuser to any other required by your GSM provider. However, for most cases it does not matter.

2. Create connection scripts:
```
sudo gedit /usr/local/bin/hui-connect.sh
```
paste the following code and save:
```

#!/bin/sh

/usr/sbin/chat -V -f /etc/chatscripts/hui-prep 
# wait to switch between GPRS/UMTS
sleep 20
# the final chat script:
/usr/sbin/chat -V -f /etc/chatscripts/hui

```

```
sudo gedit /usr/local/bin/hui-disconnect.sh
```
with the following code inside:
```

#!/bin/sh

/usr/sbin/chat -V -f /etc/chatscripts/hui-disconnect 

```

3. create chat scripts:
```
sudo gedit /etc/chatscripts/hui-prep
```
paste the following code and save:
```

ABORT BUSY
ABORT ERROR
ABORT 'NO CARRIER'
REPORT CONNECT
TIMEOUT 10
"" "ATZ"
OK "AT+CPIN=XXXX"
OK 'AT+CGDCONT=1,"IP","www.plusgsm.pl"'
OK 'ATS0=0'
OK 'ATE1\d\d'
OK AT+CGQREQ=5,0,0,0,0,0
OK AT+CGATT?
OK "AT+IPR=115200"

```

[COLOR="Red"]Important![/COLOR] Change XXXX to your sim card's PIN number. If you make it wrong then the card will be locked after three times and then you will need PUK number and Windows installation to unlock it.

You should also change this line: 
OK 'AT+CGDCONT=1,"IP","www.plusgsm.pl"' 
so it describes your provider specific data. This one is for Polish PlusGSM. 

```
sudo gedit /etc/chatscripts/hui
```
paste the following code and save:
```

ABORT BUSY
ABORT 'NO CARRIER'
ABORT ERROR
REPORT CONNECT
TIMEOUT 10
SAY "Calling ONE\n"
TIMEOUT 60
"" "ATD*99***1#"
CONNECT \c

```


```
sudo gedit /etc/chatscripts/hui-disconnect
```
paste the following code and save:
```

SAY   "\nDisconnecting the modem...\n"
""    "\K"
""    "+++ATH"
SAY   "\nDisconnected\n"

```

That's it. Now you may try to connect.
Insert the modem and wait until the light will start blinking green (no connection, network ready).

```
pon hui
```

after about 30 sec. the modem connection indicator should go permanently blue. If it blinks then the connection was not correctly established yet.

To disconnect write:
```
poff hui
```
The light should start blinking green again.

To see what's going on you may use:
```
plog
```

This is mostly based on this howto, but the modem script was changed: [http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/]("http://wwwu.uni-klu.ac.at/agebhard/HuaweiE220/")

---

### Post by stachuc on 2008-11-12
It works fine for me. Only do not forget to make hui-connect.sh an executable one. Next thing I was trying to do was share internet with my local network via wi-fi. The problem was to configure the iptables.
It works fine if one set-up the wifi first and then type "pon hui" script will set-up the iptables so it should work fine. 
Don't know if these settings are optimal it is another thing but why the script is changing the iptables????

---

