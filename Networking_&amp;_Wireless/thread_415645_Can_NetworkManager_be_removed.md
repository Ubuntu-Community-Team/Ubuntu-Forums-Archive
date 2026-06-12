---
title: "Can NetworkManager be removed?"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Metz on 2007-04-20
Oppps...I really should know better than to rebuild my machine just before I really need it.

My laptop was running beautifully on Edgy for a few weeks, wireless working fine, beryl for eyecandy. I was very pleased. But I'd only upgraded to Edgy as an interim...waiting for Feisty. Yesterday, I downloaded the i386 desktop iso and reinstalled my laptop from scratch, using the whole disk this time.

Sadly, I'm now suffering major networking issues. The laptop has an Intersil Prism 2.5 wavelan card, the router is fully closed off...WEP enabled (have to use WEP as other machines on the network won't support WPA), nothing allowed to connect if it's not known, and NO dhcp. Every machine on the network has a fixed IP.

Apparently, NetworkManager doesn't like that very much. Well...the feeling is mutual and fully reciprocated. So....is there any way of disableing/ removeing it completely?

Thanks :) 

[SIZE="1"]I look about 10 years older now....I've been at this for about 24hrs solid now.....argh !!![/SIZE]

---

### Post by mexlinux on 2007-04-20
Yes NetworkManager is really annoying, now I know it's designed by the gnome guys, that explains why it works like that:

> someone at gnome decied that using dhcp is the easiest whay to connect to the network, and that is the only way that is not going to confuse my grandma.....

try:
> sudo apt-get remove networkmanager

---

### Post by RomeReactor on 2007-04-20
Hi. I think that's

```
sudo apt-get remove network-manager
```

---

### Post by steve0921 on 2007-04-27
Hi,

I am running feisty (which decided it wanted to install network manager) and am having problems with this. I do not have the network-manager package installed, but I still have a NetworkManager process running on my system and corresponding scripts in /etc/init.d and /etc/rc*.d

What package do these belong to if I want to remove them? (It seems to always erase me resolv.conf which is very frustrating)

Thanks,
-Steve

---

### Post by RomeReactor on 2007-04-27
HI. When you uninstalled network-manager, did you do that from Synaptic? and, did you remove *only* **network-manager-gnome**? Do a search in Synaptic for "network manager"; it should return about seven results. Make sure all are uninstalled.

---

### Post by Samma3l on 2007-04-28
Reversal of Fortune...

I managed to uninstall the Network Manager via the add/remove tool, and  now I'm unable to surf the internet. It can see the wireless network, and it says it has connected, but still no joy. I'll find a solution soon...

---

### Post by RomeReactor on 2007-04-29
Hi. Try installing [WICD]("http://wicd.sourceforge.net/"); see if that helps.

---

### Post by mexlinux on 2007-04-29
Try wlassistant

---

