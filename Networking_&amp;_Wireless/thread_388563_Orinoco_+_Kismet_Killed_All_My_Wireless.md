---
title: "Orinoco + Kismet Killed All My Wireless"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by typ3 on 2007-03-19
This is my first post, so go easy on me:

My wireless is now dead-completely and I need it for work!

I'm running Edgy Eft will all the latest updates. It installed perfectly and my Orinoco card in my Dell D400 worked perfectly out of the box.

I wanted to try kismet and wireshark, so I eventually got the orinoco card working with kismet according to the instructions I found on these very forums. Kismet was working perfectly, and so was wireshark.

Today, I put my laptop to sleep after (or maybe while) using wireshark (I think). Now my wireless doesn't work in anything except kismet.

Sometimes I get a symbol with a no entry sign on my net status but usually I just get a network status indicator but I can't get any connections. Wireshark says it can't get a stream from my device. 

sometimes iwpriv shows the card, sometimes it doesn't. 

I've tried running sudo iwpriv eth1 force_reset, which worked when my card won't leave monitor mode after kismet, but it doesn't work.

PLEASE HELP ME! I NEED TEH INTERNETS!!!111

Thanks,

Brandon

---

### Post by chili555 on 2007-03-19
Is your card still in monitor mode? ```
sudo iwconfig
```If you see ```
IEEE 802.11b  ESSID:"GBR1"  Nickname:"Prism  I"
          Mode:**Monitor**  Frequency:2.422 GHz  Access Point: **Not-Associated**   
          Bit Rate:1 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:keysecret
```Then your card is not coming out of monitor mode as Kismet quits. Not really a problem; many cards have problems. Issue a command:```
sudo iwconfig <your_interface> mode managed
```and you should be all good.

---

### Post by typ3 on 2007-03-19
It's still dead and I know that they're are at least 3 open APs in my area.

What's going on!!!! I don't want to go to windows!

Brandon

---

### Post by chili555 on 2007-03-19
Could I please see:```
lsmod | grep prism
lsmod | grep orinoco
lsmod | grep hostap
```Thanks.

---

### Post by typ3 on 2007-03-19
lsmod | grep orinoco

> 
orinoco_cs              17412    1       
orinoco                     47760    1  orinoco_cs
hermes                        9984    2   orinoco_cs, orinoco
pcmcia                     40380     1   orinoco_cs
pcmcia_core            43924    4   orinoco_cs, pcmcia, yenta socket,rsrc_nonstatic
 

the other two produced no results

Thanks,

Brandon

---

### Post by chili555 on 2007-03-19
Looks good so far. Have you tried pulling the card out and reinserting it? Reboot? ```
sudo dhclient eth1
```If all these steps are not productive, let's step back a bit and look at basic settings:```
sudo iwconfig eth1
sudo iwlist eth1 scan
cat /etc/network/interfaces
```Be sure to obscure any encryption codes. We'll get it!

---

### Post by typ3 on 2007-03-19
So the dhclient produced "No DHCPOFFERS" received. No working leases in persistent database.

the iwconfig eth1 produces (I have to type this all out)

IEEE 802.11DS
ESSID: ""
Nickname: "HERMES I"
Mode: Managed
Freq: 2.457 GHz
AP: None
Bit Rate: 11Mb/s
Tx-Power=15 dBm
Sensitivity: 1/3
Retry limit: 4
RTS thr: off
Fragment thr: off
Encryption key: off
Power Management: off
Link Quality=0/92
Signal level=134/135
Noise level=134/135

and so on...

that's all

Thanks,

Brandon

---

### Post by typ3 on 2007-03-19
iwlist eth1 scan

produces

eth1  Failed to read scan data: No data available

---

