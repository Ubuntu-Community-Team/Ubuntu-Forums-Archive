---
title: "Dlink Dwl-660 and troubles with the ap"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by Noiano on 2007-04-15
Hello everybody
I have been given a dlink dwl-660 pcmcia wireless card. It has a orinoco chipset as I can see from dmesg:

```
 pccard: PCMCIA card inserted into slot 0
[17180106.248000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[17180106.252000] pcmcia: registering new device pcmcia0.0
[17180106.868000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17180106.876000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17180106.976000] eth1: Hardware identity 0001:0004:0005:0000
[17180106.976000] eth1: Station identity  001f:0001:0008:000a
[17180106.976000] eth1: Firmware determined as Lucent/Agere 8.10
[17180106.976000] eth1: Ad-hoc demo mode supported
[17180106.976000] eth1: IEEE standard IBSS ad-hoc mode supported
[17180106.976000] eth1: WEP supported, 104-bit key
[17180106.976000] eth1: MAC address 00:05:5D:25:35:C6
[17180106.976000] eth1: Station name "HERMES I"
[17180106.976000] eth1: ready
[17180106.992000] eth1: index 0x01: , irq 3, io 0x0100-0x013f
[17180107.244000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

The module loaded into the kernel (concerning orinoco) are

```
orinoco_cs             17540  1 
orinoco                45076  1 orinoco_cs
hermes                  9472  2 orinoco_cs,orinoco
pcmcia                 40380  1 orinoco_cs
pcmcia_core            43924  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

```

The problem is that, even though I can see the ap and I can get associated to it, I cannot send/receive data

iwconfig eth1 says:

```

          eth1      IEEE 802.11b  ESSID:"crypto"  Nickname:"noialap"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:C1:0D:6B:94   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/92  Signal level=-49 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The weird thing is that the arp table is mysteriously empty (after having shutdown the eth0 which is lan)

So i cannot send/receive data, the dhcpclient cannot talk with the dhcpserver installed on the ap, ping says "operation not permitted" and ssh says "no route to host"

What can I do? Should you require more info just ask

---

### Post by chili555 on 2007-04-16
Are you trying to connect when the LAN cable is connected and has an IP address? It probably will not work. I suggest disconnecting the wire and restarting networking: *sudo /etc/init.d/networking restart* and see if you get an IP address.

I assume all encryption details are double-checked and correct?

---

### Post by Noiano on 2007-04-16
> **chili555 said:**
> Are you trying to connect when the LAN cable is connected and has an IP address? It probably will not work. I suggest disconnecting the wire and restarting networking: *sudo /etc/init.d/networking restart* and see if you get an IP address.

I assume all encryption details are double-checked and correct?

The encryption details are triple-checked and are more than correct :wink: ...concerning your advice I have tried...nothing...I am very sad because I am leaving within 2 weeks and I would like to call family through voip...

---

### Post by chili555 on 2007-04-16
You say:> I can see the ap and I can get associated to it, I cannot send/receive dataNot sure I understand. If you are not given an IP address by the DHCP server, then I doubt you are really "associated." You may be flirting but you aren't kissing. It should be as easy as:```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig key <wep_key>
sudo dhclient eth1
```Sometimes cards respond if you suffix the key with 'open' or 'restricted,' thus:```
sudo iwconfig eth1 key 0123456789 open
```

If your key is ASCII instead of hex, prepend it with s:.

I would confirm the ESSID with:```
sudo iwlist eth1 scan
```It may take a few tries.

Hang in there, we'll get it.

---

### Post by Noiano on 2007-04-17
> > **chili555 said:**
> You say:Not sure I understand. If you are not given an IP address by the DHCP server, then I doubt you are really "associated." You may be flirting but you aren't kissing. 


I said I was associated not only because I can see AP' mac address but also because I can see my pccard's mac from the router control panel as shown in the picture attached:


[QUOTE]
It should be as easy as:```
sudo iwconfig eth1 essid <your_essid>
sudo iwconfig key <wep_key>
sudo dhclient eth1
```Sometimes cards respond if you suffix the key with 'open' or 'restricted,' thus:```
sudo iwconfig eth1 key 0123456789 open
```

If your key is ASCII instead of hex, prepend it with s:.

I would confirm the ESSID with:```
sudo iwlist eth1 scan
```

I disabled the encryption but nothing works...the dhcp client always says: NO DHCPOFFERS RECEIVED 

> 
It may take a few tries.

Hang in there, we'll get it.

I tried 5 times, should be enough to understand that the problem isn't that...don't you agree? :wink

---

### Post by chili555 on 2007-04-17
This:> It may take a few trieshas to do with many, perhaps most cards, having a default scan time of two seconds. Depending on what channel the card is on at the moment you press Enter, two seconds may not be enough time for it to scan 11 or 13 channels, depending on your location. So, it may take a few tries to get a scan result.

It had nothing to do with how long it might take to understand the problem.

---

### Post by Noiano on 2007-04-20
The mystery is unveiled: there was a firewall misconfiguration which caused all packets to be dropped!

---

