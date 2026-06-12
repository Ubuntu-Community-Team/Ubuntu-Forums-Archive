---
title: "How to undo wpasuppicant?"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2005-12-01
I was somewhat confused and followed these instructions:  [http://www.ubuntuforums.org/showthread.php?t=90450&highlight=setup+wep](http://www.ubuntuforums.org/showthread.php?t=90450&highlight=setup+wep) to setup a WPA.  It was a really nice tutorial, and worked great... however, I realized afterward that I need WEP, not WPA.  So my question is how do I undo this now?  Do I need to ```
sudo apt-get remove wpasuppicant
```  How can I undo these configurations that I did?  Thanks.

Shane

---

### Post by hw-tph on 2005-12-02
Simply follow the guide and try to restore the configuration files you edited, most importantly /etc/network/interfaces. The wlan0 part of my interfaces file looks like this with wpasupplicant:```
auto wlan0
iface wlan0 inet dhcp
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
To remove the wpasupplicant parts and just set it up as a dumb DHCP interface (that goes online automatically without ifplugd or anything similar):```
auto wlan0
iface wlan0 inet dhcp
```

Håkan

---

### Post by shane2peru on 2005-12-02
Thanks!  That is what I did.  I didn't use the nsdiwrapper thing, so it was not an issue.  I only edited the two files that I made backup's for so that was simple.  I love those backup's!  After restoring original files I did a ```
sudo apt-get remove wpasupplicant
```  and that was the end of that!  Thanks for the info.

Shane

---

