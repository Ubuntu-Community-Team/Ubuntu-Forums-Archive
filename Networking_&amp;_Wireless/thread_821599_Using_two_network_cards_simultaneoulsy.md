---
title: "Using two network cards simultaneoulsy"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by tobodestroyer on 2008-06-07
Hi,

I'm new to Ubuntu and I'm loving it.:guitar: However, I have just one problem...

I have two networks cards in my PC - one on the motherboard connected to my work place's network/intranet and a PCI network card connected to my BT Home-Hub and home network. The good news is that both of these work beautifully after a simple install of Ubuntu. (If only WinXP could have done it so easily).

The only problem is that I can't get Ubuntu to connect to both SIMULTANEOUSLY; this is where XP has the upper hand.

Is there a quick fix for this - It's be great if I could just press the two radio-buttons on the network icon simultaneously.

Many thanks in advance.

Tobo

---

### Post by SpaceTeddy on 2008-06-07
nm (network manager) does not support that. Linux itself has absolutly no problem with that setup.

Do you know what your network cards are called ? If not, open up a terminal, and type in ifconfig. This should give you an overview of the network cards installed. Then disable network manager and use type in
```
sudo dhclient %device
```
where device is the name of your network card (my guess is eth0 and eth1). that should connect you to both. 

As i said before, this is a problem of nm and not linux. It's been bugging me too. Tho i never really cared as i know how to work the command line.

Hope it helps :)

---

### Post by Unix_Slayer on 2008-06-07
I have two network devices working together. My wired is my intranet. My wireless is my internet. You have to do some modding in Linux to get them to work in unison. Why would you need both though?

---

