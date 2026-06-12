---
title: "Wireless is slow and disconnects often"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by MdaG on 2006-11-25
Hi!

I've got a ```
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
``` wireless card. Since there are no native Linux drivers for it I have to use ndiswrapper. Problem is that the connection is sometimes painfully slow and it's not uncommon that it loses connection with my router. This is not an issue in Windows XP or Gentoo Linux (where I also use ndiswrapper). Why then is it an issue in Ubuntu 6.10 or is it me that's made some faulty setup somewhere?

---

### Post by ReaderRat on 2006-11-25
See if this is what you need >>>  **[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)**

---

### Post by MdaG on 2006-11-25
Yes I've done those steps and my wireless setup is working, but not as good as in Gentoo or WinXP. I'm using bcm43xx-fwcutter to extract some files from my native Windows drivers and store them in /lib/firmware and the kernel location. I wonder what's making it work worse than in Gentoo? ](*,)

---

