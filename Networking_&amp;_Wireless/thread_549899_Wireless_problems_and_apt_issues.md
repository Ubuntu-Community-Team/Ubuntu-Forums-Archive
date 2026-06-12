---
title: "Wireless problems and apt issues :"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2007-09-13
I have an Acer Aspire 9300 laptop with a broadcom wireless networking card in it.

I followed the instructions to use bc43xx-fwcutter, and they worked great!

But now, whenever the computer goes into hybernation mode, when I bring the machine up, wireless connectivity is lost, and I don't know how to bring it back.  What's peculiar is that in the gnome network manager (accessed by click on the icon on the top bar), wireless is no longer listed.


Also, a related problem is with apt-get.  Now whenever I run apt-get upgrade I get the following at the end:

Setting up bcm43xx-fwcutter (006-1) ...
--07:28:20--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
07:28:20 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)




Any Ideas?

---

### Post by spd106 on 2007-09-13
That source of firmware has been removed so the install script is failing.
You could edit the script to use this source instead, [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

Or since you've already got the firmware, just uninstall the bcm43xx-fwcutter package. It has served it's purpose.

---

### Post by mohnkern on 2007-09-13
Yup, that solved the second problem, now if I can just figure out how to "bring back" the wireless connection after going into hibernate mode.

---

### Post by spd106 on 2007-09-13
There is a suggestion on the network manager help page.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

