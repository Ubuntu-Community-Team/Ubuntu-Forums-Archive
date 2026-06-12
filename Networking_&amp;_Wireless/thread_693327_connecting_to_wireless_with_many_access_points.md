---
title: "connecting to wireless with many access points"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by s3raphim on 2008-02-10
This is not an Ubuntu specific problem (I had it with Fedora too) nor an HP laptop specific problem (my labmate has the problem on his Dell).

My Broadcom wireless card is nicely working with Feisty and the bcm43xx drivers.  It works at home with WPA or WEP.  At school, however, we have two main SSIDs broadcast over many many access points on multiple "channels."  The computer gets comfused.  It takes forever to connect, and usually the connection gets dropped.  One SSID is unencrypted, the other is encrypted, but the problem seems to be the same with both.  Under Fedora with wlassistant, things worked for about a day.  I think Netwok Manager may be to blame, getting confused by the many access points and unloading and reloading the firmware repeatedly?  In any case, does anyone else have this problem?  How did you fix it?

machines:
HP dv2416us with working Broadcom card
running Ubuntu Feisty 7.04 with
bcm43xx and fwcutter

also on 
Dell using fwcutter also with Broadcom card

---

### Post by Bubba64 on 2008-02-10
using roam which it sounds like you are using instead of clicking on properties then network name then choosing a connection that it will stay on may be your problem. I never use roam it causes the problems you suggest you having.

---

### Post by s3raphim on 2008-02-11
So, if I specify the SSID, what do I do about the fact that there are many points with the same SSID?

(I can't test it today b/c my laptop slept in this morning)

---

### Post by Bubba64 on 2008-02-12
If you tell it to read a ssid that needs a key it will ask you for the key so keep trying until you find the open one. I am not sure I understand your question though.

---

### Post by aeiah on 2008-02-12
try connecting to the AP you want by specifying its MAC address and not its SSID?

iwconfig wlan0 ap MAC

may work, although i have no experience with your card. you can find the MAC with aircrack-ng, kismet or RutilT, amongst others

---

### Post by s3raphim on 2008-02-14
So, if I try to connect to the ap specifiically (having done iwlist scan to get the MAC address) nothing happens.  I seem to be having limited success allowing Network Manager to automatically connect to the unencrypted network.  Network Manager only lets me connect to a specific SSID manually if I specify a WEP key, however, and neither network is WEP.  

Furthermore, poking around in ~/.gconf/system/networking/wireless/networks/ showed one directory for each of the two SSIDs plus one for my apartment.  However, each directory only contained a link to a gconf.xml file, and they were all the same file.  I feel like make putting something in these directories would fix the problem, but I don't know what it is. 

Is there usually something besides the xml file link in the SSID directories?  

I was able to edit gconf.xml to delete multiple MAC addresses from the encrypted SSID, but the result was just that NM bounced me to the unencrypted network.  It seems to be functioning at the moment, but I don't hold out any hope.

Any thoughts?

---

