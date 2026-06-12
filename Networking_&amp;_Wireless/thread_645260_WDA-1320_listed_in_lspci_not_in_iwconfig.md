---
title: "WDA-1320 listed in lspci not in iwconfig"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by sedition on 2007-12-19
Hello all,

After hours of scouring the forums and Googling I am at my wit's end. I just tonight bought a D-Link WDA-1320 because of its praises of 'just working' and these links:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127080&Tpk=wda-1320](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127080&Tpk=wda-1320)
However, I got no love. lspci shows the card and lsmod shows "wlan", "ath_pci" and "ath_hal" but ifconfig -a and iwconfig shows nothing regarding it, only eth0 and lo.
I've uninstalled network-manager. No dice. I added ath0 and wlan0 to /etc/network/interfaces, with no love there either. dmesg | more did reveal:
"wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)" which led to:
[http://madwifi.org/ticket/808](http://madwifi.org/ticket/808)
I presume that there's a bug in the madwifi drivers, but I was curious if anyone is using this card in Gutsy? If so, then I might have to rollback or upgrade my package... I would just like to know if it works in the current version and what version of the madwifi package you may be using. Since my box is land-locked (i.e. no intarwebs) I'd like to get an idea before I start downloading and burning to transfer.

Thanks in advance,
-sed

EDIT: Nothing to see here, move along...
I reseated the card and everything works. Nothing more than PEBCAK. This has been another monthly installment of me asking a question and then figuring it out on my own the next day. That is all...

---

