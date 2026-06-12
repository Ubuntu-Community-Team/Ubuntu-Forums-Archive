---
title: "Best way to share seamless desktop between Ubuntu and Windows"
date: 2017-06-08
forum: Networking &amp; Wireless
---

### Post by sisyphus84 on 2017-06-08
Hi,

I have a Windows 10 machine on which I can not sadly install Ubuntu due to kernel conflicts with the AMD Ryzen and gigabyte board. I would like to work on this computer from another laptop which has Ubuntu 14.04. I've already tried Remina using RDP but the experience is not smooth and it seems it could create issues in the long run. I've also tried RealVNC server with client on Ubuntu end, but it turned out to be even more slower and laggy. I would like to work seamlessly on the server. Is it possible to do that somehow?

Best,

---

### Post by gordintoronto on 2017-06-08
I've had better results with KRDC. Watch out: if it's your first "K" package, it's a huge download. (I also use K3B.)

Another option is Teamviewer: proprietary, but free for personal use.

---

### Post by sp40140 on 2017-06-08
Performance depends on the quality of your network and monitors / resolution. Also the settings for vnc / rdp.. either optimized for quality or speed.
Windows to windows rdp will be very fast due to proprietary nature of the protocol.

---

### Post by QIII on 2017-06-08
The very best performance I have ever gotten is with NX.  NoMachine provides a free, but not open source, NX environment with built-in ssh.  Over the last few years NoMachine has gotten so good that it is almost ... *almost* ... good enough to render video between machines.  But you won't be able to watch your favorite super-hero movie.  News clips maybe.

I use it in the opposite direction you are talking about, however.  I sit at my Linux computer and NX to my Windows machine.  But you can NX from Windows to a Linux machine.

---

### Post by sisyphus84 on 2017-06-09
Thanks for the suggestion. I've installed the NoMachine on both computers. I can log into ubuntu machine from windows 10 machine but not the other way around. In-fact ubuntu machine can not even see the windows 10 machine. I have tried to see if firewall at the windows end is blocking the port but it seems all OK. In the firewall, I could see that server for NoMachine is allowed all ports for UDP and TCP, however I am unable to see any NX protocol in the list. Is it normal? Since it is free version, therefore, I can not test on SSH. Could you tell what is blocking the connection? I've also tried putting an exception in the router for that port but then again there is not NX protocol in the router either.

---

