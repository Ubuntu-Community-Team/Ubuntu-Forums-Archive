---
title: "Can't connect with Atheros AR5416 Wireless Network Adapter"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by martinyt on 2015-03-31
I have a D-link DWA-547 with the AR5416 chipset. I find my network and have applied my password - It tries to connect, but fails. It does not ask for password again??, just stops trying. I am running ubuntu 14.10. and using the ath9k driver. I have found some threads with similar problems, but no solution.
Attached is the output from the wireless script.

All help, tips, hints or links to possible solutions are most welcome.

---

### Post by jeremy31 on 2015-03-31
Access point Mira_EXT is using TKIP which doesn't work well in Linux.  If you can, change it to WPA2 only with no WPA, WEP, or TKIP and see if you can connect then

---

### Post by Hadaka on 2015-03-31
Hi, you also have an incorrect driver loading ..

```
##### lsmod #############################
[COLOR=#ff0000]wl[/COLOR] [COLOR=#ff0000][/COLOR]                  6367694  0 
ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  5 wl,ath,ath9k_common,ath9k,mac80211

```
from a working wired connection please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get update
sudo modprobe -rf ath9k
sudo modprobe ath9k
```

---

### Post by martinyt on 2015-04-01
Thanks for reply! Unfortunately, it did not work. I am trying to connect to "mira" and not "mira_EXT", but thanks for the tip anyway - I might use my extender for a different purpose later. I have a laptop with ubuntu as well.


I followed your suggestion Hadaka. lsmod now gives:

```
##### lsmod #############################

ath9k                 136984  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446568  2 ath9k_common,ath9k
ath                    29052  3 ath9k_common,ath9k,ath9k_hw
mac80211              660592  1 ath9k
cfg80211              510218  4 ath,ath9k_common,ath9k,mac80211

```

But I still can't connect.

---

### Post by jeremy31 on 2015-04-01
If you are in Oslo, Norway we should set the regulatory code correctly ```
sudo iw reg set NO
``````
gksudo /etc/default/crda
``` go to the last line and make sure it says ```
REGDOMAIN=NO
``` Save and exit program

Since you are not trying to connect to the extender, turn it off or change what channel it is on and one other thing I would try ```
sudo modprobe -r ath9k
``````
sudo modprobe ath9k nohwcrypt=1
```

If the nohwcrypt=1 helps you can make the option load automatically with ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Setting IPv6 to ignore in Network Manager under the connection settings may help also

---

### Post by martinyt on 2015-04-01
Thanks Jeremy! but still no luck :( I have no disabled the wireless  extender, which I did not use - so at least I am saving some power  (Still using the cabled extender though). Is it possible to try to  connect from the terminal - maybe I could get some sort of error  message?

---

### Post by jeremy31 on 2015-04-02
I would try connecting to the extender after changing the encryption to WPA2 only and see if you can connect to that, or turn off encryption on the router for a little while to see if it will connect to it without a password

---

### Post by martinyt on 2015-04-09
I tried to connect to the router without password, but I still can't connect.:(

---

