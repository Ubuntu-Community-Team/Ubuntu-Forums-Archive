---
title: "Compaq NC6320 - Broadcom - weird issue.."
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by Thraka on 2006-07-25
My wireless actually works from using the CD but as soon as I install it onto the harddrive, the wireless card doesn't appear in the network adapters anymore.  

I'm 100% new to linux - i thought i would try it out.  Thoughts?

---

### Post by hw-tph on 2006-07-25
Wiki docs to the rescue: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Skip to section 1.2, you don't want to use ndiswrapper if you can help it.

Håkan

---

### Post by Thraka on 2006-07-25
Thank you very much. I'll get to that in the next few days when I get time to play.

It seems like a lot of work though :(  (Especially when the CD boot detects and uses it just fine)

Thanks again!

---

### Post by Thraka on 2006-07-26
Unfortunitly from that wiki site, the [http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o) doesn't exist anymore.  It also doesn't give me any steps of where to download it to, so I'm unsure where to put it.  

I noticed my boot menu had 2 Ubuntu entries on it with different kernals, i tried the older one and it detected the card and added it to the list of available ethernet devices.  Why do you think the new one doesnt see it?

---

