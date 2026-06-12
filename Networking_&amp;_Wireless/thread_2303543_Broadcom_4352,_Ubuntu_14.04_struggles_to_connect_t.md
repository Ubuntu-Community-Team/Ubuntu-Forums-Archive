---
title: "Broadcom 4352, Ubuntu 14.04 struggles to connect to wireless network"
date: 2015-11-19
forum: Networking &amp; Wireless
---

### Post by roma24ster on 2015-11-19
[COLOR=#111111][FONT=Ubuntu]I'm using Ubuntu 14.04 and I have problems connecting to the wireless network in my house. It sees the network, it can connect sometimes (one out of every 100 attempts it suceeds) but normally it just tries to connect for about 2 minutes, then fails. Sometimes it asks for the password again, which has already been entered correctly. It connects fine in windows (I dual boot).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm using an Asus z97i-plus motherboard, broadcom 4352, and the driver suggested by ubuntu: broadcom 802.11 linux Sta wireless driver source from bcmwl-kernal-source (proprietary).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've run the wireless info script linked [here]("http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos"). My results are pasted below:[http://paste.ubuntu.com/13335757/](http://paste.ubuntu.com/13335757/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The network i'm trying to connect to is 'BTHub5-QMXQ'.[/FONT][/COLOR]

---

### Post by Hadaka on 2015-11-19
[http://ubuntuforums.org/showthread.php?t=2289270&](http://ubuntuforums.org/showthread.php?t=2289270&)

try this, same card as yours.

---

### Post by roma24ster on 2015-11-19
Just tried that, with the same file hosted [here]("http://old-releases.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/"), after it my wireless is completely disabled, it doesn't even show wireless as an option. 

I think that may be because the file bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb doesn't list 4352 as an adapter it works with in the description in debi.

The dkms deb says there is a newer version already installed so I left that alone.

---

