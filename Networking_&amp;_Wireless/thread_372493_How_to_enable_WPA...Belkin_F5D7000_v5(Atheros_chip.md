---
title: "How to enable WPA...Belkin F5D7000 v5(Atheros chip)"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-02-28
Kubuntu Edgy...


The F5D7000(Atheros) works flawlessly out-of-the-box with WEP encryption!

I'd like to enable WPA2 with hidden ESSID.

Currently have WPASupplicant, Wpagui, Kwlan & NDISwrapper 1.8.

KWLan looks promising, but I've yet been able to figure out if WPA2 can be added easily, or if I have to run NDIS or Madwifi & manually configure the interface file?


Thanks for any help:popcorn:

---

### Post by wieman01 on 2007-02-28
Hidden ESSID used to be a problem with NetworkManager, the most popular tool for wireless connectivity. I suggest that you try the HOWTO in my signature first and see if it works for you.

---

### Post by DapperMe17 on 2007-02-28
Thank Wieman,

You helped me see the light with a prior WUSB54G.


What your saying is that WPA2 should be a similar venture, no matter which card, as long as initial connectivity exists?


):P

---

### Post by wieman01 on 2007-02-28
> **DapperMe17 said:**
> Thank Wieman,

You helped me see the light with a prior WUSB54G.


What your saying is that WPA2 should be a similar venture, no matter which card, as long as initial connectivity exists?
Hello DapperMe, 

Yes, that's what I am trying to say. :-) The HOWTO is particularly effective if you are using "ndiswrapper". My manual approach is not perfect, I would still recommend that you try out NetworkManager or other graphical tools. But the HOWTO serves the purpose of getting started... If you need help, you know where you find me. :-)

---

