---
title: "Connect Win-laptop to Internet via Linux pc"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by igor4u on 2005-07-28
I have pc with installed Ubuntu connecting to Internet via local netwrk.
I need to connect my Win-laptop to Internet via pc.
As i understand i should run pc as proxy?

How could i do this?

---

### Post by theturner on 2005-07-28
Wait... you've got a home network with a router (or cable modem, or similar) and your Ubuntu PC attached to it? If that's so, you don't need to configure anything on the PC. Just connect the Laptop to the network and it should reach the internet all right, no matter if your PC is on.

If your PC is the only link between your network and the internet (eg. when you're using two network cards or a modem), you need to set up NAT (network address translation) on your PC to forward connections to other computers on the network. The easiest way to achieve this is to install **firestarter**, it has a nice graphical assistant for configuring such things.

---

### Post by tallone75 on 2008-04-14
This is quite an old post so I have to ask again in case something changed.

I have a laptop running windows and a pc running ubuntu which is connected to an adsl modem.
I want to connect the laptop to the ubuntu pc with a UTP cable in order to access the internet.
I understand that a server must run in the ubuntu pc in order to serve the laptop.

Will this be accomplished by installing  **firestarter** or is there a newer approach with ubuntu 7.10?

      Thank you.

---

