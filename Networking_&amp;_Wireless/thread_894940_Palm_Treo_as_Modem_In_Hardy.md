---
title: "Palm Treo as Modem In Hardy"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by natrone on 2008-08-19
I have been using USB Modem for a couple of months now to connect my treo as a PPP modem in 8.04.  I hadn't used it for a couple of weeks and plugged it into my HP Pavilion laptop ran the script to connect it appears to run as normal but the computer does not connect.  I tried it on my older Dell laptop and it works fine.  The other day I could not get the Dell to work either but for some reason it worked today.  I even went as far to boot into windows and try it, works fine there as well.  Following is the instructions from Mobile Stream to make USB Modem work in Linux.  I have Sprint therefore I use the EvDO script:

Copy either ppp-script-edge-template (for GSM GPRS/EDGE networks) or ppp-script-evdo-
template (for CDMA 1xRTT or EvDO networks) file from the USB Modem distribution to
/etc/ppp/peers/ppp-script-treo (you may need to create the path manually), replacing the
USERNAME and APN (for GSM only) words with the correct values.

To connect your Treo using a USB cable to the Linux computer, start the USB Modem application on
the Treo, set the Connectivity method to USB and enable the modem mode. Now type in the
command prompt:
       bash-2.05# pppd /dev/ttyACM0 call ppp-script-treo

This is the output of terminal on the HP which is currently not working (I do not notice the difference between output on the working computers and the non working):

send (AT&F0E0V1S0=0^M)
expect (OK)
^M
OK
 -- got it

send (ATD#777^M)
expect (CONNECT)
^M
^M
CONNECT
 -- got it

Serial connection established.
using channel 1
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd697a4fa>]
rcvd [LCP ConfReq id=0x38 <asyncmap 0x0> <magic 0x540e3cb2> <pcomp> <accomp>]
sent [LCP ConfRej id=0x38 <pcomp> <accomp>]
rcvd [LCP ConfNak id=0x1 <pcomp> <accomp>]
sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xd697a4fa>]
rcvd [LCP ConfReq id=0x39 <asyncmap 0x0> <magic 0x540e3cb2>]
sent [LCP ConfAck id=0x39 <asyncmap 0x0> <magic 0x540e3cb2>]
rcvd [LCP ConfNak id=0x2 <pcomp> <accomp>]
sent [LCP ConfReq id=0x3 <asyncmap 0x0> <magic 0xd697a4fa>]
rcvd [LCP ConfNak id=0x3 <pcomp> <accomp>]
sent [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0xd697a4fa>]
rcvd [LCP ConfNak id=0x4 <pcomp> <accomp>]
sent [LCP ConfReq id=0x5 <asyncmap 0x0> <magic 0xd697a4fa>]
rcvd [LCP ConfAck id=0x5 <asyncmap 0x0> <magic 0xd697a4fa>]
sent [LCP EchoReq id=0x0 magic=0xd697a4fa]
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15>]
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP DiscReq id=0x3a magic=0x540e3cb2]
rcvd [LCP EchoRep id=0x0 magic=0x540e3cb2 d6 97 a4 fa]
rcvd [IPCP ConfReq id=0x13 <addr 68.28.241.69>]
sent [IPCP ConfAck id=0x13 <addr 68.28.241.69>]
rcvd [LCP ProtRej id=0x3b 80 fd 01 01 00 0c 1a 04 78 00 18 04 78 00]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <addr 70.11.18.87> <ms-dns1 68.28.242.91> <ms-dns3 68.28.250.92>]
sent [IPCP ConfReq id=0x2 <addr 70.11.18.87> <ms-dns1 68.28.242.91> <ms-dns3 68.28.250.92>]
rcvd [IPCP ConfAck id=0x2 <addr 70.11.18.87> <ms-dns1 68.28.242.91> <ms-dns3 68.28.250.92>]
not replacing existing default route via 192.168.2.1
Cannot determine ethernet address for proxy ARP
local  IP address 70.11.18.87
remote IP address 68.28.241.69
primary   DNS address 68.28.242.91
secondary DNS address 68.28.250.92

---

### Post by natrone on 2008-09-12
Apparently this is working again.  Really don't know how I did it other than a clean install.  

Thanks

---

