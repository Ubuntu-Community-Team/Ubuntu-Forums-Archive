---
title: "Ralink RT61 &amp; Feisty - Yet again."
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by stefan_dk on 2007-07-30
Dear ubuntu users.

I realize that this subject has been discussed in some earlier threads, however i have not been able to solve my specific problem reading these. However thanks to those quite detailed guides on the subject, they have tought me several things.

Anyway, my problem is setting the correct ESSID.

If my interface is up, the command [FONT="Courier New"]sudo iwconfig ra0 essid "blabla"[/FONT] does not do anything (as I have read it wouldn't).

On the other hand, if my interface is down I get the error that ESSID cannot be set, since the network is down: SET failed on device ra0 ; Network is down.

Accessing the network using windoze is not a problem.

My hardware is:
MEDION MD 96400 with a RaLink Wireless card rt61.
Linksys WRT54GL router.

I have tried the following in  the /etc/network/interfaces:
[FONT="Courier New"]
iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "blabla"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="A shared key"
        pre-up ifconfig ra0 up[/FONT]

and the rt61-1.1.0-b2 driver from serialmonkey.

I really hope someone can help, sorry if I did not provide that detailed info, I'm quite new to linux.

Regards
Stefan

---

