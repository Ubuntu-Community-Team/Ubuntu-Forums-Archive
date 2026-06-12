---
title: "Wicd not auto connect to wired network upon boot"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by stchman on 2008-06-10
Hello all, I have installed Wicd as my network manager.

Problem is that on my one PC it has only a wired connection.  I created a default profile called Static_IP in which I want a static IP.

I checked the box Use as default profile for the Static_IP.  When I boot into Gnome Wicd does not auto connect to the wired interface as desired.  I can hit connect and Wicd then connects to the wired network.

Is there a way to make Wicd do this?  Is Wicd really only supposed to be used for wireless connections?  Any thoughts?  Should I use network-mamager for wired and Wicd for wireless?

Let me know.

---

### Post by wannadumpwindows on 2008-06-10
When you install WICD, it removes network-manager for you. It should work fine with wired connections. There's a check box to start the connection automatically when you expand the little arrow in WICD. Just go to the connection you want to use, expand the preferences menu, and then just tick the box, and it should fire right up for you. I've never had any troubles with mine doing exactly that.

---

### Post by stchman on 2008-06-10
> **wannadumpwindows said:**
> When you install WICD, it removes network-manager for you. It should work fine with wired connections. There's a check box to start the connection automatically when you expand the little arrow in WICD. Just go to the connection you want to use, expand the preferences menu, and then just tick the box, and it should fire right up for you. I've never had any troubles with mine doing exactly that.

I did just that and Wicd does not auto start upon boot.  There are not too many menus in Wicd so I don't think I could have missed it.

I guess if it keeps up I will reinstall network-manager.  Wicd works very well for wireless connections as it allows me to give my wireless connection a static IP.

---

### Post by wannadumpwindows on 2008-06-10
Yeah sorry it doesn't work for you. That's all I had to do. It's got me wondering now. It's always worked that simple on my end. Do you have that box checked for more than one connection by chance? That's about the only other thing I can think of. Sorry I can't help you more.

---

