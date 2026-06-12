---
title: "Wifi trouble after upgrade to Jaunty"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-10
>  Originally Posted by Curvature_Tensor  View Post
sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card. Also worked for Marvell 88E8038 wired Ethernet port


Hi, I have an Atheros AR242x wifi card on my laptop, I first found this post [http://nuclear-imaging.info/site_con...nty-jackalope/](http://nuclear-imaging.info/site_con...nty-jackalope/) which did not work to get my wifi working.

So I ran into this post after that, and tried it, but yet to no avail did it work either. I am thinking it might be because I messed up by following the first post I had found. Can anyone help me with this.

SOLVED WITH THIS POST [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html/comment-page-1]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html/comment-page-1")

---

