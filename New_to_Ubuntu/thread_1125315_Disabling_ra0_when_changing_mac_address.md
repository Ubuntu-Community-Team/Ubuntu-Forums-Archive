---
title: "Disabling ra0 when changing mac address"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-14
I am trying to change my mac address, as shown in this guide [http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html](http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html)

I try to run the command,

sudo macchanger ra0

and it tells me

ERROR: Can't change MAC: interface up or not permission: Device or resource busy

How do I turn off the device so it isn't busy?

---

### Post by hovzio on 2009-04-14
```
sudo ifconfig ra0 down
```

That should do the trick, replace "down" with up to start it up again.

Edit: you may also need to stop networkmanager. I don't know what your up to..

```
sudo /etc/init.d/NetworkManager stop
```

---

### Post by alanfang on 2009-04-14
When I try to do the second command the networkmanager stops it says,

Ignoring unknown interface ra0=ra0.

any way I can make it a known interface?

---

### Post by hovzio on 2009-04-15
> **alanfang said:**
> When I try to do the second command the networkmanager stops it says,

Ignoring unknown interface ra0=ra0.

any way I can make it a known interface?

I'm not sure. I "think" this may not be of all to great importance. I'm not entirely sure.. can only speak about my personal experience; I have an atheros wifi card, it seems that it is creating 2 interfaces. wifi0 and ath0. ath0 (in my case) is the main thing to look at. (when using wireshark etc. I refer/specify ath0, wifi0 gives the same error you mentioned) What I'm trying to say, I get the same message rather often but it doesn't affect anything, or whatever it is I'm trying to do. (mainly creating ad-hoc sessions)

When you use sudo "/etc/init.d/N...manager stop" you are just turning of ubuntu's network manager which *can* in some cases be bothersome when playing with network settings. This actually has little to do with disabling ra0. After you do a sudo ifconfig ra0 stop; ra0 will/should be disabled. I havent tried the prog. you mentioned. It may or may not be necessary to turn off N.Manager for your needs, I would try leaving it on first. Play around, try only disabling ra0 and then try macchange. Copy the axact output you get in a terminal when macchange fails. :)

EDIT: If you already disabled ra0, then this could very well be the reason that NetworkManager is complaining, it is trying to contact an interface that is shut down..can be ignored. I would try macchange without disabling NM first.

---

