---
title: "Dell C640 Modem"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by MoonBlossom on 2007-06-11
Hello,

I have a Dell C640 laptop and I'm trying to get the modem to work. I read the modem installation wiki and I'm able to compile the modem driver but when I do "modprobe" I get a segmentation fault error.

I tried installing both Intel536 and Intel537. I hope somebody can help me, I'm going to go on a trip outside the US and the place where I'm going to be staying only has dial up :(

---

### Post by progik on 2007-08-20
Can already late, but all the same I shall answer. Somebody will be useful
For installation modem on Dell Latitude C640 necessary to install only one package sl-modem-daemon 
[http://packages.ubuntu.com/feisty/misc/sl-modem-daemon](http://packages.ubuntu.com/feisty/misc/sl-modem-daemon)

For convenience of dialing use Gnome-ppp
[http://packages.ubuntu.com/feisty/net/gnome-ppp](http://packages.ubuntu.com/feisty/net/gnome-ppp)

---

