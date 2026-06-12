---
title: "Attempted Ubuntu 6.06,7.04,6.10 aswell as Sabayon to install wireless"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by Eikcuhc on 2007-05-31
Hello, i have attempted to use all of the above to install the WUSB54G 802.11g Linksys Wireless for the internet but i have not been able to install in any of these OSes. I am currently on Kubuntu. help please!

---

### Post by tturrisi on 2007-05-31
Depending on what version of that usb adapter you may have to use ndiswrapper for it.  The version # is on the bottom side of it.  Find the version & do a forum search for wusb54g.

---

### Post by Eikcuhc on 2007-05-31
i forgot to mention that it was v1(since it does not show any version number i guess thats what it is) and i have searched here and linuxforums.org or com (forgot which it is) and i have done ndiswrapper and rt2570 for all of the OSes except Sabayon and i restart it and everything but nothing!

---

### Post by tturrisi on 2007-05-31
The version 1 has a prism chipset.
[http://linux-wless.passys.nl/query_part.php?brandname=Linksys](http://linux-wless.passys.nl/query_part.php?brandname=Linksys)
[http://prism54.org/](http://prism54.org/)
or see [http://ubuntuforums.org/showthread.php?p=2557642](http://ubuntuforums.org/showthread.php?p=2557642)

---

### Post by Eikcuhc on 2007-05-31
which one of the prism54 driver do i use? and do i just use ndiswrapper to install? do i blacklist what was on the other forum or something else?

i installed WUSB54G driver but it said that prism54usb or something like that and i put it on blacklist but it still would not connect!

also i went to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

and found the Version 1 and it said to remove islsm_usb

is that just blacklisting it?

and when i blacklist it doesnt seem to work

---

