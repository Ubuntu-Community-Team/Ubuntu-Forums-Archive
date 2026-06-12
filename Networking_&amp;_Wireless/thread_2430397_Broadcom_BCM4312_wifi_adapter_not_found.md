---
title: "Broadcom BCM4312 wifi adapter not found"
date: 2019-10-31
forum: Networking &amp; Wireless
---

### Post by zhayyeh on 2019-10-31
I installed Ubuntu 18.04 alongside Windows 10 Pro on my Dell Vostro 1320. The wifi settings show "no wifi adapter found". I have spent several hours trying to install various drivers to see if I could get on to work to no avail. I am posting the results of script that I found on another page that helps run a thorough diagnosis.

You help is greatly appreciated.

---

### Post by zhayyeh on 2019-11-01
Here's an updated file.

---

### Post by jeremy31 on 2019-11-01
Open the backport-iwlwifi folder in terminal and do ```
sudo make uninstall
sudo apt install firmware-b43-installer
```
Reboot

---

### Post by zhayyeh on 2019-11-01
Firstly, thanks for your help. I see that you have assisted many in overcoming this issue and I don't believe I can say thank you enough.

I tried removing  backport-iwlwifi and other drivers but I still have issues. See updated wireless-info.txt.

Regards

---

### Post by zhayyeh on 2019-11-01
Here's the result after "sudo apt install firmware-b43-installer" and reboot.

Thanks again

---

### Post by jeremy31 on 2019-11-01
You need to uninstall the backports from Intel, post results from terminal for ```
dkms status
```

---

### Post by zhayyeh on 2019-11-01
dkms status shows nothing

---

### Post by zhayyeh on 2019-11-01
dmesg | grep iwl
[   14.930809] Loading modules backported from iwlwifi
[   14.930810] iwlwifi-stack-public:master:8042:654c426c
[   18.179561] WARNING: CPU: 0 PID: 243 at /home/zaid/Downloads/backport-iwlwifi/net/wireless/core.c:866 wiphy_register+0xb56/0xb70 [cfg80211]

---

### Post by jeremy31 on 2019-11-01
You may have to wait for a kernel update if you can't uninstall the backport-iwlwifi

---

### Post by zhayyeh on 2019-11-01
Any sugestions?

---

### Post by jeremy31 on 2019-11-01
In terminal try
```
cd ~/backport-iwlwifi
sudo make uninstall
```

---

### Post by zhayyeh on 2019-11-01
What about blacklisting?

---

### Post by jeremy31 on 2019-11-01
It won't work as some modules installed by  backport-iwlwifi are not compatible with the kernel modules you need

---

### Post by zhayyeh on 2019-11-01
How often do kernel updates occur? Will reinstalling the kernel work?

---

### Post by zhayyeh on 2019-11-01
Thank you! Everything is working now. I reinstalled the backports sofware then uninstalled it.

---

