---
title: "WPA with NetworkManager stopped working"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by MikeNick42 on 2006-10-10
I've been using WPA through NetworkManager for several months at least. All of a sudden a couple days ago my connection stopped working. I can still connect to non-protected networks, but my WPA protected network can not connect.
I have an ipw2200 wireless card.
If any one can help I'd really appreciate it. Thanks.

---

### Post by TheWizzard on 2006-10-10
what is your output of
```
cat /etc/network/interfaces
```

---

### Post by MikeNick42 on 2006-10-10
Here's my output from cat /etc/network/interfaces

```
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth1
# The primary network interface
#iface eth1 inet dhcp
#       # wireless-* options are implemented by the wireless-tools package
#       wireless-mode managed
#       wireless-essid <my-essid>
#iface eth0 inet dhcp
```

One of the other posts in here said all interfaces except lo should be commented out to use NetworkManager but I haven't touched that file in a long time, so I'm not sure if it was changed by a recent update or something like that.

---

### Post by MikeNick42 on 2006-10-10
I was able to get my wireless to work again by turning "Protected Mode" (not hidden essid) off on my router. The only thing I'm still not completely comfortable with is the fact that I only turned Protected Mode on because I was having this problem connecting to my router.
Thank you for your help Wizard.

---

### Post by TheWizzard on 2006-10-11
> **MikeNick42 said:**
> I was able to get my wireless to work again by turning "Protected Mode" (not hidden essid) off on my router. The only thing I'm still not completely comfortable with is the fact that I only turned Protected Mode on because I was having this problem connecting to my router.
Thank you for your help Wizard.

good to hear you got your stuff working. i'm not using gnome, so i can't help you with networkmanager. 
you do have your wlan protected with a wep-key? 

cheers

---

