---
title: "how to set up ad-hoc connection"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by r.stiltskin on 2007-05-24
When I try to configure my wireless connection in ad-hoc mode it gives this error: ```
 Error for wireless request "Set Mode" (8B06) :
     SET failed on device ath0 ; Invalid argument.
```

My laptop is running Kubuntu Edgy, with the madwifi modules installed as part of linux-restricted-modules-2.6.17-10-generic.

The wireless care is Netgear WG511T, which is supposed to support ad-hoc mode.

Specifically, I commented out most of /etc/interfaces/network, leaving  only these lines:```
auto lo
iface lo inet loopback
```
Then (choosing an arbitrary IP address) I ran ```
ifconfig ath0 192.168.2.107
```.
Finally: ```
iwconfig ath0 essid any mode Ad-Hoc
``` (I also tried ad-hoc and adhoc and AD-HOC) but each time I got the "invalid argument" error.

What am I doing wrong?

---

### Post by spd106 on 2007-05-26
Unfortunately it's not so easy with madwifi-ng. You can't switch mode like that instead you have to create a new VAP in adhoc mode. This can be done either through the wlanconfig tool, which means installing the madwifi-tools packages or by reloading the madwifi driver and creating an adhoc VAP automatically.

The steps to both methods are outlined on the madwifi website, [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

[http://madwifi.org/wiki/UserDocs/AdHocInterface](http://madwifi.org/wiki/UserDocs/AdHocInterface)
[http://madwifi.org/wiki/UserDocs/autocreate](http://madwifi.org/wiki/UserDocs/autocreate)

---

### Post by r.stiltskin on 2007-05-26
Great!  Thanks for those links, spd106.

---

