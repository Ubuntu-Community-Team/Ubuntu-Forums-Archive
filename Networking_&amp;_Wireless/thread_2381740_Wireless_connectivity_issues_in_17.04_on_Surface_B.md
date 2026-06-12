---
title: "Wireless connectivity issues in 17.04 on Surface Book"
date: 2018-01-04
forum: Networking &amp; Wireless
---

### Post by bilekbp on 2018-01-04
Hello, I'm running into an issue where I apparently stay connected to a WiFi network but lose all ability to send or receive data after only a few minutes each time I reboot Ubuntu 17.04. I can't directly copy and paste the info, but after running dmesg I found a kernel bug:

kernel BUG at /build/linux-Fk60NP/linux-4.10.0/net/core/skbuff.c:105!

The trace includes many references to mwifiex, and I understand that there is a known issue with the Surface Book and mwifiex but I can't seem to find a solution in the forum here.

Can someone please assist (keeping in mind that I'll have to apply any fixes offline)?

Thank you!

---

### Post by chili555 on 2018-01-05
Please refer to comment #2 here: [https://bugzilla.redhat.com/show_bug.cgi?id=1505058](https://bugzilla.redhat.com/show_bug.cgi?id=1505058) Let's try disabling power saving. From the terminal:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Restart Network Manager:```
sudo service network-manager restart
```Any improvement?

---

### Post by bilekbp on 2018-01-05
Per comment #2 in that thread, I had previously disabled MAC address randomization to attempt to address the issue, but it did not help.

After entering your suggested commands, I am still unable to connect to websites. dmesg now shows a very long string of mwifiex_pcie warnings, including "failed to get signal information" over and over.

Edit: For some reason, after rebooting this seems to have worked long enough for me to run an in-place distro upgrade, so we'll see if I need to address this again after the upgrade. Thank you very much!

---

### Post by bilekbp on 2018-01-05
I spoke too soon. At some point during the in-place upgrade, I was no longer able to connect to the Ubuntu servers and the upgrade failed. I'm back to mwifiex_pcie issues, now it's stating "Card removed or firmware in bad state."

---

### Post by Hadaka on 2018-01-05
Hi, did you try both of these commands ?
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
printf "[device]\nwifi.scan-rand-mac-address=0\n"| sudo tee -a /etc/NetworkManager/*.conf
```

and are you aware Ubuntu 17.04 is going L.O.S [loss of support]

* ..................End of Life
Ubuntu 17.04 Jan-2018
Ubuntu 16.10 Jun-2017
Ubuntu 16.04  LTS Apr-2021
Ubuntu 14.04  LTS Apr-2019

---

### Post by bilekbp on 2018-01-05
I did not try the printf command before now as I didn't see it listed above, but I have found a workaround. It turns out that by running do-release-upgrade from the terminal and then rebooting each time I ran into connectivity problems I was eventually able to complete the in-place upgrade to 17.10, as the package download progress was cumulative. This has now resolved my issue; an inelegant, but effective, workaround.

I am aware that 17.04 is going through L.O.S., but needed to install it as my Surface Book has both an NVidia and Intel built-in GPU, and any attempt to install 17.10 or run it live from USB resulted in black-screen driver issues. The suggested solution on this forum was to install 17.04 first and upgrade it in-place, which I have finally completed, and I'm able to boot to 17.10 now without driver problems. So, yay! Problem finally resolved.

Thanks again!

---

