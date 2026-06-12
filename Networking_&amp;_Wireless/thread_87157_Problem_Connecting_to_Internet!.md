---
title: "Problem Connecting to Internet!"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by michaelzhao on 2005-11-07
A friend and I are in the school web design class. Our abilities far exceed any of the other kids in the class so we have a "independent" study course. Basically, we stay in a back room/storage room with 3 computers and goof off. Recently, we had a stroke of genius and decided to further the Linux revolution. We installed Ubuntu on one of the 3 computers.

After the installation, it was all good. However, we didn't configure the network during installation. We thought we could just do it later. So, today, I booted up Ubuntu, expecting to configure the installation. However, I don't have root access. So, I tried logging into the root in the terminal. Still I could not start the "Network Configuration" under the "System" then "Administration" tab. 

Quite literally, nothing happens. I click the "Network Configuration" option and it opens up a tab in the bottom. But it goes away. No error message. Nothing. Why is this problem occuring? Is there a way to configure the Network in the Terminal? How?

---

### Post by shinygerbil on 2005-11-07
It depends what you want to do with it.

A lot of people (myself included) find the Terminal the only way to configure network stuff... Search around a bit on these forums and you should be fine.

A good place to start is ifconfig - open up terminal and type man ifconfig, although this is pretty confusing... There are other programs which are also helpful; for example dhclient may help solve your problems. I use wireless, so my ethernet knowledge is a bit rusty, but perhaps you could try something like ```
sudo dhclient {interface}
``` where {interface} is the ethernet interface, often something like eth0. (you can find out which one to use by typing ifconfig with no options into the terminal.)

Steve

EDIT: Oh, and you probably don't want to use the root account too often ([this](https://wiki.ubuntu.com/RootSudo) page helps explain what to do instead, and why.)

---

