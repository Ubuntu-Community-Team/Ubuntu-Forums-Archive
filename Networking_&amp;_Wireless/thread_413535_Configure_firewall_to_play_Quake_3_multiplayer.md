---
title: "Configure firewall to play Quake 3 multiplayer"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by Prism on 2007-04-19
Hi there,

I've installed Quake 3 on my Ubuntu machine using this howto: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

I'd like to play Quake in a multiplayer mode with another computer in a LAN network. Unfortunately, when I open a server, the remote machine doesn't see it. The remote machine is running Windows.

What steps should I follow in order to allow remote LAN computers to enter my server? I use the shorewall firewall, but a iptables script will do, I think.

Thanks!

---

### Post by Prism on 2007-04-20
Bump. :)

---

### Post by Prism on 2007-04-21
Please? Someone? It breaks my heart, booting to Windows to play a game I can play on linux...

---

### Post by lothar.swe on 2007-04-21
Enable traffic through UDP port 27960 in your firewall. Also configure your router's virtual server to point at your computer for inbound UDP port 27960 traffic.

Happy fragging! /Lothar

Btw, connect to Lothar's Team Arena server on 85.24.132.56. Always running.

---

### Post by Prism on 2007-04-23
Almost there. I opened those ports and ran quake. I created a server, but when I try to enter it from another machine in a LAN, I get a "client unknown to auth" error message.

If I open the server on the other machine, and try to enter it from my ubuntu box, I get a "mis-typed cd key" error. However, I know that my cdkey is valid because I use it on my Windows version of quake.

---

### Post by lothar.swe on 2007-04-23
On your Q3 server computer, edit your home/.q3a/baseq3/q3config.cfg file with Gedit. The .q3a folder is a hidden folder, which is revealed by pressing ctrl-h in Nautilus. Find the sv_strictAuth entry. Alter it to:

seta sv_strictAuth "0"

If it doesn't exist, just add it somewhere in that file.

That's all. Good luck!

Btw, admit my replies are remarkably quick. :-)

---

### Post by Prism on 2007-04-23
It works perfectly well! Thank you!

BTW, thanks for your speedy replies, I wish I could answer you in such a timely manner. :D

---

