---
title: "Problems with UMTS Vodafone Card"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by lalablubb on 2007-03-25
Hello people,

at first sorry for my bad English. :( 

I've got a big problem with my girlfriend's UMTS Vodafone 3G Card (SNR: QL...).

The card works fine. It recognizes the local UMTS networks and I can connect to my provider. 
But after connecting nothing works. There's a connection but I can't send or receive any data. 

```
angie@Nhel:~$ sudo echo "AT+CPIN=7424" > /dev/ttyUSB0
angie@Nhel:~$ sudo wvdial umts
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATM0
ATM0
OK
--> Sending: AT+CGDCONT=1,"IP","A1.net"
AT+CGDCONT=1,"IP","A1.net"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT 384000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Mar 25 20:03:17 2007
--> Pid of pppd: 9091
--> Using interface ppp0
--> local  IP address 84.20.189.71
--> remote IP address 10.64.64.64
--> primary   DNS address 194.48.139.254
--> secondary DNS address 194.48.124.202

```

Looks great, doesn't it?
But it doesn't work :(

Here's the /etc/wvdial.conf:

```

angie@Nhel:~$ cat /etc/wvdial.conf
# cat /etc/wvdial.conf
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
SetVolume = 0
Dial Command = ATDT
FlowControl = NOFLOW
Init1 = ATZ
Init2 = ATM0

[Dialer umts]
Username = ppp@A1plus.at
Password = ppp
Phone = *99***1#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","A1.net"
Dial Attempts = 3
angie@Nhel:~$ 

```

Anyone here to help me? My girlfriend's getting frustrated (as I'm getting since I'm on this problem since yesterday 3 pm..).


Edit:

/var/log/messages:

```
Mar 25 20:03:17 Nhel pppd[9091]: pppd 2.4.4 started by root, uid 0
Mar 25 20:03:17 Nhel pppd[9091]: Using interface ppp0
Mar 25 20:03:17 Nhel pppd[9091]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 25 20:03:17 Nhel pppd[9091]: CHAP authentication succeeded
Mar 25 20:03:17 Nhel pppd[9091]: CHAP authentication succeeded
Mar 25 20:03:23 Nhel pppd[9091]: Could not determine remote IP address: defaulting to 10.64.64.64
Mar 25 20:03:23 Nhel pppd[9091]: local  IP address 84.20.189.71
Mar 25 20:03:23 Nhel pppd[9091]: remote IP address 10.64.64.64
Mar 25 20:03:23 Nhel pppd[9091]: primary   DNS address 194.48.139.254
Mar 25 20:03:23 Nhel pppd[9091]: secondary DNS address 194.48.124.202
Mar 25 20:04:01 Nhel pppd[9091]: Terminating on signal 15
Mar 25 20:04:01 Nhel pppd[9091]: Connect time 0.7 minutes.
Mar 25 20:04:01 Nhel pppd[9091]: Sent 0 bytes, received 0 bytes.
Mar 25 20:04:01 Nhel pppd[9091]: Connection terminated.
Mar 25 20:04:01 Nhel pppd[9091]: Exit.

```

```
Mar 25 20:03:23 Nhel pppd[9091]: Could not determine remote IP address: defaulting to 10.64.64.64
```

Could it be that single line?

---

### Post by lalablubb on 2007-03-25
No suggestions?
Sorry for my imaptience, but this is really imortant.. :(

---

### Post by lalablubb on 2007-03-25
I don't have any clue why.. But it works no.. :)
Sorry for bothering^^

---

### Post by lalablubb on 2007-03-25
So, it's me again and I'm getting angry..
I've done NOTHING to get this to work and I've done NOTHING to get it broken..

I've figured out what's the problem: The DNS.

Just a few minutes ago when everithing went fine the DNS were something about 194.xxx.xxx.xxx.
Now they are 10.xx.xx.xx

Also before sometimes I got the 10.xxx... DNS.. But after one or two reconnects I got my "good" DNS and it worked. Now I only get the bad DNS..

Please, if someone has a clue why this damn thing wants to get me crying.. Tell me :(

---

### Post by lalablubb on 2007-03-25
So, now I've written two scripts:
The first to send the PIN to the UMTS-card and start wvdial to connect and the second to overwrite the /etc/resolv.conf with the working DNS-adresses.

Not the best solution but it works.. Somehow..

---

