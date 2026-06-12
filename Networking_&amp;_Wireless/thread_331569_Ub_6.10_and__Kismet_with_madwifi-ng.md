---
title: "Ub 6.10 and  Kismet with madwifi-ng"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by scottylans on 2007-01-04
Hi guys,

I need some help!
i followed this guide.
[http://huwico.hu/~litch/wep/ubuntu_wep_hack.pdf](http://huwico.hu/~litch/wep/ubuntu_wep_hack.pdf)

my aircrack and aireplay are working fine but now kismet is broken.

I don't know what sources to try, I just want it to work :evil: ](*,) 
I swear it all worked fine in 6.06, I should never have got 6.10! :( 

I've tried the following sources
source=madwifi_ag,wifi0,madwifi
source=ath0,atheros,ath0
source=wifi0,atheros,wifi0

and several combinations of all those, I'm a bit of a noob :(

I don't understand what happened to the  atheros drivers in the latest release? In 6.06 I could install it fresh, install kismet and aircrack and it just WORKED?

Can someone tell me how to fix kismet, if at all?

P.S the error is.

> 
user@laptop:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
WARNING: wifi0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: GetIFFlags: interface wifi0: No such device
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...
user@laptop:~$ 


P.S Just to re-state, I no longer have the same drivers that most of you 6.10 owners have, I have the ones mentioned in that PDF link up the top, which should (?) allow me to get packet injection working (I think! :-? )
I really would appreciate it, sorry about the frustration but I've had wireless issues with Ubuntu since 5.04!

---

### Post by netztier on 2007-01-05
> **scottylans said:**
> 
source=madwifi_ag,wifi0,madwifi
source=ath0,atheros,ath0
source=wifi0,atheros,wifi0

and several combinations of all those, I'm a bit of a noob :(


In Ubuntu 6.10, I use kismet with this source line and it works perfectly well:
```
source=madwifi_g,wifi0,HP-WLAN400
```
> **scottylans said:**
> 
I don't understand what happened to the  atheros drivers in the latest release? In 6.06 I could install it fresh, install kismet and aircrack and it just WORKED?

The thing is that with 6.06 to 6.10, Ubuntu went from madwifi to madwifi-ng, which brought the separate wifi0 interface for monitoring along.

When I upgraded to 6.10, all I had to change was the interface in [FONT="Courier New"]**/etc/kismet/kismet.conf**[/FONT] from **[COLOR="DarkRed"]ath0[/COLOR]** to **[COLOR="Green"]wifi0[/COLOR]**. However what you did is replacing the madwifi-ng kernel module with some "madwifi-old" from CVS.  So your source line should be something like:

```
source=madwifi_ag,**ath0**,<arbitrary name visible in kismet>
```
Since your madwifi module seems nonstandard, a possible alternative could be: [LIST]
[*]run the **[FONT="Courier New"]wlanconfig ath1 create... [/FONT]**command from that HOWTO you posted
[*]run the [FONT="Courier New"]**ifconfig ath1 up**[/FONT] command from the HOWTO you posted
[*]then start kismet using a source line that refers to **ath1** instead of ath0 or wifi0
[/LIST]

The syntax of the source command is explained in kismet.conf:

```
...
# Sources are defined as:
# source=sourcetype,interface, name[,initialchannel]
...
```

I'm not mistaken, there's even a few examples in kismet.conf. Furthermore,  as mentionned in the same place, [FONT="Courier New"]**/usr/share/doc/kismet/README.gz**[/FONT] lists exactly what source definitions are needed for which kind of WLAN NIC, and which interface string should be used in the sources definition. You'll find all the information there.

best regards

Marc

---

