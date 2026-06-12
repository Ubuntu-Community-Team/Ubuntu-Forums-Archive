---
title: "WPA supplicant: working, now just where to put it."
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2006-08-13
Hi,

I'm trying to get WPA working in Ubuntu and Xubuntu (preferably Xubuntu since my wireless laptop is quite old.)

I went to install wpasupplicant and then found that it was already installed.

Both the **/etc/wpa_supplicant.conf** and **/etc/default/wpasupplicant** files were blank, so I filled them out.

I then tested the connection with the **wpa_supplicant** command and it associates with the access point and authenticates just fine.  My internet connection then works (while the console window running wpa_supplicant is still open).

But, I'm having trouble getting WPA supplicant to start when I boot up. 

I have these lines in my **/etc/network/interfaces** file:

```

auto ath0
  iface ath0 inet dhcp
  pre-up /etc/init.d/wpasupplicant start
  pre-up sleep 5

```

I reboot, and it brings up the ath0 interface but wpasupplicant hasn't worked its magic to authenticate itself with my AP.

I then checked, and I don't actually have the **/etc/init.d/wpasupplicant** file, which I assume is just a shell script to start wpasupplicant (sorry, I'm new to this.)

I'm assuming if I get a copy of this file and drop it in the directory, things should work?   Where do I get it from?

Help with this matter would be much appreciated.

---

### Post by visik7 on 2006-08-13
completly wrong 
read this
/usr/share/doc/wpasupplicant/README.modes

---

### Post by cookfromfrozen on 2006-08-13
Erm..."completely wrong" about what?

I'm at work at the moment so I don't have access to the readme file you talk about.

---

