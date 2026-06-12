---
title: "[SOLVED] wireless interface detected as a wired interface"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by andymushu on 2007-11-01
My wireless network interface, ath0, was previously working fine. I recently changed my router's encryption to WPA-PSK, then changed the setting accordingly in my network-administration menu. For reasons unknown to me, the next day after a reboot the wireless network interface ath0 was detected as a wired interface. This caused a few issues, namely the lack of an input box for the encryption key. After some configuration, i have a network connection again, although this was only accomplished by disabling network encryption altogether. This is obviously not desirable, and i was hoping there was some way to make ath0 be recognized as wireless again. I don't know which logs i should post or anything like that, but i will be happy to post any logs that may help with the issue. Any help would be much appreciated.

-Andy

---

### Post by kevdog on 2007-11-01
For changing the interface name such as ath0 associated with a network card MAC address:

/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses

---

### Post by andymushu on 2007-11-02
Thanks for the reply. Looking at that file, it contains ath0 and eth0, my wired connection. I don't see anywhere where it specifies that it is a wired connection, however. I am basically seeking to change ath0 from a wired connection to wireless. I didn't see anything about that in the file posted, but maybe I am just missing it. Thanks for the help.

Edit: For some odd reason my wireless-tools package was no installed. Once I reinstalled it, ath0 was recognized correctly. Everything works fine now, thanks for the help.


-Andy

---

