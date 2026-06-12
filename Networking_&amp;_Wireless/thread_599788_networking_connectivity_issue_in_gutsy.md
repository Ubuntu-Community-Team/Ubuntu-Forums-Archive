---
title: "networking connectivity issue in gutsy"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by shyamsg on 2007-11-01
I have installed Gutsy newly on my HP laptop with Intel 3945 ABG wireless card built in. The network manager has some connectivity issues. I have a netgear router with WEP 64-bit encryption. When I remove the encryption, everything seems to work fine. If I use the encryption, the network manager does not want to connect at all.  The laptop connects to the unencrypted netwoks that my neighbors have. 
I had edgy before this and all was good.
Any help is appreciated.

Thanks
Shyam

---

### Post by macgreagoir on 2007-11-01
I'm using Kubuntu Gusty with ipw3945, and WEP 128 Hex on a Netgear router/access point. The only issue I had was in trying you use the manual config option, which screwed up knetworkmanager. Deleting the wlan (eth1) adapter's lines from /etc/network/interfaces fixed it. That might be worth a look if you done any manual configuration, and you're using knetworkmanager.

It is still very flakey after waking from Hibernate, but otherwise works fine.

---

### Post by shyamsg on 2007-11-01
I have gnome. I use the gnome network manager. I tried to use manual config when I had edgy and it did mess up the network manager. I am really confused about why it does not work when i use any kind of encryption. I will try manual config now and see what happens.

Thanks

---

### Post by macgreagoir on 2007-11-02
Sorry to ask obvious questions, but are you entering the encrypted key in Network Manager or the real word that you used to create it? Do you have the correct type (ASCII or Hexadecimal)?

Has encrypted wireless worked on this router previously?

---

### Post by shyamsg on 2007-11-04
Update on the issues, I was using this router with feisty and it worked just fine, WEP and all. I switched to gutsy and was having problems. My router only supported WEP. I tried both network manager and wicd, but both had issues with WEP. I also tried the passphrase and hex codes but to no avail. I abandoned the guis and tried terminal connection but the same issue. 
I finally went out and bought a new router that supports WPA. Finally everything works just fine. Guess the problem was WEP. Dont know why. Thanks for all the help.

Shyam

PS: I tried the WEP with the new router but again no success.

---

