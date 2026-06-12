---
title: "Why can't I easily get a DHCP address when I go to different locations?"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by SnowPunk98 on 2007-05-31
I am a network consultant and go to different networks almost every day. Almost every time I plug in and boot up I log in and don't get a network address. If I boot up in Windows everything works perfectly fine. I am logging into a Windows network every time but DHCP should be DHCP. I have tried manually configuring an address (which I don't want), I have tried restarting networking, I even just reinstalled Ubuntu because I thought something might have been wrong with my system since I had just done upgrades from herd 5.

Anyways can anyone help me figure out why networking is so poor? I would like to be able to just plug in and get a DHCP address when I go to different clients so I don't have to work in Windows.

EDIT: If it matters I am on a Dell Latitude D800 with a Broadcom 570x Gigabit onboard NIC and am using Feisty.

---

### Post by x64Jimbo on 2007-05-31
What does your NetworkManager say about the connection? is it even trying to connect first, then failing?

---

### Post by SnowPunk98 on 2007-05-31
It always says its connected

---

### Post by scrooge_74 on 2007-05-31
Maybe try In the network manager tell the card to work on traveling mode (not sure of the translation mine is in spanish)

---

### Post by SnowPunk98 on 2007-06-01
Ive tried roaming mode also with no success, I dont see why I couldnt just do DHCP thats pretty roaming status.

---

### Post by x64Jimbo on 2007-06-02
If it says that it's connected, then it has gotten its DHCP address. Part of the connection process is getting assigned an IP address unless it's already been assigned manually.

---

