---
title: "adding a network adapter"
date: 2005-09-24
forum: Networking &amp; Wireless
---

### Post by simonkitch on 2005-09-24
My Hoary system started out with a ethernet network adapter. I have now disconnected from the wired network and have added a Netgear MA311 wireless adapter. On rebooting the Wireless adapter was not detected. I'm not sure how to add the device manually? The lan card is still fitted an is set as eth0.

---

### Post by mlomker on 2005-09-24
I'm not sure what chipset that uses.  Try **lspci** at a prompt and look for the card information.

---

### Post by simonkitch on 2005-09-24
Its a prism. Question is how do I get Hoaryto use it?

---

### Post by mlomker on 2005-09-24
[QUOTE=simonkitch]Its a prism. Question is how do I get Hoaryto use it?[/QUOTE]

Try **sudo modprobe prism54** and then type **iwlist** at a prompt to see if you can see the card listed.  

If that works then the general process is to add a line for that interface to the /etc/network/interfaces file and then add the name of the module to the end of the /etc/modules file.

Let me know if the first step works and we'll look at the rest.

---

### Post by simonkitch on 2005-09-25
did sudo modprobe prism54
then iwlist, saw just a list saying interface, bitrate etc with no data an no mention of a wireless adapter?

---

### Post by mlomker on 2005-09-25
Is your adapter a PCI card or USB?  The USB adapters have to use [ndiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper), but I've found some other posts saying that the PCI version is suppoed to work with the native driver.

---

### Post by fordfan753 on 2005-09-25
I actually have a prism, and can say that while some will work with the prism54 module others will not. Mine will not, so I just use ndiswrapper. Ndiswrapper is fairly easy to set up.

Oh, on a side note, how do you get the kernel to stop loading the prism54 module automatically every time I plug in my card? The module *does not* work with my card, and has to be unloaded before I load ndiswrapper, which is a bit of a pain.

---

### Post by mlomker on 2005-09-25
> Oh, on a side note, how do you get the kernel to stop loading the prism54 module automatically every time I plug in my card? The module *does not* work with my card, and has to be unloaded before I load ndiswrapper, which is a bit of a pain.

Add the driver to the /etc/hotplug/blacklist file.

This only seems to work for hotplug modules, though.  I'd love to use it to keep the kernel from loading certain default modules, but that doesn't work (I'd rather not use a custom kernel for compatibility reasons).

---

### Post by fordfan753 on 2005-09-27
[QUOTE=mlomker]Add the driver to the /etc/hotplug/blacklist file.

This only seems to work for hotplug modules, though.  I'd love to use it to keep the kernel from loading certain default modules, but that doesn't work (I'd rather not use a custom kernel for compatibility reasons).[/QUOTE]

Thanks for that :)
I can see benefits of what you're talking about too, being able to stop the kernel loading cetain modules.

---

