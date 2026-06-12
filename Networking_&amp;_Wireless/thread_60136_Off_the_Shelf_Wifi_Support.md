---
title: "Off the Shelf Wifi Support"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by faddat on 2005-08-26
Could anyone point me to PCI or USB wifi products that will work with Ubuntu right off the shelf?  I am travelling to university tomorrow and I'd like to know that my Ubuntu system will be ready to rock with Wifi as I'll be living near Starbucks :).

Thanks!

-Jake

---

### Post by Juergen on 2005-08-26
I have a 'levelone WNC-0300' running fine, but you should get the same results with all cards that are supported by [madwifi](http://madwifi.sourceforge.net/dokuwiki/doku.php)
Look at the compatibility list (and the Ubuntu-entry ;-)).

If you want to use WPA (you should), you need to edit some files, I didn't find a GUI for this. 
But all info should be in the docs for 'wpa_supplicant' (its in the Ubuntu-repositories) or here in the forums ;-)

Other people seem to get the 'ndis-wrapper' to work, but for me this seems to be more like a 'workaround' - but if you want, search for it in the forums (or google)...

---

### Post by npaladin2000 on 2005-08-26
There is no GUI for wpa_supplicant.  I'm considering writing/converting one, but that depends on how fast I learn enough useful Python to be able to do it.

Anyway, an Aethros-based card is best (D-Link uses Aethros pretty reliably), Next up would be an Intel-chip based wifi card.  They'd probably actually be BETTER supported, but I don't think anyone uses the Intel chips to make USB or PC cards, do they?

---

### Post by bored2k on 2005-08-26
If you find out what card do the Toshiba Qosmio include, I know those work basically out of the box (my neighboor just tried it yesterday).

---

### Post by numberexhaust on 2005-08-27
I have a netgear wg511t card (works with g networks) and it runs... but with a few minor troubles (sometimes disconnects, etc.)  I'm using ndiswrapper right now to make it work but apparently it works with madwifi too.  My recommendation is to get a card like this rather than an older one because Breezy Badger and other later releases will have better support for cards (I hope), so you might as well go for the better card.

---

