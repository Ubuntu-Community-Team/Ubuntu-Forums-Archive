---
title: "Difference between rausb0 and wlan0"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Supercross on 2007-04-25
I'm trying to get my Linksys WUSB54G to work under Feisty (Clean install) and I'm having some problems here.  The card does not work out of the box with network manager.  So I blacklisted the rt2570 driver and used ndiswrapper to utilize the rt2500usb driver.  This allowed network manager to show signal strengths and I even did get it to connect ONCE, just enough to get updates and install a graphics driver.  However, everytime I booted up, keyring manager would ask for a password and after I typed it in, the network would never connect.  So I removed network manager using package manager and tried to use just ndiswrapper w/ wpa_supplicant, however, now when I'm booted it always shows my network card as being rausb0.  Mind you I still have the rt2570 blacklisted and the rt2500usb being used through ndiswrapper.  I have tried countless times to un-blacklist, reboot, re-blacklist, reboot, and it always shows either rausb0 or rausb1, only once, back when I had network manager did it show wlan0, which is what worked back in Edgy, and what I thought was supposed to display.  Can someone help me out here?  How do I get the card to read as wlan0 and work that matter work.  Currently, even though its listed as rausb0, it still doesn't work even when I load all the modules (depmod, modprobe ndiswrapper, and ndiswrapper -m) and I added ndiswrapper to /etc/modules.  Any clue?

---

### Post by Sav on 2007-04-29
Same problem with asus wl-167g.
With the module provided by feisty, I can't connect to the access point.
I tried to recompile the last cvs from serialmonkey, but with the same results.

Using ndiswrapper I was able to connect only to open networks.

By the way, with suse 10.2 the r2570 module works vey well.

Maybe, can it be a kernel problem?

---

### Post by AmyRose on 2007-05-01
I got my Ralink-based device to work in Feisty by creating a file /etc/modprobe.d/blacklist.ralink:

```
blacklist rt73usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt61pci
blacklist prism2_pci
blacklist prism2_usb
blacklist prism54pci
blacklist prism2_plx
blacklist prism54common
blacklist prism54usb
blacklist ndiswrapper
```

And reboot.

For some reason, I had to blacklist all of that to force it to fall back on the working driver. Hope this helps! It took me a while to find out all the things I had to blacklist. *sigh* At least it's working now. :) (Don't ask me why I had to blacklist the Prism modules too... I thought it was ridiculous that I had to blacklist those too in order to get my wireless working...)

But I still can't get it working with Network Manager. However, it works, so I'm not complaining.

---

### Post by luca.mg on 2007-05-03
I almost successfully run a wl-167g stick, with feisty's rt2570 module, wep network however. This box has upgraded from ubuntu 5 to 6 to feisty going thru several beta versions, therefore I messed up a lot with configuration files ever since when the rt2570 wasn't supported at all. I happen to have an /etc/modprobe.conf file (don't know if that's there by default with debian/ubuntu) with a single line of text: 

alias rausb0 rt2570

from a non nerd pov like mine maybe that makes the difference or either could be changed to read alias wlan0 rt2570. I also own an /etc/modprobe.d/nidiswrapper file that reads: 

alias wlan0 ndiswrapper 

belonging to a successfull attempt to run the card with ndiswrapper. It worked with network manager too but I find it too unconfortable being asked for password at every login. perhaps someone more computer literate than me could jump in and point you to the right configuration files. on the other side the device stops working randomly, and stops quite regularly after the sistem/network is not being used/accessed for a while: the blu led goes off and I have to  turn off the computer via the front  power switch and start it again to go back to normal. I may try suse to see how things work. I also came across an improved module at 

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/)

and that's the thing I'm going to test next.  hope this helps

---

### Post by SubCool on 2008-03-25
> **AmyRose said:**
> I got my Ralink-based device to work in Feisty by creating a file /etc/modprobe.d/blacklist.ralink:

```
blacklist rt73usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2x00lib
blacklist rt61pci
blacklist prism2_pci
blacklist prism2_usb
blacklist prism54pci
blacklist prism2_plx
blacklist prism54common
blacklist prism54usb
blacklist ndiswrapper
```

And reboot.

For some reason, I had to blacklist all of that to force it to fall back on the working driver. Hope this helps! It took me a while to find out all the things I had to blacklist. *sigh* At least it's working now. :) (Don't ask me why I had to blacklist the Prism modules too... I thought it was ridiculous that I had to blacklist those too in order to get my wireless working...)

But I still can't get it working with Network Manager. However, it works, so I'm not complaining.

Couple people said this worked.
It didnt help me at all. Sorry- Thanks tho! :-) :KS

---

### Post by ascii4u on 2008-03-30
To many hands in the pot, hrm.

tried: ralink driver, and serialmonkey's rt73 /w rutilt, which brought me to your post....

try this: 

find /etc/udev -type f | xargs egrep -i rausb0

found a persistant name for rt73 module, not even a kernel option would trump.
in the file, just edit it replacing rausb0 with wlan0.

but things are still more unstable than i desire from linux, so building the rt2x00 series see if that works out better for me.

... debian etch 2.6.18 i386 
... ibm t40 laptop
... wusb54gc

im guessing the stability issue has to do with initializiation of the firmware, and updating it when changing it. yeah, so i tried to break it. very possible the hardware has changes some and does the funky monkey ... hard locks ... man i hate that.

good luck, and hope it helps out.

---

