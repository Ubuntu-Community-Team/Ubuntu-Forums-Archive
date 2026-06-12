---
title: "Help with Hawking HWPG-1 PCI adapter"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by waltn on 2006-07-22
I am using the subject Hawking wireless network card in a dual-boot Ubuntu 6.06/WinXP desktop. The adapter has been working fine in WinXP; it uses the Ralink RT2500 chip which is supposed to be supported by the Ubuntu kernel. The situation is as follows:
[LIST=1]
[*]When I use the System>Administration>Networking tool to activate the connection, interface ra0 is there, unconfigured
[*]I select Properties then Enable the connection, then click the drop-down on the ESSID field; the ESSIDs of the two networks accessible in the area appear and I select mine. (This indicates to me that the card is working to the extent that is scans for networks and correctly reports their ESSIDs)
[*]I select Hex for the WEP key type and enter the key as 10 characters. I have tried formats XXXXXXXXXX, XX XX XX XX XX, and XXXX-XXXX-XX
[*]I request DHCP configuration and click OK
[*]At the main screen I click Activate; the Activating interface "ra0" message box appears and the progress bar cycles for awhile. When it stops, the wireless connection is shown as active (it isn't).
[*]Returning to the Properties box shows that there is no IP address, mask or gateway.
[/LIST]
I have read the wiki and all of the wireless docs on this site I can find, and have tried nearly everything there to no avail.

The activity light on the adapter is solid green; the TX/RX light blinks amber occasionally.

It acts as though there is a problem negotiating the connection between the access point and the computer. I have seen this in the past when one expects a key length different from the other. The windows machine(s) all use the XXXXXXXXXX hex key format if this helps.

Any help is gratefully appreciated!

Walt Novinger
[email]walt.novinger@gmail.com[/email]

---

### Post by dshuck on 2006-09-15
I just put the same card in my son's computer running 6.06.1 and had the exact same results.  Did you ever find a solution?

Thanks!

---

