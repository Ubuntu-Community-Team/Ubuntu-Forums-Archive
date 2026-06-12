---
title: "Feisty only able to connect to encrypted wifi RTL8187 chipset."
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by jimdaworm on 2007-12-31
Hi everyone I am only able to connect to encrypted networks.  If I try to connect to an unencrypted one it appears to connect according to the nm-applet but never receives an ip address, somtimes it doesnt even appear to connect:confused:

Dmesg
> [30199.971695] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[30199.971728] wlan0: deauthenticate(reason=3)
[30207.056561]  CIFS VFS: No username specified
[30207.056565]  CIFS VFS: cifs_mount failed w/return code = -22
[30217.259607] eth0: no IPv6 routers present
[30239.133980] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30240.656576] wlan0: Initial auth_alg=0
[30240.656580] wlan0: authenticate with AP 00:11:f5:dd:b4:e1
[30240.854098] wlan0: authenticate with AP 00:11:f5:dd:b4:e1
[30241.054052] wlan0: authenticate with AP 00:11:f5:dd:b4:e1
[30241.254005] wlan0: authentication with AP 00:11:f5:dd:b4:e1 timed out
adam@buntyhome:~$ 


Modules I think are in use:
> adam@buntyhome:~$ lsmod |grep rtl
rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  6 ndiswrapper,rtl8187,usbhid,ehci_hcd,uhci_hcd
adam@buntyhome:~$ 


Tell me if any other info might help.  I am using the standard kernel 2.6.22-14-generic

---

