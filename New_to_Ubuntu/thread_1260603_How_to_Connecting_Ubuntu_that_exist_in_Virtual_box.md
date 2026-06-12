---
title: "How to Connecting Ubuntu that exist in Virtual box to internet"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by n36atr0n on 2009-09-07
HI

Im installed Windows xp as host and ubuntu inside its virtual box. Usually, im using venus VT-21 cdma usb modem to connect to the internet. My question is, how i can connect my ubuntu to internet?
1. Connecting its directly from the virtual box with host's modem?
2. Connecting its with the host via virtual network and arrange internet connection sharing?

Thanks all

---

### Post by Pirolocito on 2009-09-07
Usually virtual box and host deal with network, but better to share internet in windows and give a try.

And dont forget to install guest adiction to get full screen and all goodies.

---

### Post by n36atr0n on 2009-09-07
> **Pirolocito said:**
> Usually virtual box and host deal with network, but better to share internet in windows and give a try.


And dont forget to install guest adiction to get full screen and all goodies.

Can you tell me where i can find out how to connecting this?
quiest adiction ?like what?

---

### Post by cdburgess75 on 2009-09-07
if you host can connect,  check that your guest network adapter is added.  (wired/wireles etc.)

---

### Post by tacantara on 2009-09-07
The guest additions should show up as a .iso CD file in the Devices > Mount CD/DVD-ROM > CD/DVD-ROM Image.  As for the internet connectivity issue, look for the details tab when you first open VirtualBox.  Scroll down to the network portion, and make sure that you have a network adapter assigned that will allow VB to use your system's Wi-Fi or Ethernet (whichever one you use to connect to your DSL).  If you don't have anything configured, run the virtual machine, and from the Devices menu, select Network Adapters.  Adapters 1 & 2 should be checked. If they aren't, then check them.  The networking icon in the lower right portion of the VB screen should show activity if you're connected to the Internet.  If necessary, you can configure the network adapters before you start your virtual machine by highlighting the machine in the box that comes up when you open the program, and click the Settings icon.

---

