---
title: "Gnome network settings colliding with WICD"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Gyatak on 2008-01-11
Hey all,

I've got WICD running great on Gutsy. I do not have network manager installed, and I can't seem to get rid of the innate network location chooser. I have two problems, which I think are related:

[LIST=1]
[*]**System > Administration > Network** is maintaining tight restrictions on my freedom to roam. To go to new wifi locations, I have to use the Network location to establish the location. I'd really like to get Network out of this and let WICD take total control, since it seems to deal with roaming much more fluidly.
[*]I can't connect to unencrypted networks. This means I can't use wifi in coffee shops.[/LIST]I'm getting really tired of having to rejig my network locations every time I go from home to work to home. It often means I have to restart my laptop with the new settings in place in order to get my wifi card to kick in.

Can anyone help?

Thanks so much in advance,

Bill

---

### Post by jeffus_il on 2008-01-12
Maybe this is not your problem, but I solved my Wicd problem of not getting the ip address using DHCP by uninstalling the dbus dhcp client "dhcdbd" used by NetworkManager. Wicd uses "dhclient", there must have been a conflict.

---

### Post by Gyatak on 2008-01-13
> **jeffus_il said:**
> Maybe this is not your problem, but I solved my Wicd problem of not getting the ip address using DHCP by uninstalling the dbus dhcp client "dhcdbd" used by NetworkManager. Wicd uses "dhclient", there must have been a conflict.

Thanks, Jeffus.

I've removed dhcdbd, and will see if I have any luck next time I'm in an internet cafe.

Do you think there could be a conflict between dhclient and dhcp3-client, the innate Ubuntu dhcp client? When I tried removing it, it wanted to remove ubuntu-minimal, too, so I canceled the operation.

---

### Post by kevdog on 2008-01-13
A little off topic, but if at an internet cafe, Id recommend tunneling your internet connection back home through ssh/socks proxy for security reasons.

---

