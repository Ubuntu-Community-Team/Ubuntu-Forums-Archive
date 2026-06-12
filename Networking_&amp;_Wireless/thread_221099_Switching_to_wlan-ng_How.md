---
title: "Switching to wlan-ng? How?"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by mrbrdo on 2006-07-22
Hey

I have an USB wlan card (NetGear WG121). When i plugged it in it started working (it has the Prism2 chipset). I don't know which driver it is currently using (tg3 is loaded, is there a way to check for sure which driver it is using?). I would like to the wlan-ng driver, it seems to support my card (as stated on their page), but i don't know how to do this. I have installed the wlan-ng package and the -firmware one (with synaptics), but now i'm stuck. If anyone could point me to some info on how to configure an USB wlan card to use wlan-ng, or tell me in a reply, i would be most grateful.

Thank you

---

### Post by Dr. Nick on 2006-07-23
run this command to see if the dirver is loaded

lsmod

look at the usbcore line for Prism2_usb. I know that the prism2_usb has been covered in the forums before, I posted back some time ago with my problems using it.

I will tell you that last I knew you couldnt use the wireless gui configuration tools to set it up.

here is my thread
[http://ubuntuforums.org/showthread.php?t=72362](http://ubuntuforums.org/showthread.php?t=72362)

may have some helpful info, I am sure their are other threads, maybe better suited also, I just dont know of any right now, but a search on "prism2_usb" may proove useful.

---

