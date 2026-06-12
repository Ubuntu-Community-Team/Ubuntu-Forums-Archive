---
title: "network is unavailable error"
date: 2005-06-15
forum: Networking &amp; Wireless
---

### Post by egon spengler on 2005-06-15
yesterday i installed ubuntu onto my downstairs computer, tested it out for a while, liked it and so installed it onto my other computer. the frst install went perfectly, the second less so.

for some reason my network connections won't work. the ethernet card seems to be recognised but can't connect to anything. i can't ping anything except localhost. i've looked through past threads but found nothing that helped. these are the steps i've done so far.

in the networkng menu when using DHCP default gateway won't show anythinig. it's possible to change it to eth0 but it won't stick. changing from DHCP to static lets the default gateway stick as eth0 but i'm still unable to connect to anything, the only change is that  am then able to ping myself at 10.0.0.8

route -n
my routing table is blank. ths seems like the most obvious cause of error but trying to add entries by ```
route add -net 0.0.0.0 gw 10.0.0.2 netmask 0.0.0.0 eth0
``` (which is one of the entries in the working downstairs pc) i get the response "network is unreachable"

/etc/network/nterfaces has no address, netmask or gateway. should it?

ifconfig shows no ipv4 address

/var/log/syslog shows a couple of errors stating 
1) No DHCP offers received
2) No working leases in persitent database - sleeping

/etc/resolv.conf has only the entry "nameserver 10.0.0.2" (the router address). should there be anything else there?

any help is much appreciated

---

### Post by jerrykenny on 2005-06-17
Are you using a router modem ?   maybe the router wont authorize your request - try changing your computers name . . . to the same as the upstairs one . . . 


Your etc/resolv.conf is OK I think

my  /etc/network/nterfaces has the line        iface eth0 inet dhcp

---

### Post by egon spengler on 2005-06-18
thanks for the suggestion jerry but it didn't make any difference.

i did eventually manage to enter info to the route table but still nothing worked (and the table kept getting overwritten seemingly at random). i realised that seeing as even with identical settings to the working pc this one wouldn't work it could well be a hardware problem. did a search for davicom 9102 cards and found this thread where someone else was having [similar problems](http://www.ubuntuforums.org/showthread.php?t=23380&highlight=davicom+dm9102) 

looks like this card just won't work with the current version of ubuntu. i tried rmmoding/modprobing both tulip and dmfe but no joy. i think i'll give simply mepis a try next (i'm filling with dread just at the prospect of having to use the k menu again)

edit:
now i think about it instead of mepis i might just use warty seeing as that seems to have no problems with my card. i know this isn't the right place for this but can anyone tell me what are the shortcomings of warty vs. hoary? i'm gonna go investigate this myself too but still, feedback would be appreciated

edit:

re-reading that thread made me realise that although i had tried unloading tulip and loading dmfe i hadn't tried adding dmfe to /etc/modules. i just did that and now everything works. thanks again jerry cos if you hadn't replied to this i most likely would have never looked at that other thread again.

now just to get the sound working  :)

---

### Post by alastair on 2005-06-18
Check the syslog for ethernet device probe/config e.g. look for "eth0" or device module load.

e.g.

e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex

Also :

ifconfig -a

Your /etc/network/interfaces should contain config for the ethernet device - but the device has to be functional.

---

