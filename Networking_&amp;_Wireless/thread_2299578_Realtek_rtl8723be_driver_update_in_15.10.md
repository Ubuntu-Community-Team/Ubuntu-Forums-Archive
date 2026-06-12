---
title: "Realtek rtl8723be driver update in 15.10"
date: 2015-10-19
forum: Networking &amp; Wireless
---

### Post by ajmedfor2 on 2015-10-19
I have installed Ubuntu 15.10 on a HP Stream 11 laptop with a Realtek wireless card. I can connect to wifi networks most of the time, but the card seems to sporadically drop the signal. It seems that there is an updated driver from Larry Fingers that many people report as a fix in 14.X:

[https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi)

but when I try to add the PPA I get a 404 error on apt-get update:

```
W: Failed to fetch http://ppa.launchpad.net/hanipouspilot/rtlwifi/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found
```

Does anyone know if there is a version that will work with wily? Or know if it is possible to get the old version installed? I would prefer to avoid building from source in order to make it more stable.

I have also tried modifying the /etc/modprobe.d/rtl8723be.conf file as reported in several other posts (e.g. [http://ubuntuforums.org/showthread.php?t=2243978](http://ubuntuforums.org/showthread.php?t=2243978)) but this doesn't seem to help. Any other ideas? The wireless-info is attached.

---

### Post by kysergey on 2015-11-11
The ppa maintainer did not provide package for 15.10 version. I have the same issue on my MSI laptop, setting options does not help me. I rebuilt [rtlwifi-new-dkms]("https://docs.google.com/uc?id=0B4xGiBgX1YJEbU5aa3ZFZEJZbjg&export=download") for wily. You can try it, but I'm not sure it works as stable as rtlwifi-new-dkms on vivid.

---

