---
title: "Need for a ndiswrapper command line to install DWL-122 D-link usb adapter"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by ainigma on 2007-01-03
Could anyone send me his proposal for a ndiswrapper command line to install a d-link usb adapter DWL-122?I have used a non-ndiswrapper command line in order to install the adapter.It worked but i cannot have my pc to use wpa-psk authentication protocol(I need too use  that specific protocol).So maybe if I use a ndiswrapper command line, things could change....Thank you people!

---

### Post by c.dric on 2007-01-03
Hi ainigma

could u check the output of the following command :

**lspci | grep prism**

This will tell you which module was loaded automatically for your card. 
You'll have to remove it and blacklist so that it doesn't interfere with ndiswrapper.

From what i could read in the docs, it should be called : prism2_usb

If this is the case; use the following 2 commands to remove & blacklist it :

[B]sudo modprobe -r prism2_usb
echo "prism2_usb" | sudo tee -a /etc/modprobe.d/blacklist[/B]

To install Ndiswrapper you should follow this tutorial : 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
(Do not do Step 7, you should already have blacklisted the module by now)

If that went well, you can move on to set up WPA using this tutorial : 
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

i hope this helps ... 
just ask here if you get stuck somewhere :)

---

