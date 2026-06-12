---
title: "DWL 520+ not working."
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by sparX CG on 2007-02-27
Hi everyone.

I'm having trouble setting up my brother's wireless card in Edgy.  Fresh install, updated, installed NetworkManager.

Here's the problem.  NetworkManager detects the card and all, but refuses to connect.  It can detect wireless networks floating around but when my brother clicks connect, it keeps spinning around and around without connecting.  Not a single light lights up.  Tried erasing the junk from /etc/network/interfaces, same thing.

lspci outputs the following for his card:

Texas Instruments ACX 100 22Mbps Wireless Interface

It's a D-Link DWL-520+ Wireless B Card.

Any ideas why it would do this?

---

### Post by Floppyjoe on 2007-02-28
Do you have all the network interfaces disabled in System/Administration/Networking?
If you are using Network-Manager you need to do this.
Also all the network interfaces except for the lo interface should be commented out in /etc/network/interfaces.
That is adding # in front of the lines there.

Floppyjoe

---

### Post by bcheng81 on 2007-02-28
I'm the useless n00b brother who can't get the wifi to work.

Actually, I kinda jiggled around with System/Administration/Networking and got it to work in that setup, bypassing the Network Manager altogether.

Well, since I'm using it in a desktop environment and won't be connecting this machine to any other network, I'll leave it this way.  Thanks for your help!

-B

---

