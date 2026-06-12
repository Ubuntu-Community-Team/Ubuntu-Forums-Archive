---
title: "Wireless Problems"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Crimsunwulf on 2008-05-29
Okay, I have been able to connect to wireless networks perfectly fine for awhile now.  My family has a new home, and until we get wired network throughout, my dad finally bought a wireless router to make do.  We have a WEP 128 bit encryption to secure it.  However, whenever I go to connect, if I choose open network or whatever it tries to connect for a bit and then gives up and asks for the security key again.  If I choose shared key it tries to connect for a bit then gives up and doesn't ask again.  Yes, I am certain I am using the correct key, before anyone asks.  The network driver is Broadcom B43.  I tried to open hardware information to find my card type but it won't open for some reason.  The laptop is a Dell latitude D620 if that says anything.

I forgot to say this.  If I go to administration>network, turn roaming off on wireless and connect that way, I connect but I can't do anything.  No pages will load or anything.

---

### Post by Ayuthia on 2008-05-29
> **Crimsunwulf said:**
> Okay, I have been able to connect to wireless networks perfectly fine for awhile now.  My family has a new home, and until we get wired network throughout, my dad finally bought a wireless router to make do.  We have a WEP 128 bit encryption to secure it.  However, whenever I go to connect, if I choose open network or whatever it tries to connect for a bit and then gives up and asks for the security key again.  If I choose shared key it tries to connect for a bit then gives up and doesn't ask again.  Yes, I am certain I am using the correct key, before anyone asks.  The network driver is Broadcom B43.  I tried to open hardware information to find my card type but it won't open for some reason.  The laptop is a Dell latitude D620 if that says anything.

I forgot to say this.  If I go to administration>network, turn roaming off on wireless and connect that way, I connect but I can't do anything.  No pages will load or anything.

Have you tried connecting to it without network manager?
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

Here is a link on how to connect manually if you have not tried it before:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

