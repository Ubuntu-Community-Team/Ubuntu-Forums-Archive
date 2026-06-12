---
title: "Finally got RT61wireless card working with WPA"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by casperlingus on 2007-04-15
I'm posting this because I searched these forums exhaustively for a solution to my problem and was not able to find it.  Eventually I found the solution in a non-ubuntu forum and it worked like a charm so I'm going to share it with you.  Dapper may be the only release that suffered from this problem, but there is useful information in here for anyone wanting to use WPA (use iwpriv).

I have an RT61 card for which the drivers appeared to already work.  I hear that the rt2600 drivers were broken in Edgy, but they definintely worked out of the box on Dapper.  There is a post somewhere that explains how to get those drivers working if they are not.

My problem was that NetworkManager was not acknowledging the existence of a wireless adapter.  No big deal, b/c I usually use ifconfig/iwconfig to connect--except that only works for WEP and we recently upgraded our security to WPA-PSK w/ TKIP.  I tried using wpa_supplicant, but for some reason I couldn't get that to work either.   I was totally SOL.

The solution was in the command **iwpriv**.  Apparently iwconfig provides a generic interface to your wireless adapter, while iwpriv deals w/ parameters and settings specific to your wireless driver.  Typing **iwpriv** (no parameters) gives you a list of commands available for each of your network interfaces.  Using **iwpriv ra0 get_site_survey** provided a nice alternative to **iwlist ra0 scan**.

Anyways, onto the goodies.  These are the commands I used to enable WPA via the shell:

```

sudo ifconfig ra0 down
sudo iwconfig ra0 essid [COLOR="Red"]NETWORKNAME[/COLOR]
sudo iwconfig ra0 mode managed
sudo ifconfig ra0 up
sudo iwpriv ra0 set Channel=6
sudo iwpriv ra0 set AuthMode=WPAPSK
sudo iwpriv ra0 set EncrypType=TKIP
sudo iwpriv ra0 set WPAPSK="[COLOR="Red"]my pre-shared key[/COLOR]"
sudo iwpriv ra0 set TxRate=0
sudo dhclient ra0

```

And that's it.  I wish I had known about iwpriv before.  I had seen a reference to it, but no good examples (if they're there and I missed them, don't grill me please--I'm trying to help).  I spent six hours playing with network manager and wpa_supplicant to no avail.   Oh well.

Any comments on iwpriv?  I'd like to know of any extra functionality I could pull out of it.

-Casper

---

### Post by Austin_KW on 2007-04-15
You do not have to run these commands from command line, the can be run when the interface comes up.

edit your /etc/network/interfaces and add your commands with "pre-up"
```

auto ra0
iface ra0 inet dhcp
   pre-up ifconfig ra0 down
   pre-up iwconfig ra0 essid NETWORKNAME
   pre-up iwconfig ra0 mode managed
   pre-up ifconfig ra0 up
   pre-up iwpriv ra0 set Channel=6
   pre-up iwpriv ra0 set AuthMode=WPAPSK
   pre-up iwpriv ra0 set EncrypType=TKIP
   pre-up iwpriv ra0 set WPAPSK="my pre-shared key"
   pre-up iwpriv ra0 set TxRate=0

```

---

