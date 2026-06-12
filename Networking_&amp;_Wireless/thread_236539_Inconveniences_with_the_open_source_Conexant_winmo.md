---
title: "Inconveniences with the open source Conexant winmodem driver"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by te27ch on 2006-08-14
Hi folks, I've successfully gotten my conexant winmodem to work using the open (non-Linuxant) driver as per [this part of the wiki page]("https://help.ubuntu.com/community/DialupModemHowto#head-d0559c803689d0820bf698ab0029c01a7345a5e7"). I followed all the directions, used the script to compile it for my kernel, then followed the other directions to compile the driver for my specific modem. The internet now works.

I downloaded gnome-ppp to connect because I like the convenience of a nice graphical front-end.

Unfortunately, several things don't seem as good as they should be. I live about 30km from the nearest town, so my top modem speed in Windows is usually 24 to 26.4kbits/sec, around 3kbytes/sec. In Ubuntu, download speeds in Firefox, for example, hover around 2.1 to 2.4 kbytes/sec. While this seems like a minor difference to broadband users, it's actually very significant, especially for larger files.

Another inconvenience is when I try to download more than one thing at once. In Windows, I could have a pdf, program, or other file downloading while I browsed the internet. While it would be a bit slower, it was possible. Not so in Ubuntu, where downloading a file from the internet seems to use all of my bandwidth, making browsing impossible and even disconnecting GAIM. 

Getting a different modem is not an option at the moment for me, but I believe that these problems can be fixed. While certain aspects of dial-upping are more convenient in Windows so far, I still have strong faith in the open-source community.

Thanks for any help.

---

### Post by towsonu2003 on 2006-12-05
You seem to ghave got no responses, so I'm just gonna guess... I've got no info to backup my guess... check out this:
[http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6](http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6)

---

### Post by neoaddict on 2007-02-13
Above link is broken, try this one:

[http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/](http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/)

---

