---
title: "Aircard 580 at Ubuntu 8.04"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by AV1611 on 2008-05-29
Actually, I have tried the same (about the same) at Debian 4.0 32-bit; neither there is any success in that.

So, what have we got:
1. A laptop - HP 7400
2. A PCMCIA modem Aircard 580, produced originally for Sprint USA. A big lot of these (and other) modems have been brought into Ukraine, unlocked and made up for using at a local CDMA-provider network (Intertelecom).

The modem has been set up at the provider's office and thoroughly tested right there (at Win XP Home). But, sure, I would not want to be limited with Windows env-t and I've been thinking of a possibility to make it work at Linux (actually, its specs say it is linux-compatibtle). OK, after some short googling I found a little manual with some initial instructions.
> 
The Sierra Wireless AirCard® 580 is a wireless mobile card offering users the fastest speeds to access critical information, it is an ideal communication tool for road warriors requiring seamless connectivity. the AirCard features 1xEV-DO hispeed wireless access at up to 2.4Mbps.



The AirCard only officially support the MS Windows OS. This of course isn't going to stop us from trying to get it working in Linux!. The Windows application provided by Sierra does provide a nice GUI for tracking usage, but nothing that our typical ppp connection could not keep track of.

Installation 
To begin we need to insert our wireless card into our PCMCIA slot. 'lspci -v' shows us what this card looks like:

03:00.0 USB Controller: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller (rev 10) (prog-if 10 [OHCI])
Subsystem: Agere Systems (former Lucent Microelectronics) USS-312 USB Controller
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at 40800000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [50] Power Management version 2

Oddly enough, the PCCard gets detected as a USB hub. But not to worry, we just need to tell linux what it does. It will essentially operate as a dual port usbserial device.

/sbin/modprobe usbserial vendor=0x1199 product=0x0112

Take note of the vendor and product code which are specific to the AirCard 580. Next we need to create a USB device:

mknod /dev/ttyUSB0 c 188 0

Once we get hear, we need to create our ppp config: vi /etc/ppp/peers/lxevdo

-detach
ttyUSB0
115200
debug
user [email]user@telstra.pcpa[/email]ck
password telstra
defaultroute
usepeerdns
crtscts
lock
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/lxevdo_chat

Make sure you replace the 'user' and 'password; setting above with those supplied by your ISP. Once this is complete, we can setup our chat config which actually dial our number.

vi /etc/ppp/peers/lxevdo_chat

"" "AT"
OK "ATE0v1&F&D2&C1&C2S0=0"
OK "ATE0V1"
OK "ATS7=60"
OK "ATDT#777"

Once that is complete, you should be able to dialup your ppp config using this command:

pppd call 1xevdo


OK, here is what I got:
```

> cat /etc/ppp/peers/lxevdo
-detach
ttyUSB0
115200
debug
user IT # that's my username
password IT # my passwd
defaultroute
usepeerdns
crtscts
lock
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/lxevdo_chat

> /cat /etc/ppp/peers/lxevdo_chat
"" "AT"
OK "ATE0v1&F&D2&C1&C2S0=0"
OK "ATE0V1"
OK "ATS7=60"
OK "ATDT#777" # my 'tel. number' is #777

```

Now, let's see how it works:

```

> pppd call lxevdo
Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x472572b8> <pc
omp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <auth pap> <magic
0x78a1dcb9>]
sent [LCP ConfAck id=0x1 <asyncmap 0xa0000> <auth pap> <magic
0x78a1dcb9>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x472572b8> <pc
omp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x472572b8]
sent [PAP AuthReq id=0x1 user="IT" password=<hidden>]
rcvd [LCP EchoRep id=0x0 magic=0x78a1dcb9]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd
v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <
ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 195.128.18
2.5>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 195.128.18                                                                             2.5>]
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 7                                                                             8 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) re                                                                             ceived
rcvd [IPCP ConfNak id=0x1 <addr 78.111.180.238> <ms-dns1 195.1                                                                             28.182.40> <ms-dns3 195.128.182.41>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 78.111.180                                                                             .238> <ms-dns1 195.128.182.40> <ms-dns3 195.128.182.41>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 78.111.180                                                                             .238> <ms-dns1 195.128.182.40> <ms-dns3 195.128.182.41>]
Cannot determine ethernet address for proxy ARP
local  IP address 78.111.180.238
remote IP address 195.128.182.5
primary   DNS address 195.128.182.40
secondary DNS address 195.128.182.41
Script /etc/ppp/ip-up started (pid 7415)
Script /etc/ppp/ip-up finished (pid 7415), status = 0x0

```

it looks like I got in into network nicely,
BUT: as I try to open a web site:
konqueror - debian.org - oops, there is not any data transfer,
firefox - the likewise;
kopete: ICQ is fine, MSN is failure;
kmail, konqueror, firefox, dillo - it doesn't work :(;
ping, wget, apt-get install foo, links2 - it works!
galeon (attention, please!) - it works.

Has got anybody any comments to that?

Thanks in advance!

---

### Post by savsav on 2008-05-31
BUMP!

I would like to know the answer to this issue ...

which might be a "defaultroute" issue.

(I may be having a related problem)

---

### Post by AV1611 on 2008-06-01
> **savsav said:**
> BUMP!

I would like to know the answer to this issue ...

which might be a "defaultroute" issue.

(I may be having a related problem)

And it goes on down:
kmail - doesn't work;
evolution doesn't either;
thunderbird - works nicely.

---

### Post by kbuel on 2008-07-12
Hi,

one final step that I had to to do to get my aircard to work was after it connects like yours did, i had to copy /etc/ppp/resolv.conf to /etc/resov.conf

```
sudo cp /etc/ppp/resolv.conf /etc/resolv.conf
```


Hope this helps!

---

