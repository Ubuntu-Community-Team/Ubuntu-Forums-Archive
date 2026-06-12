---
title: "Atheros AR242x 802.11abg (Can't find the Wlan.)"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by venjog on 2008-04-30
Hello, This is my first time ever having problems with my Wlan I'm new to Ubuntu and I proberly don't give you enough informations.. but please help me.

I have "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) "
(I think, how can I check it exactly?)

My problem is that I can't see my "wireless connection" but I do have a little amount of wireless connection settings.

My driver is in the restricted driver section part.

I actually made my sound go away in the try fixing this... pretty strange:O
I have attached some pictures of my problem.. I guess that the pictures tells the problem better than I can write:)


Sincerely 
Martin Nielsen.

ps. Just tell me how to get more information if its needed

---

### Post by muecker on 2008-04-30
You need to double-check exactly what card you really have.  Ubuntu reported mine as an AR242x but it was really an AR5007EG and I could not get Hardy's madwifi driver to work with it.  I did a search on the Ubuntu forums for that card and found a link to a specific version of the madwifi drivers.  After installing it, I got the card working but it has to be recompiled every time there is a kernel update.

The first of these two links is the madwifi site for Atheros cards.  The second one tells how to get this specific card to work.  It isn't the page I found but should work anyway.  If it doesn't work for you, search the Ubuntu forums and you should find the same link I found.

[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

