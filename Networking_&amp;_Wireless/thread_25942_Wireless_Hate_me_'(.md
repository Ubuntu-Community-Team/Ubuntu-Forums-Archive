---
title: "Wireless Hate me :'("
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by Gandalf on 2005-04-11
Hello,
i have been trying to get wireless connection up since 2 weeks, i already reinstalled OS serval times because of this, here's what's happeneing
my Laptop is HP, i have Intel Pro 2200BG wireless card
i installed ipw2200 and the firmware, then [COLOR=Blue]modprobe ipw2200[/COLOR] till now so far so good, i try to [COLOR=Blue]iwlist eth1 scan[/COLOR] i always get no wireless routers found, ok so i tried the gnome network utility changed some things and OK, now it's working, when i type iwconfig, there's connection (that was yesterday night) so i worked on wireless for more than 6 hours without a single problem... ok turned off the laptop woke up this morning, turn it on and... no wireless, iwconfig gives:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.
``` 
so i thought wireless not probed so
```

wael@nasreddine:/etc/network$ modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.10-5-386/drivers/net/wireless/ipw2200.ko): Operation not permitted
wael@nasreddine:/etc/network$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.10-5-386/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

checked dmesg :
```

ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Disabled Privacy Extensions on device c02f0500(lo)
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
eth0: no IPv6 routers present
eth0: link down
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

```
and it's not the first time, i already told you i have reinstalled OS serval times!!! what can be the problem? why after a reboot i have to reinstall OS to get wireless working again :neutral: 

thanks to anyone can help

---

### Post by luca_linux on 2005-04-11
I'm getting these errors too. I don't know what to do. Please, help us.

---

### Post by Gandalf on 2005-04-11
[QUOTE=luca_linux]I'm getting these errors too. I don't know what to do. Please, help us.[/QUOTE]
 can you tell me your hardware devices to see if it happen tu us only? which laptop you have, i have HP pavilion dv1071ea

---

### Post by luca_linux on 2005-04-11
I've an Asus M6N laptop with ipw2200

---

### Post by Gandalf on 2005-04-11
[QUOTE=luca_linux]I've an Asus M6N laptop with ipw2200[/QUOTE]
 ok good to hear that i'm not the only one having this weird behavor, bored2k any ideas???

---

### Post by Gandalf on 2005-04-11
hmmmmmmmm... it seems that there's a bug, see this [http://sourceforge.net/tracker/index.php?func=detail&aid=1171562&group_id=108390&atid=650334](http://sourceforge.net/tracker/index.php?func=detail&aid=1171562&group_id=108390&atid=650334)
i will instal 1.0.0 drivers and try again and tell you

---

### Post by luca_linux on 2005-04-11
It's really strange...untill I've installed Ubuntu, I was running Fedora and ipw2200 1.0.2 worked well...Anyway let me know, even if I really need version 1.0.2, since I need WPA support...

---

### Post by Gandalf on 2005-04-11
[QUOTE=luca_linux]It's really strange...untill I've installed Ubuntu, I was running Fedora and ipw2200 1.0.2 worked well...Anyway let me know, even if I really need version 1.0.2, since I need WPA support...[/QUOTE]
 i installed 1.0.0 version works so fine, if you want i can try for you 1.0.2 (because i will reinstall OS in any way because it's just a temp install so i will know what to install) anyway i tried 1.0.0 restarted/shudown for 3 times, so far so good (note that you need to make a change to the MakeFile before running make install
```

KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/

```
replace with
```

KMISC := /lib/modules/$(KVER)/drivers/net/wireless/

```

---

### Post by luca_linux on 2005-04-12
I've managed to get ipw2200 1.0.3 to work!
I've just copied all the modules from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/

---

### Post by Gandalf on 2005-04-12
[QUOTE=luca_linux]I've managed to get ipw2200 1.0.3 to work!
I've just copied all the modules from /lib/modules/$(KVER)/drivers/net/wireless/ to /lib/modules/$(KVER)/kernel/drivers/net/wireless/[/QUOTE]
hmmmmmm... really weird because the new kernel load them from drivers/net/wireless not from kernel/drivers/net/wireless !!! to get the 1.0.0 working i had to move them from kernel... to drivers...

---

### Post by Gandalf on 2005-04-12
no man didn't work for me, i had the same result :( i'm continuing to use 1.0.0 as it's a stable release

---

### Post by luca_linux on 2005-04-13
I finally figure it out! The problem is that Ubuntu loads the modules of ipw2200 from /lib/modules/$(KVER)/kernel/drivers/net/wireless/, while ipw2200 installs its modules in /lib/modules/$(KVER)/drivers/net/wireless/. So you have to copy them in the other location.
And you also have to copy /lib/modules/$(KVER)/drivers/net/wireless/ipw2000.ko to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/.

---

### Post by wlx on 2005-04-14
I have the same problem with dell lattitude d410, intel 2915 abg wireless card,ubuntu 5.04, ipw2200 1.0.3.
and I have not resolved this problem.
and I have copyed the files to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ and copyed /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/ipw2200.ko files.

---

### Post by Gandalf on 2005-04-14
[QUOTE=wlx]I have the same problem with dell lattitude d410, intel 2915 abg wireless card,ubuntu 5.04, ipw2200 1.0.3.
and I have not resolved this problem.
and I have copyed the files to /lib/modules/$(KVER)/kernel/drivers/net/wireless/ and copyed /lib/modules/$(KVER)/kernel/drivers/net/wireless/ipw2200/ipw2200.ko files.[/QUOTE]
 try ipw2200 1.0.0 it didn't work for me neither

---

### Post by luca_linux on 2005-04-14
hmmm...It's really strange...It worked on my box . Anyway I wrote the steps I followed in this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

