---
title: "trying to get wireless working"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by tornsolitude on 2008-02-09
I am following the guide to get wireless working manually, but I can't get it to work.  When I type "sudo dhclient -r wifi0", it says this twice, unknown hardware address type 801".  Now, in wpa_supplicant.conf, where I put the psk, is the the same thing as the passphrase when I set it up in the router?  And then I tried connecting and leaving it unencrypted, and I got "Error for wireless request "set ESSID" (8B1A) : SET failed on device wifi0 ; Invalid argument".  What's wrong?

---

### Post by kevdog on 2008-02-09
Its probably not wifi0, but ath0.  wifi0 is the actually interface name, the madwifi drivers actually function through virtual interfaces.  So for each actual real interface, madwifi creates either one or more virtual interfaces.  By default the first virtual interface is ath0.  You would direct your commands to ath0, which in turn would be passed to wifi0.

---

### Post by tornsolitude on 2008-02-09
It said the same thing when I typed in "sudo dhclient -r ath0".  But when I typed in "sudo wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd", it's giving me a bunch of stuff that keeps repeating itself in a loop and won't stop.

---

### Post by tornsolitude on 2008-02-09
Ok, I rebooted and it doesn't do that loop thing anymore.  But when I type sudo dhclient ath0, it says No DHCP OFFERS received.  Does it matter that I configured the router to be an access point?

---

### Post by kevdog on 2008-02-09
Ok this is a good sign:

It said the same thing when I typed in "sudo dhclient -r ath0". But when I typed in "sudo wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd", it's giving me a bunch of stuff that keeps repeating itself in a loop and won't stop.

As long as you didnt see any errors than do this:
sudo wpa_supplicant -B -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf 

This will start the process in the background but will not show you if there are any errors.  If you want to see the output, then you need to pop open another window and type the dhclient command in the other window.

As far as the access point, I dont think this matters, however dhcp needs to be configured on the access point.  The whole point of this exercise is to allow the router to assign your computer a dynamic IP address with an encrypted connection.  If the DHCP server on the router is disabled, then the router or access point will never assign or give out an IP address.

---

### Post by tornsolitude on 2008-02-09
Thanks!  I got it to work manually.  But when I followed the instructions to have it connect from startup, it doesn't work and a window will popup asking for the network passphrase.

rc.local = 
ifconfig eth0 down
ifconfig ath0 down
dhclient -r ath0
wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -dd 
ifconfig ath0 up
iwconfig ath0 mode Managed
dhclient ath0
exit 0

---

### Post by tornsolitude on 2008-02-09
anybody?

---

