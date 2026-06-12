---
title: "881u on Hardy"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by cliffhaas on 2008-07-15
I would appreciate any assistance you can provide in making the 881u work on my Ubuntu Hardy laptop with att wireless service.
The card operates under windows but when I boot to Linux I can not navigate to a web page. The Data light on the device shows activity however.
I am running the 2.6.24 kernel. When I run modinfo from terminal I get;
modinfo sierra
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.2.10b
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd <klloyd@sierrawireless.com>
srcversion:     03D56421B29BA18078ECDC0
alias:          usb:v1199p0FFFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6469d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6468d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F30p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.24-19-generic SMP mod_unload 586
parm:           truinstall:TRU-Install support (bool)
parm:           nmea:NMEA streaming (bool)
*************************************
I have installed the pppd scripts from the sierra site as well and if I run pppd call gsm I get;
*************************************
root@cliff-laptop:~# pppd call gsm
Starting Sierra Wireless GSM connect script...

Setting the abort string

Initializing modem

Setting APN

Dialing...
Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4ec0025> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0xa806eb88> <pcomp> <accomp>]
sent [LCP ConfAck id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0xa806eb88> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4ec0025> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x4ec0025]
rcvd [LCP DiscReq id=0x4 magic=0xa806eb88]
rcvd [CHAP Challenge id=0x1 <20855e2d240f7698ae52dc6e5e56b842>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <388bd320ed6db9d84c0d094f2df8721e>, name = "ISP@CINGULARGPRS.COM"]
rcvd [LCP EchoRep id=0x0 magic=0xa806eb88 04 ec 00 25]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x5 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x2]
sent [IPCP ConfNak id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x3]
sent [IPCP ConfAck id=0x3]
rcvd [IPCP ConfNak id=0x4 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
sent [IPCP ConfReq id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
rcvd [IPCP ConfAck id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 166.217.49.71
remote IP address 10.64.64.64
primary   DNS address 209.183.33.23
secondary DNS address 209.183.33.23
Script /etc/ppp/ip-up started (pid 8838)
Script /etc/ppp/ip-up finished (pid 8838), status = 0x0
*******************************
If i use kppp the interface shows modem ready and then hangs. 

I am unsure as to where to go from here.
Thanks for anything that you guys can do to help.

---

### Post by gmanigault on 2008-08-20
First I think you are close.  I believe that the problem has to do with:

1.  AT&T pushing the incorrect DNS in their script. 
See first red line in snippet

2.  Providing a bad remote IP address that will not allow you to ping anything. 

Couple of questions.  How did you get the following ip address shown in you script?


209.183.33.23     NSlookup shows it as schinetdns.mycingular.net

Once you connect are you able to ping anything (ie. [www.google.com](www.google.com)) etc?  

I am planning on hooking up my windows box see what info I can get from it and hopefully it will help fix this problem.  If anyone hears or discovers anything let me know.  I think we are close. 

Gary

=====[snippet]


[COLOR="Red"]sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>][/COLOR]rcvd [IPCP ConfReq id=0x3]
sent [IPCP ConfAck id=0x3]
rcvd [IPCP ConfNak id=0x4 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
sent [IPCP ConfReq id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
rcvd [IPCP ConfAck id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 166.217.49.71
[COLOR="red"]remote IP address 10.64.64.64[/COLOR]
primary   DNS address 209.183.33.23
secondary DNS address 209.183.33.23

=====[snippet]







> **cliffhaas said:**
> I would appreciate any assistance you can provide in making the 881u work on my Ubuntu Hardy laptop with att wireless service.
The card operates under windows but when I boot to Linux I can not navigate to a web page. The Data light on the device shows activity however.
I am running the 2.6.24 kernel. When I run modinfo from terminal I get;
modinfo sierra
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.2.10b
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd <klloyd@sierrawireless.com>
srcversion:     03D56421B29BA18078ECDC0
alias:          usb:v1199p0FFFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6469d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6468d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F30p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.24-19-generic SMP mod_unload 586
parm:           truinstall:TRU-Install support (bool)
parm:           nmea:NMEA streaming (bool)
*************************************
I have installed the pppd scripts from the sierra site as well and if I run pppd call gsm I get;
*************************************
root@cliff-laptop:~# pppd call gsm
Starting Sierra Wireless GSM connect script...

Setting the abort string

Initializing modem

Setting APN

Dialing...
Serial connection established.
using channel 5
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x4ec0025> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0xa806eb88> <pcomp> <accomp>]
sent [LCP ConfAck id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0xa806eb88> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x4ec0025> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x4ec0025]
rcvd [LCP DiscReq id=0x4 magic=0xa806eb88]
rcvd [CHAP Challenge id=0x1 <20855e2d240f7698ae52dc6e5e56b842>, name = "UMTS_CHAP_SRVR"]
sent [CHAP Response id=0x1 <388bd320ed6db9d84c0d094f2df8721e>, name = "ISP@CINGULARGPRS.COM"]
rcvd [LCP EchoRep id=0x0 magic=0xa806eb88 04 ec 00 25]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0x5 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x2]
sent [IPCP ConfNak id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x3 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x4 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfReq id=0x3]
sent [IPCP ConfAck id=0x3]
rcvd [IPCP ConfNak id=0x4 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
sent [IPCP ConfReq id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
rcvd [IPCP ConfAck id=0x5 <addr 166.217.49.71> <ms-dns1 209.183.33.23> <ms-dns3 209.183.33.23>]
Could not determine remote IP address: defaulting to 10.64.64.64
Cannot determine ethernet address for proxy ARP
local  IP address 166.217.49.71
remote IP address 10.64.64.64
primary   DNS address 209.183.33.23
secondary DNS address 209.183.33.23
Script /etc/ppp/ip-up started (pid 8838)
Script /etc/ppp/ip-up finished (pid 8838), status = 0x0
*******************************
If i use kppp the interface shows modem ready and then hangs. 

I am unsure as to where to go from here.
Thanks for anything that you guys can do to help.

---

