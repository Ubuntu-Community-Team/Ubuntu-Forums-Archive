---
title: "WEP install failure"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by JimS on 2007-01-01
...
Can't install WEP.

Toshiba Satellite M35X-S161 notebook
w/ Atheros AR5212 802.11abg NIC.
Dapper.
Linsys WRT54G router - new.

All PCs (3) run well wired.
The notebook runs well wirelessly w/o security.
When I was running WinXP and Netgear router, WEP worked on notebook.
I see no way to setup WPA, only WEP on the notebook.

I go to Network Setting, Internet Properties (ath0).
I enter Key 1 in hex - OK - It takes over a minute to finish - much too long IMO.
I try to get to internet - NOGO.

While I would prefer WPA, WEP will do.
Maybe the router's security is broke - new, untested router.
Any ideas??

One thought - Maybe since my notebook is the only wireless connection,
I could restrict connection to the notebook's MAC address and not use WEP/WPA.
What do you think?

I have to go now - no time to experiment.
Hope to see your responses.
...

---

### Post by haiku99 on 2007-01-01
try manually editing your /etc/interface/networks file and reboot, that should do it.  It may also be necessary to run **sudo ifdown ath0** follwed by **sudo ifup ath0** the first time you connect,  the connection should be automatic following bootup after that .  FWIW my interfaces file looks like this and the eth0 entry is for a WEP connection

bill@bill-laptop:~$ cat /etc/network/interfaces


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
wireless-essid Freenet


auto wlan0
iface wlan0 inet dhcp
wireless-essid Ignatius
wireless-key 1234567890

---

### Post by JimS on 2007-01-01
...
Thanks for your reply.
I will give it a look later.

I disabled the security mode and am using
a MAC filter.  Connection successful, but
I'm not sure how secure I am.

Got to go again.
Thanks.
...

---

### Post by fredj on 2007-01-01
Not secure at all. Anyone who is within range of your unsecured wireless network can
use a network sniffer to see what you are sending over the internet and the network.
At the very least they will be able to connect to your network and use your internet
connection using mac spoofing. 
Since your card works without security you should be able to get it to work either with
WEP or WPA. We need more details about your WEP failure to help you.

---

### Post by elses_pels on 2007-06-02
hi guys, 
I have a similar problem. any more on this? 
router: netgear
wireless card: linsys 
toshiba portege 7200 (v old. but I am stubborn) 
again. i could connect wireless and it all works until I ty to set up WEP. then ....nothing. 
if this thread is alive I can follow up 
regards 
Marcelo

---

