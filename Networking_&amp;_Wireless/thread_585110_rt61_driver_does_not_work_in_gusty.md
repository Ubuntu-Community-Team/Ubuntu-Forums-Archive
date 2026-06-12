---
title: "rt61 driver does not work in gusty"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by DrIdiot on 2007-10-21
Hi,

I just upgraded to Gutsy.  For some reason, I get internet for about a minute when I start up, and then it dies.  Nothing I do can revive it (I tried the network troubleshooting page on the forums, and /etc/init.d/networking restart).  The only thing that revives it is restarting the computer.

I am using a Edimax 7128G
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041)

Which uses the rt61 driver.  I did not have this problem in Feisty, although my network would occasionally drop, i could always revive it by /etc/init.d/network restart

does anyone know how to fix this, or does anyone know a network card that they know for sure works out of the box in Gutsy?  I've been looking at this one, for example:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127075](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127075)

Thanks,
-Harrison

---

### Post by owenl on 2007-10-22
I followed the instructions found here..

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)

and my network now works. 

Not you can't use network manager once you have applied this and you get a restricted driver warning.

---

### Post by DrIdiot on 2007-11-06
Thanks.  I also saw this:

[http://ubuntuforums.org/showthread.php?t=563547&highlight=rt61+driver+gutsy](http://ubuntuforums.org/showthread.php?t=563547&highlight=rt61+driver+gutsy)

However, the Edimax drivers can't be unzipped (the exes) like it says.  Is there a way for me to get the proper inf file?

Thanks.

---

### Post by DrIdiot on 2007-11-06
Also, do you know of a good wireless card that works well with Linux?  Er, how is madwifi support in Linux?  I might just get a new card.

Thanks,
-Harrison

---

### Post by TheWizzard on 2007-11-07
i have a linksys with rt61 chipset. worked out of the box in gutsy, although not perfect. i have to do a manual network restart. 

since you have a rt61, i'd try to get it working properly.

---

### Post by DrIdiot on 2007-11-12
what do you mean manual network restart?  like, sudo /etc/init.d/networking restart?

---

### Post by kevdog on 2007-11-12
Atheros/Madwifi compatible cards work great and truly work out of the box.  Be sure to consult the madwifi website to check what Atheros chipsets are supported by madwifi, since not all Atheros chipsets are.  For the others that are not, you will need ndiswraper.

For your rt61 card, you might want to try using the serial monkey drivers -- many have found them to work better.  They require some compiling however.  There are plenty of instructions in the forums.

---

### Post by wieman01 on 2007-11-12
> **TheWizzard said:**
> i have a linksys with rt61 chipset. worked out of the box in gutsy, although not perfect. i have to do a manual network restart. 

since you have a rt61, i'd try to get it working properly.
Try this & restart the PC:

Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

_Create startup script:_
> sudo gedit /etc/init.d/wireless-network.sh
_Add this line & save file:_
> /etc/init.d/networking restart
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/**[COLOR="Red"]S40[/COLOR]**wireless-network

---

### Post by DrIdiot on 2007-11-14
i get this when i try to launch /etc/init.d/networking restart:

harrison@hermitian:/etc/init.d$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ra0.pid with pid 16049
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/ra0/00:0e:2e:bd:1b:96
Sending on   LPF/ra0/00:0e:2e:bd:1b:96
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 18.7.21.127 port 67
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
There is already a pid file /var/run/dhclient.ra0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/ra0/00:0e:2e:bd:1b:96
Sending on   LPF/ra0/00:0e:2e:bd:1b:96
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

