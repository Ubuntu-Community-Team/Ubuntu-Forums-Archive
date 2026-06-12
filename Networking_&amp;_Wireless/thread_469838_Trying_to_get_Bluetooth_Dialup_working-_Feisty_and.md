---
title: "Trying to get Bluetooth Dialup working- Feisty and Nokia E61"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Danni on 2007-06-10
I am trying to get Bluetooth Dialup to work with my Nokia E61 (SymbianOS S60 3rd Edition) and Kubuntu Feisty. As it's my only internet connection at the moment I'm currently using my Windows XP partition to use the internet. My network is T-Mobile (UK) and I've checked all the settings with them. 

I've followed all the instructions in [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup), including the bits just for T-Mobile, but it still won't work. I can sync well enough for file transfers.

My /var/log/syslog output looks like this:

```
Jun  4 20:50:00 Matilda modprobe: WARNING: Not loading blacklisted module ipv6
Jun  4 20:50:00 Matilda pppd[6278]: pppd 2.4.4 started by danni, uid 1000
Jun  4 20:50:03 Matilda hcid[5922]: link_key_request (sba=00:11:67:5E:B6:E4, dba=00:12:D2:28:56:8A)
Jun  4 20:50:04 Matilda chat[6281]: timeout set to 35 seconds
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nBUSY\r)
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nERROR\r)
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nNO ANSWER\r)
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nNO CARRIER\r)
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nNO DIALTONE\r)
Jun  4 20:50:04 Matilda chat[6281]: abort on (\nRINGING\r\n\r\nRINGING\r)
Jun  4 20:50:04 Matilda chat[6281]: send (^MAT^M)
Jun  4 20:50:04 Matilda chat[6281]: expect (OK)
Jun  4 20:50:05 Matilda chat[6281]: ^MAT^M^M
Jun  4 20:50:05 Matilda chat[6281]: OK
Jun  4 20:50:05 Matilda chat[6281]:  -- got it
Jun  4 20:50:05 Matilda chat[6281]: send (AT+CGDCONT=1,"IP","general.t-mobile.uk"^M)
Jun  4 20:50:05 Matilda chat[6281]: expect (OK)
Jun  4 20:50:05 Matilda chat[6281]: ^M
Jun  4 20:50:05 Matilda chat[6281]: AT+CGDCONT=1,"IP","general.t-mobile.uk"^M^M
Jun  4 20:50:05 Matilda chat[6281]: OK
Jun  4 20:50:05 Matilda chat[6281]:  -- got it
Jun  4 20:50:05 Matilda chat[6281]: send (ATD*99***1#^M)
Jun  4 20:50:05 Matilda chat[6281]: expect (CONNECT)
Jun  4 20:50:05 Matilda chat[6281]: ^M
Jun  4 20:50:07 Matilda chat[6281]: ATD*99***1#^M^M
Jun  4 20:50:07 Matilda chat[6281]: CONNECT
Jun  4 20:50:07 Matilda chat[6281]:  -- got it
Jun  4 20:50:07 Matilda chat[6281]: send (^M)
Jun  4 20:50:07 Matilda pppd[6278]: Serial connection established.
Jun  4 20:50:07 Matilda pppd[6278]: using channel 5
Jun  4 20:50:07 Matilda pppd[6278]: Using interface ppp0
Jun  4 20:50:07 Matilda pppd[6278]: Connect: ppp0 <--> /dev/rfcomm0
Jun  4 20:50:08 Matilda pppd[6278]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xa0acc91a> <pcomp> <accomp>]
Jun  4 20:50:08 Matilda pppd[6278]: rcvd [LCP ConfRej id=0x1 <magic 0xa0acc91a> <pcomp> <accomp>]
Jun  4 20:50:08 Matilda pppd[6278]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Jun  4 20:50:08 Matilda pppd[6278]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [LCP ConfReq id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Jun  4 20:50:10 Matilda pppd[6278]: sent [LCP ConfAck id=0x0 <auth pap> <mru 1500> <asyncmap 0xa0000>]
Jun  4 20:50:10 Matilda pppd[6278]: sent [LCP EchoReq id=0x0 magic=0x0]
Jun  4 20:50:10 Matilda pppd[6278]: sent [PAP AuthReq id=0x1 user="Matilda" password=<hidden>]
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [LCP EchoRep id=0x0 magic=0x0]
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [PAP AuthAck id=0x1 ""]
Jun  4 20:50:10 Matilda pppd[6278]: PAP authentication succeeded
Jun  4 20:50:10 Matilda pppd[6278]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jun  4 20:50:10 Matilda pppd[6278]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 192.168.1.7> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
Jun  4 20:50:10 Matilda pppd[6278]: sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jun  4 20:50:10 Matilda pppd[6278]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jun  4 20:50:10 Matilda pppd[6278]: rcvd [LCP TermReq id=0x1]
Jun  4 20:50:10 Matilda pppd[6278]: LCP terminated by peer
Jun  4 20:50:10 Matilda pppd[6278]: sent [LCP TermAck id=0x1]
Jun  4 20:50:13 Matilda pppd[6278]: Connection terminated.
Jun  4 20:50:14 Matilda pppd[6278]: Modem hangup
Jun  4 20:50:14 Matilda pppd[6278]: Exit.
danni@Matilda:~$                                
```

Anyone got any suggestions? (I know the log file is a few days old but I didn't see the point in copying it again when I get an identical message at the end.) I really want internet with Kubuntu again :)

---

### Post by ian on 2007-10-17
I had today the very same problem. Solution was not to use chat for the chatscript but wvdial with the following configuration:
--8<--
[Dialer radiolinja_usb_orange_spv]
#Modem = /dev/ttyUSB0
#Baud = 115200
Init1 = ATH
Init2 = ATE1
Init3 = AT+CGDCONT=1,"IP","internet.t-mobile"
#Init3 = AT+CGDCONT=1,"IP","internet","",0,0a
# Some phones like the NEC DB7000 don't like empty strings, so an address must
# be provided
#Init3 = AT+CGDCONT=1,"IP","internet","0.0.0.0",0,0
# Some phones don't like the quality of service parameters:
# Init4 = AT+CGQREQ=1,0,0,0,0,0
# Init5 = AT+CGQMIN=1,0,0,0,0,0
#Dial Command = ATD
#Phone = *99#
Phone = *99***1#
Username = t-mobile
Password = t-mobile
--8<--

---

### Post by PmDematagoda on 2007-10-17
You can try Blueman which worked perfectly with my K510i in connecting to the internet through the bluetooth, it can be found here:-

[http://walmis.balticum.lt/index.php?option=com_content&view=article&id=51&Itemid=56](http://walmis.balticum.lt/index.php?option=com_content&view=article&id=51&Itemid=56)

---

### Post by jago25_98 on 2007-12-02
With this info I fixed the same problem with kppp by leaving

Init1 as:
 `ATZ`

and changing

Init2 to just:

 `AT+CGDCONT=1,"IP"`

Hope this helps someone. I now notice that while I'm logged on (using username `3` and password `3` on Three UK pay as you go), I can't ping etc.

---

### Post by stevedasilva on 2008-01-16
I had the same problem:
> Jan 16 14:27:51 pluto pppd[14316]: Connect: ppp0 <--> /dev/rfcomm0
Jan 16 14:27:54 pluto pppd[14316]: PAP authentication succeeded
Jan 16 14:27:54 pluto pppd[14316]: LCP terminated by peer
Jan 16 14:27:57 pluto pppd[14316]: Connection terminated.
Jan 16 14:27:57 pluto pppd[14316]: Modem hangup

After some testing my ppp connection now works:
find out about your provider @ [Ross Barkman's GPRS Info Page]("http://www.taniwha.org.uk/gprs.html")
and note the APN
Enter your Provider in the AT+CGDCONT=1 string, like:
'AT+CGDCONT=1,"IP","your_provider_APN_Name"",,0,0'

everything else like mentioned in all the [HowTos]("http://http://www.google.de/search?hl=de&q=linux+mobile+ppp+E61+howto&btnG=Suche&meta=")

Hope that helps you to succeed...
Stefan

---

