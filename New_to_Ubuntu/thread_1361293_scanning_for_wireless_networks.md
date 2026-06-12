---
title: "scanning for wireless networks"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by beano0528 on 2009-12-21
Anyone know how to do it?

---

### Post by kermiac on 2009-12-21
You might want to try "sudo iwlist scan" from the terminal.

Hope this helps :)

---

### Post by juancarlospaco on 2009-12-21
yes..., its kinda automatic, 
wifi networks just come up on the network icon when you click it.
You can connect to invisible networks too using the proper option,
and create your own wifi network.

---

### Post by beano0528 on 2009-12-21
> **juancarlospaco said:**
> yes..., its kinda automatic, 
wifi networks just come up on the network icon when you click it.
You can connect to invisible networks too using the proper option,
and create your own wifi network.
Well, I have a router and I'm trying to get it working with my computer.  I called technical support with the router and they assured me it was working and that I just needed to scan for wireless networks to find it, but I can't.

---

### Post by beano0528 on 2009-12-22
Ok, so I am now assuming that the brand of router that I am using does not support Linux.  If so, is there anyway I can make it work?  Under wireless networks it says "device not ready".  Is this a compatibility issue?

---

### Post by lisati on 2009-12-22
What kind of router? Perhaps someone on the forums has experience with a similar model.

edit: if you're using a laptop with built-in wireless, don't forget to make sure it's switched on.

---

### Post by bkratz on 2009-12-22
> **beano0528 said:**
> Ok, so I am now assuming that the brand of router that I am using does not support Linux.  If so, is there anyway I can make it work?  Under wireless networks it says "device not ready".  Is this a compatibility issue?




First thing we need to determine is what is your wireless card. If it is a pci card go to the terminal  (Applications..Accessories..Terminal) and type in--- lspci | grep Wireless--- (note capital  W and lspci is lowercase LSPCI).   If it is a usb device type in lsusb.  Either carefully look at the output or post it here and someone will decode it for you.

---

