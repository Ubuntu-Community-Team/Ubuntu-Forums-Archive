---
title: "Sony Ericsson GSM PC Card GC85 - lose connection"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by danpre on 2006-08-07
I have Sony Ericsson GSM PC Card GC85 and connection from Orange, Poland.

I'm able to start connection, browse 1 or 2 pages and then I lose connection. 

The only thing I have found out is when connection is broken command:
```
dmesg | grep tty
```

gives nothing.

Any ideas?

```
root@danpre:/etc/ppp# cardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1="Sony Ericsson"
PRODID_2="GC85 PC Card"
PRODID_3="ML2022"
PRODID_4=""
MANFID=0221,2000
FUNCID=2

```
My conf:
file: /etc/ppp/peers/orange

```

noauth
connect "/usr/sbin/chat -v -f /etc/ppp/orange-connect"
disconnect "/usr/sbin/chat -v -f /etc/ppp/orange-disconnect"
debug
/dev/ttyS3
115200
defaultroute
crtscts
lock
local
nodetach
usepeerdns
lcp-echo-failure 4
lcp-echo-interval 65535

```

file: /etc/orange-connect
```
TIMEOUT 600
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'ERROR'
SAY 'Starting GPRS connect script\n'

"" 'AT+CFUN=1,1'
"" 'AT+CPIN=****'

OK 'ATE1\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d'

SAY 'Setting APN\n'
OK 'AT+CGDCONT=1,"internet","internet"'

ABORT 'NO CARRIER'
SAY 'Dialing...\n'
OK 'ATD*99***1#'

CONNECT ''
```

**** is my PIN number

file: /etc/orange-disconnect

```
"" "\K"
"" "+++ATH0"
SAY "GPRS Disconnected."
```

And this is my:
file: /var/log/messages
```
Aug  7 22:30:20 localhost pppd[12070]: pppd 2.4.4b1 started by root, uid 0
Aug  7 22:30:20 localhost chat[12071]: timeout set to 600 seconds
Aug  7 22:30:20 localhost chat[12071]: abort on (BUSY)
Aug  7 22:30:20 localhost chat[12071]: abort on (NO ANSWER)
Aug  7 22:30:20 localhost chat[12071]: abort on (ERROR)
Aug  7 22:30:20 localhost chat[12071]: send (AT+CFUN=1,1^M)
Aug  7 22:30:20 localhost chat[12071]: send (AT+CPIN=****^M)
Aug  7 22:30:21 localhost chat[12071]: expect (OK)
Aug  7 22:30:21 localhost chat[12071]: ^M
Aug  7 22:30:21 localhost chat[12071]: *MRDY: 1^M
Aug  7 22:30:21 localhost chat[12071]: AT+CFUN=1,1^M^M
Aug  7 22:30:21 localhost chat[12071]: OK
Aug  7 22:30:21 localhost chat[12071]:  -- got it
Aug  7 22:30:21 localhost chat[12071]: send (ATE1\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d\d^M)
Aug  7 22:30:51 localhost chat[12071]: expect (OK)
Aug  7 22:30:51 localhost chat[12071]: ^M
Aug  7 22:30:51 localhost chat[12071]: AT+CPIN=****^M^M
Aug  7 22:30:51 localhost chat[12071]: *MRDY: 4^M
Aug  7 22:30:51 localhost chat[12071]: ATE1^M
Aug  7 22:30:51 localhost chat[12071]: OK
Aug  7 22:30:51 localhost chat[12071]:  -- got it
Aug  7 22:30:51 localhost chat[12071]: send (AT+CGDCONT=1,"internet","internet"^M)
Aug  7 22:30:52 localhost chat[12071]: abort on (NO CARRIER)
Aug  7 22:30:52 localhost chat[12071]: expect (OK)
Aug  7 22:30:52 localhost chat[12071]: ^M
Aug  7 22:30:52 localhost chat[12071]: ^M
Aug  7 22:30:52 localhost chat[12071]: *MTSMENU: "SIMteligent", 0, 4
Aug  7 22:30:52 localhost chat[12071]: ^M1:"Serwisy"
Aug  7 22:30:52 localhost chat[12071]: ^M2:"mBox"
Aug  7 22:30:52 localhost chat[12071]: ^M3:"HitCzat"
Aug  7 22:30:52 localhost chat[12071]: ^M4:"Lokalizacja"
Aug  7 22:30:52 localhost chat[12071]: ^M^M
Aug  7 22:30:52 localhost chat[12071]: ^M
Aug  7 22:30:52 localhost chat[12071]: *MRDY: 3^M
Aug  7 22:30:52 localhost chat[12071]: ^M^M
Aug  7 22:30:52 localhost chat[12071]: OK
Aug  7 22:30:52 localhost chat[12071]:  -- got it
Aug  7 22:30:52 localhost chat[12071]: send (ATD*99***1#^M)
Aug  7 22:30:52 localhost chat[12071]: expect (CONNECT)
Aug  7 22:30:52 localhost chat[12071]: ^M
Aug  7 22:30:52 localhost chat[12071]: AT+CGDCONT=1,"internet","internet"^M^M
Aug  7 22:30:52 localhost chat[12071]: OK^M
Aug  7 22:30:52 localhost chat[12071]: ATD*99***1#^M^M
Aug  7 22:30:52 localhost chat[12071]: CONNECT
Aug  7 22:30:52 localhost chat[12071]:  -- got it
Aug  7 22:30:52 localhost chat[12071]: send (^M)
Aug  7 22:30:52 localhost pppd[12070]: Serial connection established.
Aug  7 22:30:52 localhost pppd[12070]: Using interface ppp0
Aug  7 22:30:52 localhost pppd[12070]: Connect: ppp0 <--> /dev/ttyS3
Aug  7 22:30:57 localhost pppd[12070]: appear to have received our own echo-reply!
Aug  7 22:30:57 localhost pppd[12070]: Remote message: PAP access OK
Aug  7 22:30:57 localhost pppd[12070]: PAP authentication succeeded
Aug  7 22:30:57 localhost kernel: [17195239.692000] PPP BSD Compression module registered
Aug  7 22:30:57 localhost kernel: [17195239.740000] PPP Deflate Compression module registered
Aug  7 22:30:59 localhost pppd[12070]: local  IP address 172.21.24.135
Aug  7 22:30:59 localhost pppd[12070]: remote IP address 172.21.24.0
Aug  7 22:30:59 localhost pppd[12070]: primary   DNS address 194.9.223.79
Aug  7 22:30:59 localhost pppd[12070]: secondary DNS address 217.17.34.10
Aug  7 22:33:57 localhost pppd[12070]: Terminating on signal 2
I have terminated this manually
Aug  7 22:33:57 localhost pppd[12070]: Connect time 3.0 minutes.
Aug  7 22:33:57 localhost pppd[12070]: Sent 31041 bytes, received 38149 bytes.



```

---

