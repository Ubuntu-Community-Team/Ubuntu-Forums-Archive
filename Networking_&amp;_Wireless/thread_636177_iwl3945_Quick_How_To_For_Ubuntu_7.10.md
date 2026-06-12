---
title: "iwl3945 Quick How To For Ubuntu 7.10"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by dayzed2 on 2007-12-09
Anyone wanting to use the iwl3945 replacement driver for ipw3945 only needs to do the following:
sudo modprobe -r ipw3945
sudo modprobe -r ieee80211
sudo modprobe -r ieee80211_crypt
sudo modprobe iwlwifi_mac80211
sudo modprobe iwl3945
Of course for you newbies that don't understand when you reboot this all goes away and you will need to do this all over again. I am not going to get off topic and show you how to fix this, however I will give you a hint, you will need to modify 2 files /etc/modprobe.d/blacklist and /etc/modules.

The iwl3945 driver already comes with Ubuntu 7.10 so there is no need to install or compile. This driver is newer and fixes a lot of problem people have been seeing. Some of you might have already tried to use the iwl3945 driver before and got an error when trying to insert the module, the above commands should fix your problem. Most likely the problem you were having is that you were trying to use mac80211 instead of iwlwifi_mac80211. I finally figured out that this is what was causeing my problems after reading this [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501).

I sure hope this helps someone.

---

### Post by dayzed2 on 2007-12-09
Oh I almost forgot if your card shows up as wlan0_rename which isn't a big deal it will still work, but if you would like to fix the name then follow these instructions [http://wiki.debian.org/iwl4965](http://wiki.debian.org/iwl4965) . The actual name of the file you need to edit for Ubuntu is 70_persistent-net.rules

The only problem with the renaming solution is when running iwconfig you will get a "wmaster0 no wireless extensions"  so this might not be the best way to do things. However it doesn't seem to hurt anything either.

---

### Post by caryb on 2008-01-03
I'm struggling with getting my T61 wireless going & it doesn't help when I get this from the Debian link

This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists.



Cary

---

### Post by phenest on 2008-01-10
> **dayzed2 said:**
> Anyone wanting to use the iwl3945 replacement driver for ipw3945 only needs to do the following:....

Or you can use the Restricted Drivers Manager like I did. Uncheck the box for the ipw3945 and restart.

---

### Post by caryb on 2008-01-17
1st mine is a 8.04 install! I installed wicd & uninstalled network manager this was a dismal failure! I uninstalled wicd & reinstalled network manager & knetwork manager gui, this now connects to wireless but it disconnects & says interface is down after 10 minutes. Are there any thoughts in the brains trust?


Lenovo T61 Kubuntu Hardy 8.04 2.6.24-4 64bit kernel with iwl3945 wireless card

wlan0     IEEE 802.11g  ESSID:"adminap"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0D:54:A0:AF:B7
          Bit Rate=36 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:xxx etc
          Link Quality=74/100  Signal level=-60 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Cheers Cary

---

