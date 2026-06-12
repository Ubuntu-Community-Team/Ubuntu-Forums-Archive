---
title: "USB Modem authentication error and garbage values"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Harini1111 on 2008-11-25
Hi,

I have followed the tutorial below to setup my modem.

[http://ubuntuforums.org/showthread.php?t=650795](http://ubuntuforums.org/showthread.php?t=650795)

My question is, my modem try to connect in the first time and getting tje authentication failure. If I try to reconnect I am getting some unknown (garbage) strings and those are look like ppp string. I would like know what those are? Even if I tried many times I got the same. If I reset my device forcefully(power off and on) then only these garbage strings goes off and getting Authentication error back.

Since my modem has not activated by Internet provider, Authentication error is expected one but garbage string are concerning me? Please see my log file below.

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
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Tue Nov 25 12:46:10 2008
--> Pid of pppd: 17454
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) started
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Authentication (CHAP) failed
--> ***** no quoted text found in `rcvd [CHAP Failure id=0x1 ""]' *****
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Terminate Request (Message: "Failed to authenticate ourselves to peer" )
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Terminate Request
--> ***** no quoted text found in `rcvd [LCP TermReq id=0x2]' *****
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Tue Nov 25 12:46:14 2008
--> Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password?
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[1a]H%[10]}'}"}(}"[1e]|~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[1a]H%[10]}'}"}(}"-&~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[1a]H%[10]}'}"}(}"3h~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[1a]H%[10]}'}"}(}"K[12]~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&[1a]H%[10]}'}"}(}"U\~
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&v)"L}'}"}(}".1~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&v)"L}'}"}(}"}=k~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&v)"L}'}"}(}"}#%~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&v)"L}'}"}(}"{_~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&v)"L}'}"}(}"e[11]~
--> Modem not responding.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&Vi}!}1}'}"}(}"$O~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&Vi}!}1}'}"}(}"}7[15]~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&Vi}!}1}'}"}(}"})[~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&Vi}!}1}'}"}(}"q!~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&Vi}!}1}'}"}(}"oo~
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&E"[18]r}'}"}(}"}+w~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&E"[18]r}'}"}(}"8-~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&E"[18]r}'}"}(}"&c~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&E"[18]r}'}"}(}"^}9~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&E"[18]r}'}"}(}"@W~
--> Modem not responding.
--> Disconnecting at Tue Nov 25 12:47:26 2008
root@hp-umpc:/home/hp# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&rpN4}'}"}(}"/n~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&rpN4}'}"}(}"}<4~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&rpN4}'}"}(}"}"z~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&rpN4}'}"}(}"z} ~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&rpN4}'}"}(}"dN~
--> Sending: ATQ0
--> Re-Sending: ATZ
~[7f]}#@!}!}!} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&cQ5#}'}"}(}"l-~~[7f]}#@!}!}"} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&cQ5#}'}"}(}"_w~~[7f]}#@!}!}#} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&cQ5#}'}"}(}"A9~~[7f]}#@!}!}$} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&cQ5#}'}"}(}"9C~~[7f]}#@!}!}%} }=}!}$}%\}"}&} } } } }#}%B#}%}%}&cQ5#}'}"}(}"'
~
--> Modem not responding.

---

