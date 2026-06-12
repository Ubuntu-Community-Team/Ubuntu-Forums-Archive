---
title: "Newbie: System freeze using Belkin Wireless G+ MIMO"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Fran Varin on 2008-05-24
I have installed Hardy on a Dell Inspiron 1000 with a Belkin Wireless G+ MIMO card. I have it configured fine but, when I try to access the inet sometimes the entire system freezes forcing me to power the laptop down and doing a cold boot. I have noticed this when trying to install maintenance using the following command sudo dpkg --configure -a. Also, this has happened while using Firefox. I have not seen the symptom with Evolution to date however. Any help would be greatly appreciated.

One thing I would add is that it works fine with my D-Link DWL-122 Dongle. The Belkin seems to be giving Ubuntu fits.

---

### Post by cutlerite on 2008-12-04
I'm no expert in Ubuntu either.  But I am having similar issues.  I was using the Linksys WUSB54gv4, and recently upgraded to the Belkin Wireless G Plus MIMO.  My system does not freeze, however I lose the internet and when trying to restart it will freeze shutting down.

I think this may be related to having too many driver installed.  

$ lsmod | grep usbcore
usbcore               148848  10 ndiswrapper,rt73usb,rt2x00usb,uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

There is a related post here: [http://ubuntuforums.org/showthread.php?t=691186](http://ubuntuforums.org/showthread.php?t=691186)

I have followed so many tutorials trying to get it to work, that I don't know how many drivers I have installed.  I don't know how to remove the rt2x00usb, and supposedly the rt73 is the newer version of rt73usb.  

If anyone can add some more information to this I would very much appreciate it.

---

