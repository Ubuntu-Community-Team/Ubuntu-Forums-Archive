---
title: "My wireless card isn't recognized?"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Masterion on 2009-12-25
I'm running Ubuntu Linux version 9.10 (Karmic Koala) from a virtual PC (the host is Windows 7 Home Premium 64-bit, by the way, if it makes a difference) and, whenever I boot up Linux, it doesn't recognize my wireless card, which is a Atheros AR9285 802.11a/b/g/n Network Adapter. Is there any reason as to why it won't recognize? How can I make it recognizable?

---

### Post by bkratz on 2009-12-25
Check out post 2 of this thread

[http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285](http://ubuntuforums.org/showthread.php?t=1286503&highlight=AR9285)

---

### Post by ugm6hr on 2009-12-25
What "Virtual PC" software are you using to host Ubuntu?

Virtualbox does not require any Ubuntu drivers for network connectivity.

---

### Post by Masterion on 2009-12-25
> **ugm6hr said:**
> What "Virtual PC" software are you using to host Ubuntu?

Virtualbox does not require any Ubuntu drivers for network connectivity.

Windows Virtual PC

---

### Post by Masterion on 2009-12-25
Anyone?

---

### Post by sandyd on 2009-12-25
> **ugm6hr said:**
> What "Virtual PC" software are you using to host Ubuntu?

Virtualbox does not require any Ubuntu drivers for network connectivity.
i think hes saying that micosoft virtual PC screws up his wireless connnection on his laptop.

@OP in this case, use virtualbox instead of Virtual PC - it was never meant to run ubuntu.

---

### Post by Masterion on 2009-12-25
> **carlee said:**
> i think hes saying that micosoft virtual PC screws up his wireless connnection on his laptop.

@OP in this case, use virtualbox instead of Virtual PC - it was never meant to run ubuntu.

Okay, tried that, but the adapter is STILL not recognized.

---

### Post by sandyd on 2009-12-25
> **Masterion said:**
> Okay, tried that, but the adapter is STILL not recognized.
are you talking about the wireless conenction in ubuntu, or the wireless connection in windows.
there _should_not_ be a wireless connection in ubuntu since your running it in a virtual machine.

---

### Post by Masterion on 2009-12-25
Ubuntu

---

### Post by sandyd on 2009-12-25
> **Masterion said:**
> Ubuntu
virtualbox/microsoft virtual pc **does not **emulate wireless devices
it only emulates wired devices.
so although you may have a wireless connection in windows, you will_not have a wireless connection in ubuntu, but instead a virtual wired connection that feeds back into the wireless connection of vista/win7

---

### Post by Masterion on 2009-12-25
> **carlee said:**
> virtualbox/microsoft virtual pc **does not **emulate wireless devices
it only emulates wired devices.
so although you may have a wireless connection in windows, you will_not have a wireless connection in ubuntu, but instead a virtual wired connection that feeds back into the wireless connection of vista/win7

Then how does that work?

---

### Post by HereInOz on 2009-12-25
If you are using a Local Area Connection wireless connection, then if you use VirtualBox, the virtual machine should pick up on the network connection of the host machine but if you are using a USB wireless broadband type of thing, it can be more difficult.

In this case, and if you have any networking difficulties, what you need to do is to run VirtualBox, then set your networking for the virtual machine in VirtualBox to NAT, rather than bridged.

This way, the host machine establishes the wireless broadband connection, then the guest machine establishes a virtual network connection to the host machine, which then routes traffic from the guest machine to the wireless broadband network.

In either case, allow the host machine to do the network connection, then the guest machine will connect to the network adaptor of VirtualBox, and thence to the host machine.

Do not expect to see the network adaptor of the host machine in the virtual machine.

---

### Post by sandyd on 2009-12-25
> **Masterion said:**
> Then how does that work?
virtualbox will emulate wired connection for ubuntu.
the emulated wired connection connects through your wireless of your computer

---

### Post by droadtrip on 2009-12-26
> **carlee said:**
> i think hes saying that micosoft virtual PC screws up his wireless connnection on his laptop.

@OP in this case, use virtualbox instead of Virtual PC - it was never meant to run ubuntu.

[FONT=Georgia][SIZE=3][COLOR=Navy]That's why I don't like using Virtual Machines. I like to burn ISO's to a Live USB and test off of that. Then if it's worth it, I install it to a Pre-allocated empty space on my hard disc. [/COLOR][/SIZE][/FONT]

---

### Post by ugm6hr on 2009-12-26
> **Masterion said:**
> Then how does that work?

I think you need to do a bit more research into what a "Virtual Machine" does, and how it works.

I'm afraid I have zero knowledge of Virtual PC, so can't help.

You'd be better asking on a Windows / MS forum, since I can't imagine very many Ubuntu users (even those who use it in a VM) use Virtual PC.

As has been suggested before, VirtualBox is free (there is even an open-source version) which will allow you to do what I think you are trying to do.

Nevertheless, installing Ubuntu in a VM will never detect your wifi (or wired) card.  It creates a virtual interface to the host (i.e. Windows) which appears as a wired interface.  Hence, to use wifi from within the VM Ubuntu, the connection is dependent on having wifi correctly set up in the host (i.e. Windows).

---

