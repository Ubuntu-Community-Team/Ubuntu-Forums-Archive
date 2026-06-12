---
title: "Wireless not working after installing ubuntu 7.04"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by austraind on 2007-05-16
Hi All,
I have a Dell XPS laptop with Intel 2200BG network card. I had installed 7.04 a week back and since then have been trying to configure my wireless, but it just doesnt seem to come up.
I have tried many options that i came across in the forum, but none has worked.
Options i tried:
1. Using the default Network-manager.  DIDNT WORK.
2. I then installed ndiswrapper, along with ieee80211 and firmware files(ALL LATEST VERSIONS). AGAIN DIDNT WORK
3. I then uninstalled 'nm' and tried WICD. AGAIN DIDNT WORK.

Can anyone help me out here?

For your information:
I am using a wireless connection with WEP, and a network key is assigned to me automatically by the router and its not a static IP configuration.

Thanks,
austraind

---

### Post by austraind on 2007-05-20
Well,

Having waited for sometime and without anyluck, i had been looking all over the place, and guess wat?
I finally got my network working by using "wpa_supplicant".
Now it connects really well.

ubuntu rocks,
austraind

---

