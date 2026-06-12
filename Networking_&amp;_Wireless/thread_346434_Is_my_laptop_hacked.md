---
title: "Is my laptop hacked?"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by erzhong on 2007-01-25
My wireless card is working, but firefox cannot even link to google for a long time. So I started firestarter. The result is shown in the photo attached. There are two connections shown, from a single source to two difference destinies. None of these IPs belongs to my laptop. 

The wireless card of my laptop is a Atheros Communications, Inc. AR5212 802.11abg card, shown as ath0 in firestarter. I am wondering what the wifi0 is. It seems like it corresponds to wireless cards, but the amount of  traffic through wifi0 is not the same as the amount through ath0. 

Is my laptop hacked?

---

### Post by kerry_s on 2007-01-25
If there on your network, try putting that address in firefox address bar. I just get denied when i enter them because i'm not on your network. My guess is your isp is spying on you(joke :D ) . Here's the info i get from whois->

% Information related to '213.160.98.128 - 213.160.98.191'

inetnum:        213.160.98.128 - 213.160.98.191
netname:        TELECOMPLETE-AKHEX2
descr:          Akamai Technology
country:        GB
admin-c:        TNOC8-RIPE
tech-c:         TNOC8-RIPE
status:         ASSIGNED PA
mnt-by:         TELECOMPLETE-MNT
mnt-lower:      TELECOMPLETE-MNT
mnt-routes:     TELECOMPLETE-MNT
source:         RIPE # Filtered

role:           Telecomplete Network Operations Centre
address:        Telecomplete Ltd
address:        Kilburn House
address:        Lloyd Street North
address:        Manchester
address:        M15 6SE
phone:          +44 870 833 2510
fax-no:         +44 870 833 2511
remarks:        trouble:      [email]abuse@telecomplete.co.uk[/email]
admin-c:        SJW2-RIPE
admin-c:        DH1368-RIPE
tech-c:         SJW2-RIPE
tech-c:         DH1368-RIPE
nic-hdl:        TNOC8-RIPE
mnt-by:         TELECOMPLETE-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@telecomplete.co.uk[/email]

% Information related to '213.160.96.0/19AS6320'

route:        213.160.96.0/19
descr:        Telecomplete Ltd
origin:       AS6320
mnt-by:       TELECOMPLETE-MNT
source:       RIPE # Filtered

whois 63.146.109.204
Qwest Communications Corporation QWEST-INET-8 (NET-63-144-0-0-1) 
                                  63.144.0.0 - 63.151.255.255
Jupitermedia Corp. QWEST-EWR-JUPIT3 (NET-63-146-109-128-1) 
                                  63.146.109.128 - 63.146.109.255
Qwest Cybercenters QWEST-63-146-96 (NET-63-146-96-0-1) 
                                  63.146.96.0 - 63.146.127.255

# ARIN WHOIS database, last updated 2007-01-24 20:10
# Enter ? for additional hints on searching ARIN's WHOIS database.

---

### Post by tturrisi on 2007-01-25
wifi0 is  "virtual" adapter created by the madwifi driver for atheros chipset devices.  That's how the driver works in linux.

Your isp is not spying on you.  How? Not possible.  You opened your browser and it tries to connect to a homepage or to some site because you clicked a link or a bookmark.  The browser sends a request and will keep the socket open for a default period of time.  That's why you see the outbound connection (even though there is no connection, it's an attempted connection).

Reboot.
Open a term & type:
netstat -a
Open a browser.
do another netstat
compare the two.

---

### Post by kerry_s on 2007-01-25
> Your isp is not spying on you. How?

That was meant to be a joke, but i was doing several things and didn't write it right. :D

---

### Post by tturrisi on 2007-01-26
:d

---

### Post by erzhong on 2007-01-26
Thank you all for your answers :D 

I still have two questions: 
Why the amount of traffic of wifi0 is much more than that of ath0 is wifi0? 
Should I use wifi0 or ath0 as the network device in firestarter?

---

### Post by tturrisi on 2007-01-26
> **erzhong said:**
> Thank you all for your answers :D 

I still have two questions: 
Why the amount of traffic of wifi0 is much more than that of ath0 is wifi0? 
Should I use wifi0 or ath0 as the network device in firestarter?
1. it's the same traffic
2. ath0

---

