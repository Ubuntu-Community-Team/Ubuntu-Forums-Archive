---
title: "Internet connection through old Ubuntu 13 system"
date: 2022-05-10
forum: Networking &amp; Wireless
---

### Post by stevecoh1 on 2022-05-10
My laptop is in the shop and so I am temporarily forced to use an old Ubuntu 13 system that I normally use only for backup. It is connected to my router by Ethernet cable.

I can’t get on the Internet from this computer. I can reach my router’s admin page at 192.168.1.1, which eliminates all cable connection issues from consideration, I think. But no internet access is available to any site. It seems that it is not finding DNS. Yet every other device in my home has internet access via Wi-Fi. This computer doesn’t have Wi-Fi. I think internet access used to work but it’s been awhile.

I am looking for a way to debug and fix this situation.

---

### Post by QIII on 2022-05-10
Hello!

Please do yourself -- and everyone else -- a favor and don't attempt to connect to the internet with such an old, unsupported release that cannot be updated.  You would be inviting all manner of security issues and hacking that could compromise your entire LAN.  Further, someone could use your machine as a bot, which would affect us all.

Can you install a supported release?

---

### Post by stevecoh1 on 2022-05-10
Oh please!
As I said, this is a temporary machine on a home network. Tomorrow, my laptop running 22.04, should return. There’s no real “entire LAN” to be “compromised.”

---

### Post by chili555 on 2022-05-11
What does this tell you?

```
sudo dhclient 
```

---

