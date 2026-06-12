---
title: "Help the Newbie with Wireless"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by catflea on 2005-10-17
Hi,

I have a BT Voyager 1020 wireless card on an USUS K8N-E Dulux M/board.   I can't get breezy to regognise the card.

How can I install it?   and how can I then configure the WEP key so I can access my broadband?

(i'm currently writing this in XP btw)

---

### Post by Swab on 2005-10-17
You'll need to find out which chipset your BT card uses.. then search for a solution from there...  or try NDISWRAPPER.. search around the forums for some info on that.

---

### Post by breakthestate on 2005-10-17
swab,

To find out your chipset:

"To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output.
 The PCI ID is third column or fourth in some distributions and of the form '104c:8400'."

(taken from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation))

Please don't follow the directions from the above website (b/c it might be possible that you do not need ndiswrapper).  Just paste the results relavant to your card from lspci and lspci -n in this forum.

---

### Post by catflea on 2005-10-18
ok,

This might sound really really silly,   but as I already said I am entirely new to Linux and Ubuntu.

How do I use those commands?    I assume I do it through terminal?

---

### Post by Swab on 2005-10-18
[QUOTE=catflea]ok,

This might sound really really silly,   but as I already said I am entirely new to Linux and Ubuntu.

How do I use those commands?    I assume I do it through terminal?[/QUOTE]

Yes, through the terminal.  I know everything seems really complicated right now, but if you stick with it you'll get there.  Welcome to Linux :)

---

