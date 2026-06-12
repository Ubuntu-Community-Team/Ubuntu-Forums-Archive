---
title: "Autoconnect to openvpn on startup without re-typing username and password?"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by sean119 on 2016-05-15
I've recently purchased a membership to Private Internet Access, and I'd like to use it on my system. I put the .ovpn file in my */etc/openvpn* directory, and renamed it to a *.conf* file, so it runs the *openvpn --config myvpn.ovpn  *command when I boot. When I do this, I can connect, but I have am prompted to input my username and password, which is a real pain to do. Does anyone know a script or command I can use to auto-fill the username and password when I boot? Thanks!

---

### Post by sean119 on 2016-05-25
It took some digging, but I got it. To anyone in my situation, go to the  'auth-user-pass' line in your config file then change it to  'auth-user-pass /etc/openvpn/yourInfo.txt'(Directory and name don't  matter). The file should be two lines, one being your username, and the  other being your password. Good luck!

---

