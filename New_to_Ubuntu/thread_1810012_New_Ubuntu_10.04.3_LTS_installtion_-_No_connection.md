---
title: "New Ubuntu 10.04.3 LTS installtion - No connections available"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by User_ on 2011-07-22
I did a fresh installation of Ubuntu 10.04.3 LTS and it seems that Ubuntu has a problem finding my wireless connection, which btw works great on Windows 7. I looked through the help files and I found that Ubuntu can find and automatically connect to a wireless network provided that I have connected before. The thing is that it does not even pick up my connection. Any tips? Should I try the "Network Connections" option and enter the information myself? Thanks in advance!

---

### Post by howefield on 2011-07-22
Are you able to connect wired ?

If so, try System > Administration > Hardware Drivers to see if there are drivers for your wireless adapter waiting to install. (might be called Additional Drivers)

You'll probably want to do a sudo apt-get update before trying for additional drives if you haven't already.

---

### Post by halitech on 2011-07-22
does it see your network card? is it a laptop or desktop? internal (PCI card) or external(USB)?

---

### Post by User_ on 2011-07-22
> **howefield said:**
> Are you able to connect wired ?

Nope.. I can't even connect wired. It doesn't see it either.

---

### Post by User_ on 2011-07-22
> **halitech said:**
> does it see your network card? is it a laptop or desktop? internal (PCI card) or external(USB)?


It is a laptop, Windows can see my network card but I don't know about Ubuntu (probably doesn't?) with an internal (PCI card).

---

### Post by halitech on 2011-07-22
> **User_ said:**
> It is a laptop, Windows can see my network card but I don't know about Ubuntu (probably doesn't?) with an internal (PCI card).

ok, laptop doesn't mean it will be a pci card, I've seen alot that end up showing under usb.

open a terminal and run the following commands and post the output here

```
sudo lspci
```and
```
sudo lsusb
```

---

### Post by Snowboi on 2011-07-25
Did you try it on another version of ubuntu?

---

### Post by amjjawad on 2011-07-25
```
sudo lshw -C network

```

Please post the output here and wrap up the text with "#" or "CODE" tags.

---

### Post by sadaruwan12 on 2011-07-25
Other wise if all else fails you could use the ndsiwrapper and in 10.04 if the chipset is a realtek based then this type of thing happens.

I'd the same issue to get connected or even to see the network I'd to go and stand right under the wireless router.

But I managed to fix it but you want find this issue in 11.04 it works right out of the box (at least for me).

If you want to know how to use the ndsiwrapper [click here]("http://myfossness.blogspot.com/2010/05/how-to-get-rtl8187b-working-in-ubuntu.html").

---

