---
title: "Gutsy, 64 bit, Dell D630, Intel 3945 wireless, iwl3945/iwlwifi howto"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by stinkerweed999 on 2008-02-16
I solved a problem and wanted to share.  I didn't search the forum too much so this maybe a duplicate.  Either way I find most postings to be too wordy, so I'm posting my notes of how to get Intel 3945ABG working on a new Dell 630D with Gusty (7.10) 64bit.  

Without further ado:

Configuration of iwlwifi Intel 3945 driver for ubuntu 7.10, 64 bit
------------------------------------------------------------------
(partially taken from [http://dan.bodar.com/2007/12/29/more-ubuntu-710-notes-for-dell-d630/](http://dan.bodar.com/2007/12/29/more-ubuntu-710-notes-for-dell-d630/))

- disable ipw3945 proprietary module in System->Administration->Restricted Driver Manager
- sudo vi /etc/modprobe.d/blacklist
   - append:
      blacklist ipw3945
      blacklist ieee80211
      blacklist ieee80211_crypt
      blacklist mac80211
- sudo vi /etc/modules
   - append:
      iwlwifi_mac80211
      iwl3945
- reboot
- 'iwconfig' should show some kind of wlan_* interface
- sudo vi /etc/udev/rules.d/70-persistent-net.rules
   - comment out the line reserving eth1 for ipw3945 module
- sudo modprobe -r iwl3945
- sudo modprobe iwl3945
- System->Administration->Network
   - configure wireless interface
   - close
- sudo /etc/init.d/networking restart
- should get an IP address

While I post this I'm torturing the wifi interface with 15 SCPs and bittorrent over SSH proxy.  22GB+ transferred already without any errors or dropped packets (as reported by ifconfig).  The previous ipw3945 driver didn't make it 2 minutes without hanging.

Hope this helps someone.  I hate it when wifi is flaky.  Hats off to Intel for getting the iwl3945 stabilized (at least on my Dell D630)!

---

### Post by simonl2009 on 2008-02-20
I was having problems with 32-bit ubuntu and followed this advice. It looks like it worked, thanks very much!

---

### Post by stinkerweed999 on 2008-02-23
No problem.  Glad it worked for you!

---

### Post by mk4umha on 2008-02-27
I had problems in 32 and 64bit wireless  dropping connections and locking my system up. I reinstalled 64bit and did your method and so far it's been working without one hiccup or dropped connection.

---

### Post by stairwayoflight on 2008-05-20
Wow, works like a charm!

ipw3945 never gave me any problems on gutsy before, but after reinstalling I couldn't get it going. Thanks for the help.

---

