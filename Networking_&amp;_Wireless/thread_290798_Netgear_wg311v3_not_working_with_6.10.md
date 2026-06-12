---
title: "Netgear wg311v3 not working with 6.10"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by WhiteStool on 2006-11-01
I have a Netgear wg311 version three with a marvel chipset. It used to work with no problem with ndiswrapper, but when I installed edgy eft it stopped working.

All the drivers on the CD failed. Some versions of ndiswrapper don't do anything, and other versions give an insertion error. It worked fine in breezy and dapper, and under windows.

---

### Post by teumima on 2006-11-02
Man. sorry I can't solve your issue.

Can you help me though please.

How did you get WG311v3 to work on dapper?

I did everything according to [http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

I can search for networks, I find them. 

I use wpa-psk.

So I do this:  
wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -Dwext

Then it connects. I need to do this in root. But it just stays open, 
shouldn't it close? I can't believe that it's meant to be running in an open root
terminal.

Then I do [B]dhclient wlan1

And I get an IP, but i can't surf, i can't ping the router.

Can you help me with this?

Thanks

a.t.
[/B]

---

### Post by itly on 2006-11-14
Have 311v3 working with Edgy.
Upgraded from Dapper, error with Ndiswrapper.
Re-installed from latest Ndiswrapper from source.
Can get 311v3 to connect with wpa using KNetworkManager.
Works reasonably well, but a little buggy. Can surf etc. But leaving on overnight, it seems to lose the connection.
Hope this helps (follow the ndiswrapper wiki for install / re-install instructions)
Not sure how KNetworkManager works in Gnome.
Cheers.

---

### Post by teumima on 2006-11-14
Thanks man.

Will try it tonight.

---

