---
title: "&quot;ifupdown (eth0)&quot; default connection"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by CorsairFreak on 2013-09-22
Hello all,

I've installed a Lubuntu core system following [this guide]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). Aside from the Lubuntu core I've only installed a handful of other programs including: synaptic, lxinput, gdebi, leafpad, gksu, steam, and AMD graphics drivers. The issue I'm having (which I've also encountered everytime I've tried to build a minimal\core Ubuntu derivative) is setting up a static IP. 

Following the aforementioned guide I edited the "/etc/NetworkManager/NetworkManager.conf" file:
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=**true**


```
This made the Network Manager applet visible so I could add my preferred network settings and make it the default connection which I've done successfully. Yet, everytime I reboot "ifupdown (eth0)" is the connection in use, not the connection I set up. I can manually switch to my connection by left-clicking the Network Manager applet and selecting my connection, but after a reboot it will revert back to "ifupdown (eth0)". The Network Manager will not allow me to edit or delete the "ifupdown eth(0)" connection so how can I set mine as the default?

---

### Post by CorsairFreak on 2013-09-24
Finally, after playing around with minimal Ubuntu derivatives for a few years I've figure it out on my own. I compared the */etc/network/interfaces* file of a full Lubuntu install to my Lubuntu core install using VirtualBox and noticed a difference.

[B]Lubuntu
[/B]```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

**Lubuntu core**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 iface eth0 inet dhcp

```

As you can see, the Lubuntu core has an added section. Personally, I do not know enough about Linux or Ubuntu to explain why, but removing that additional section removes "ifupdown (eth0)" and adds a new connection that can be edited or deleted and stays as your default connection even after reboot.

---

### Post by varunendra on 2013-09-26
Hello CorsairFreak, Welcome to the forums !

Here's some explanation that you may find useful in your adventure with Ubuntu :

If you are going to use Network Manager to manage an interface (eth0 in your case), then the /etc/network/interfaces file is not supposed to manage it (two managers managing the same thing = confusion/conflict).

The line "managed=false" is there in the NM settings to avoid such possible conflicts. It simply tells the NetworkManger to "Ignore" all those interfaces that are being controlled by the /etc/network/interfaces file.

By changing it from "false" to "true", you told NM to 'Not' ignore them. It did so and allowed you to add/edit the configuration. But it still assumes that connection to be the default one.

The easiest and recommended fix is to just leave the interface be managed by either the interfaces file, or the Network Manager. That's what you did by deleting the lines from the interfaces file.

Hopefully, it makes your decision/actions a bit clear next time. Since the problem is solved and you posted a clear solution on how, please mark the thread as [SOLVED] using the "Thread Tools" link above the top post. It helps others by indicating that the thread contains a possible solution to the topic.

Happy Lubunting ! :)

---

