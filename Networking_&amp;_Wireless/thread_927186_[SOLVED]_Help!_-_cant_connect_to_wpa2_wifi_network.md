---
title: "[SOLVED] Help! - cant connect to wpa2 wifi network using wicd"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by pablo_toledo on 2008-09-22
Hi all, this is my first couple of days with ubuntu (hardy, x86) and I'm having real trouble getting my wifi card sorted so I would REALLY REALLY appreciate some help.

My wifi card (a cheapo marvel libertas (MRV-8335) pci card ) didn't come natively supported in ubuntu, but I finally got it working by using the ndswrapper approach. 

My home network is wpa2 encrypted, and I managed to connect to it by selecting the ssid and entering the password in network manager. So far so good!!

However, I found that on reboot network manager would fail to reconnect automatically. I had to delete the stored ssid/password info etc, stop and start the networking, and re-enter the password each time - total pain!

So anyway, this prompted me to install wicd as an alternative to network manager. It looks great, but now when I try to connect to my network, it gets stuck at "obtaining ip address". Its definitely not the password/encryption, and I know the wifi card driver is properly installed, so what the hell do I do??

should I uninstall wicd? Or can something be fixed in a config file somewhere? Would really appreciate any help anyone can give. I've googled endlessly and tried a whole bunch of stuff, and I don't want to make it worse!!

cheers

Pablo

---

### Post by pablo_toledo on 2008-09-23
Hmm, strange. Everything seems to be working now. Upgraded to wicd 1.52 and wifi connecting fine on logon. A little slow, but after the palava I've gone through I'm not complaining!

---

