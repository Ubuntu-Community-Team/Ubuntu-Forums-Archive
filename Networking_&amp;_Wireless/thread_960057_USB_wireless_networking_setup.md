---
title: "USB wireless networking setup"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by its.ray on 2008-10-27
:confused:
Hi,
I have installed Ubuntu 8.4 Hardy Heron and I cannot configure my wireless network usb dongle. It just does not seem to recognise it. My provider is ViginMedia (UK)
Could someone guide me through it please?
I used to run Vista Ultimate but I got sick of the constant upgrades and patches that hogged rescources. Bye Bye Bill Gates's crowd, you are a bunch of tossers!
Ray

---

### Post by livestockPimp on 2008-10-27
To get the wireless dongle working you need to know what type it is, it also depends on what encryption you are using wpa/wep/ect.

Open a terminal window and type "lspci" and paste the output here and also "lsusb"

---

### Post by lemmy999 on 2008-10-27
I assume that you are talking about a mobile broadband dongle? If so try searching on here for network-manager 0.7. Its been designed to take this situation into account!

Check out this post, it may help
[http://ubuntuforums.org/showthread.php?t=948977&highlight=network-manager](http://ubuntuforums.org/showthread.php?t=948977&highlight=network-manager)

---

### Post by DrMelon on 2008-10-27
Or if you want more control over your network, how about trying wicd?

You can get wicd by typing this in a terminal window:
```
sudo apt-get install wicd
```

---

