---
title: "wifi not showing and not working"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by tankarakesh.38 on 2014-02-26
hi,

recently i installed ubuntu 14.01. i am unable to connect through wifi. neither showing nor working. please help me.

---

### Post by xeonix on 2014-02-26
I guess, you mean, version of 14.04?
As, ubuntu 14.04 is still in alpha, I recommend you install anyof the realeased version of ubuntu instead of non realeased version, as they are still in testing environment. You may face one or the other issues.

However, could you please post the output of the commands:
```

nm-tool
sudo lshw -C network

```

---

### Post by gdupont on 2014-03-01
I had a similar issue when upgrading to the latest 14.04 yesterday. It's probably related to the alpha things in test but I managed to get my wifi back following this guidelines:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
On my side the issue was related to the pci bus ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices) section 5.2) and I had to add an option to the boot.

---

