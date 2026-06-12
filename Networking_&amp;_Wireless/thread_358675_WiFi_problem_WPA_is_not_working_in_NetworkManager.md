---
title: "WiFi problem: WPA is not working in NetworkManager"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by foresth on 2007-02-11
Hi,

I've installed Edgy some time ago on my laptop and it's a GREAT system but I am still not able to make my wireless connection working with networks with a wpa key required.

My wificard wasn't recognized by Ubuntu, though loading of windows drivers via ndiswrapper works. I think that a problem might be in wpa_supplicant, because when I try to connect into an open network - without wpa key required, it works just fine.

When a network is protected by a WPA key, NetworkManager allows me to enter my passphrase (or hexadecimal string) but it won't connect (I'm sure the passphrase is correct).

I tried to create a wpa_supplicant.conf but it didn't help.

The strange thing is that when I run wpa_supplicant test with -Dndiswrapper, it prints somewhere between the lines "Driver doesn't support WPA", but with -Dwext it looks fine.

I didn't have such problem on Dapper (also using wpa_supplicant+networkmanager).

Any hints?

Thanks a lot!

---

### Post by foresth on 2007-05-07
I am sorry for openning this old thread but just for the case anyone would be searching for this...

After some research I found that WEP/WPA is not supported by ndiswrapper on my wireless card since some kernel version, but there is a possibility that a new kernel version allow it to work properly once again.

My laptop is Acer Aspire 1363WLMi.

---

### Post by rich.bradshaw on 2007-05-07
Oh right, I have a similar problem, hadn't tried wpa_supplicant as I think it's installed by default in Feisty. Perhaps a future kernel will make it work...

---

### Post by Praill on 2007-05-07
wpa-supplicant is included in feisty along with a network manager that can configure wpa encryption.

In edgy you have to install wpa-supplicant and a new network manager. You also have to edit the stock network manager to no longer configure your wirelss device.
Theres a guide for this somewhere on these forums. If i wasnt at work id look for you. Maybe search for wpa ubuntu in google.. thats how I found it if i remember.

---

### Post by foresth on 2007-05-07
Well, yes, but this is a matter of driver itself, not a way of configuration.

---

