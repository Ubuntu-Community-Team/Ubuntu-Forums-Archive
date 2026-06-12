---
title: "ndisgtk disappeared?"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by Blaze637 on 2008-11-25
I need help trying to identify my windows wifi card (or whatever you call it), because the help on the system is leading me to a dead end. I tried to install ndisgtk from the list in "System > Administration > Synaptic Package Manger", but it's not even listed for installing (I think ndisgtk is the same thing as ndiswrapper, but I'm not sure). If it helps, I'm using Ubuntu 8.04. What do I do now?...

---

### Post by spcwingo on 2008-11-26
Well, there's a few choices for doing this.  If all you want to do is identify your wireless card, you can enter these commands in a terminal: lspci (for an internal card) or lsusb (for a USB card).  Alternately, if you like a GUI app to do this and much more you can install hardinfo from synaptic.  But, if all you need is ndisgtk you can download directly here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Just download all three files for your version of Ubuntu.  Double click them to open the gdebi package installer and install the packages in this order:

ndiswrapper-common
ndiswrapper-utils
ndisgtk

Let me know if this does the trick for you.

---

