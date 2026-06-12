---
title: "wireless dhcp problem"
date: 2005-07-04
forum: Networking &amp; Wireless
---

### Post by cheeseballs on 2005-07-04
After following the ipw2200 and wpa howto I was able to learn how to at least get my card to find my access point on eth1. 

In my /etc/network/interfaces i have only added the line: 

iface eth1 inet dhcp

I have not added map eth1 or auto eth1 because I do not want to wait on the dhcp when I am away from home. Therefore...

First command I issue is 

sudo -s

To get all the permissions required.

Then I enable the wireless card with 

ifup eth1 

I am able to see eth1 with the ifconfig command. I then issue the command

wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w(sometimes I add the -w option sometimes not it does not seem to matter since the interface is already up)

iwconfig lists bit rate encryption key and ESSID, ap mac address all fine. It does say unassociated though. Is that a problem?

I then proceed to run

dhclent eth1

Only one time have a gotten a dhcp reply and and hence and IP. All worked fine. I have not been able to get it running again.

I may be a little confused in the way the  wpa_supplicant.conf file is accessed. After the parameter "psk=" do you input an ascii string or do you have to input the hex code that is spit out by wpa_passphrase.

Thanks

---

