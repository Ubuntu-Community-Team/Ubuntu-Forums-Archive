---
title: "setting up wpa with wireless"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by scriv316 on 2006-11-25
Hey guys

Ive looked around for guides on how to do this but most assume you are fairly familiar with basic commands on ubuntu, could someone provide some step by step instructions on how to enable wpa for use with a wireless network, I have it unsecured right now so I know it does work, thanks for any help you can give, as simply as it can be the better, this is my first time using linux so im primarily a windows user seeing the light now, thanks!

---

### Post by andreas64 on 2006-11-25
The most simlpy way is to use network-manager-gnome for this.

Andreas

---

### Post by scriv316 on 2006-11-25
thank you, where do i go to download this

Thanks

---

### Post by spd106 on 2006-11-25
It's in the main repo, so just open up Synaptic from the System -> Admin menu and search for network-manager.

Alternatively you can install it through Add/Remove programs from the Application menu, or even by typing **sudo aptitude install network-manager** at a terminal.


Once it's installed you will have to disable your card in the System -> Admin -> networking applet and restart gnome to allow network-manager to take control. Check out the help docs page for more details [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

---

