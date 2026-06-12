---
title: "wireless woes (WMP54GS with WPA2-TSK)"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by PixelCloud on 2006-08-18
I recently decided to try out this whole ubuntu business after hearing good things. Duat botted xp and dapper drake 6.06.1.

However my wireless card decided not to work out of the box (as i was told it would)

Would the ndiswrapper work for my system? It needs to work with wpa2. 

I did try to install the ndiswrapper with no success mostly because i have to download files off my windows xp install and use an external hd to transfer them between installs. I was unable to compile ndiswrapper due to the lack of dev tools, usally wouldn't be a problem but i have no internet connection to install them.

Any ideas?

---

### Post by Zed on 2006-09-03
After a lot of work, I can tell you it's possible to get a WMP54GS to work with WPA2-PSK under ndiswrapper. It would be possible, but very painful to do it without a net connection. But you could [mount your windows partition](http://www.psychocats.net/ubuntu/mountwindows.php) under Ubuntu, figure out everything you need to download, boot back into Windows to download it, and then back into Ubuntu to install and build things -- at least it saves you futzing with the external drive.

---

