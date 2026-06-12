---
title: "Networking set up"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by Servb0t on 2008-09-27
Hi,

I'm new here and am having some trouble setting up my network.

I'm running on the Live version and have not downloaded ubuntu onto my computer yet. I also don't have my network drivers downloaded.

Should I download ubuntu onto my computer and then run the drivers?

Thanks again (I run on a 64 bit Intel, btw)

---

### Post by sdowney717 on 2008-09-27
If you install the live cd to the computer, then the wired network most always just works. In fact I have never seen one not work yet.

Then to set up wireless cards including usb, you might have to install ndiswrapper-gtk, all 3 are found in synaptic package manager.

for wireless, you will find this menu item under system-admin-windows wireless-drivers

You will need the .inf file for the card.

some wireless devices will just work with ubuntu, some will need ndiswrapper.

---

