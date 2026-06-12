---
title: "WPA wireless with ipw2200"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by lost+found on 2006-10-03
HI,

Im sure this has probably been asked about countlessly, so sorry about the recursivness here, i just starting with ubuntu...
After following various guides from googling the problem, I have yet to establish a proper communication with my wireless network. There are probably other troubles as well like the fact that gcc is installed (by default) yet when I try to compile something it will tell me no C compiler present in $PATH...anyways the wireless problem is such that I cannot actually install any KNetworkManager or such so I have to rely on wpa_supplicant to do the job. By following some tutorials on it, I have only managed to get it to connect to some "default" network that appears in my neighbourhood (it doesnt have a key required). When i try to then say use the iwconfig to change essid, hoping that the other settings in wpa_supplicant will be preserved such as the passphrase, every other thing goes straight to oblivion and i don't even get a bitrate anymore...

Any help would be greatly appreciated....

---

### Post by lcg on 2006-10-03
> **lost+found said:**
> After following various guides from googling the problem, I have yet to establish a proper communication with my wireless network. There are probably other troubles as well like the fact that gcc is installed (by default) yet when I try to compile something it will tell me no C compiler present in $PATH...
Actually, gcc is **not** installed by default on Ubuntu. That's probably the reason why your shell cannot find gcc in your path. Just an educated guess ... ;)

Oh, and ipw2200 works fine with WPA, no compiling it yourself involved.

> **lost+found said:**
> anyways the wireless problem is such that I cannot actually install any KNetworkManager or such so I have to rely on wpa_supplicant to do the job.
Why can't you use network-manager? It works wonderfully with my wireless connection. And if you have a chicken/egg problem, just dectivate WPA on your wireless for a few minutes, install network-manager (and a frontend) and re-enable WPA. The content of some .deb packages is probably not such a big secret ... ;)

HTH,
Lars

---

