---
title: "insmod: error inserting ieee80211.ko"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by colinireland on 2007-04-19
Hello



I am after screwing up big time and I am wondering if anyone can give me a hand to get back online as quick as possible.

I tried patching my ipw2200 drivers as per a tutorial I found on another thread to enable packet injection.


Everything was goin according to plan untill i reached this point:

xxxx@yyyy:/home/personal/wifi# cd ipw2200-1.1.4

xxxx@yyyy:/home/personal/wifi/ipw2200-1.1.4# sudo rmmod ipw2200

xxxx@yyyy:/home/personal/wifi/ipw2200-1.1.4# sudo insmod ipw2200.ko rtap_iface=1

insmod: error inserting 'ipw2200.ko': -1 Unknown symbol in module



This is the second time I have had this problem and it was suggested to me that I remove every running module with the rmmod command.
Afterwards when inserting ipw2200 it will call the correct ieee802.11 modules.



This is how I tried to do that:

colin@Niloc:~/wifi/ipw2200-1.1.4$ lsmod | grep ieee80211

ieee80211_crypt_wep     5120  0

ieee80211              37064  0

ieee80211_crypt         6272  2 ieee80211_crypt_wep,ieee80211

ieee80211_1_1_13       38216  0

ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211_crypt

ERROR: Module ieee80211_crypt is in use by ieee80211_crypt_wep

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211_crypt_wep

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211_crypt

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee802111_1_13_crypt

ERROR: Module ieee802111_1_13_crypt does not exist in /proc/modules

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211_1_1_13

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo rmmod ieee80211_1_1_13_crypt

colin@Niloc:~/wifi/ipw2200-1.1.4$ lsmod | grep ieee80211

colin@Niloc:~/wifi/ipw2200-1.1.4$ sudo insmod ipw2200.ko rtap_iface=1

insmod: error inserting 'ipw2200.ko': -1 Unknown symbol in module

colin@Niloc:~/wifi/ipw2200-1.1.4$



Why do I get the same error message? 

I cant get access to the net so I tried loading these  modules I found(I dont know if they are the correct ones or not):

colin@Niloc:/lib/modules/2.6.15-28-386/net/ieee80211$ ls

ieee80211_crypt_ccmp.ko  ieee80211_crypt_tkip.ko  ieee80211.ko
ieee80211_crypt.ko       
ieee80211_crypt_wep.ko

colin@Niloc:/lib/modules/2.6.15-28-386/net/ieee80211$ sudo insmod ieee80211.ko

Password:

insmod: error inserting 'ieee80211.ko': -1 Unknown symbol in module




I am new to linux and I have no idea how to fix this. I just want to be able to get on the net.
Any help would be greatly appricated.



Colin

---

### Post by colinireland on 2007-04-19
Well I ended up fixing it.

At the risk of sounding stupid, all it took was a reboot!!!!!!

However that wasn't the case the last time it happened to me.

---

