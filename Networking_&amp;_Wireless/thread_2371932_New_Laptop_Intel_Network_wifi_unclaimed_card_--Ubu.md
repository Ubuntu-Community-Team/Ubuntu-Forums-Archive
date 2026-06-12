---
title: "New Laptop Intel Network wifi unclaimed card --Ubuntu Xenial- Clevo/Kapok"
date: 2017-09-20
forum: Networking &amp; Wireless
---

### Post by trtle on 2017-09-20
[http://paste.ubuntu.com/25577635/](http://paste.ubuntu.com/25577635/)

I'm working on my computer and been installing new software cause I just got it
And trying out LXLE, which seems to be up my alley, and it works pretty good out of the box
But I can't get Ubuntu Xenial to recognize my network card.
It remains unclaimed, but about all I done is one modprobe command for sudo modprobe iwlwifi
And looked around forums a ton, trying to diagnose it.
Can you help me?

---

### Post by trtle on 2017-09-20
hello? The network card isn't being claimed by anything...  what should I do?

---

### Post by jeremy31 on 2017-09-21
What happens when you ```
sudo modprobe -v iwlmvm
```

---

### Post by trtle on 2017-09-21
sudo modprobe -v iwlmvm
#####################33
insmod /lib/modules/4.4.0-74-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-74-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.4.0-74-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
insmod /lib/modules/4.4.0-74-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko

---

### Post by jeremy31 on 2017-09-21
What about ```
dmesg | grep iwl
```

---

### Post by trtle on 2017-09-21
thanks everybody for your help!!!  Mark this as [Solved]
I had kernel 4.4 and looked up how to install kernel 4.8 or 4.9 And Now My Wifi is WORKING!!!!
I needed the iwlwifi driver installed but it's a newer pci card so it really wasn't/hadn't been invented yet for the 4.4.0 kernel.
I don't know why That happens :)
I'm going to install the newest kernel if I can ask you something before you go..  Do new kernels sometimes break older packages?

---

### Post by jeremy31 on 2017-09-21
Newer kernels can break some dkms module support but they are mainly for Nvidia graphics and Broadcom wireless.
You should have used the following command to install the new kernel so it stays updated by the Update Manager
```
sudo apt-get install --install-recommends linux-generic-hwe-16.04
```

You can mark as solved by using the Thread Tools menu near the top right of the page

---

### Post by trtle on 2017-09-22
Thanks again, will do.

---

