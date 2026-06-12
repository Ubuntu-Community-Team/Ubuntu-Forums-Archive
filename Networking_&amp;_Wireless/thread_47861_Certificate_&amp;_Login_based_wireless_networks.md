---
title: "Certificate &amp; Login based wireless networks"
date: 2005-07-10
forum: Networking &amp; Wireless
---

### Post by PinnedBot on 2005-07-10
Hey! I'm trying to get Ubuntu Hoary to work with my campus network, but the network here uses PEAP plus a unique certificate (named 'wireless') to authenticate/authorize you to login, and then access the network. I use the built-in wireless authentication tool in windows to login. Is there anything similar for Hoary?

Thanks a bunch!

---

### Post by magoo on 2005-07-11
hello,

have a look at the wpasupplicant package ([http://hostap.epitest.fi/wpa_supplicant/)](http://hostap.epitest.fi/wpa_supplicant/)).
currently there is no gui for it (in fact there is one but I don't know if it is in the package of ubuntu: wpa_gui), so it's old school command line hacking and **not all wlan drivers are supported** (look at the previous web page)


you can look at this post explaining how to use wpa supplicant with WPA-PSK. 
[http://www.ubuntuforums.org/showthread.php?t=47406](http://www.ubuntuforums.org/showthread.php?t=47406)
I beleive you will only need a little bit of work to make WPA-EAP-PEAP work.

---

