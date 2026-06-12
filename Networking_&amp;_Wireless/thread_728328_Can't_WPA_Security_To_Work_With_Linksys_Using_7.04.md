---
title: "Can't WPA Security To Work With Linksys Using 7.04 On Dell Latitude"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by bobt12 on 2008-03-18
I have an old Dell Lattitude laptop running 7.04. I have been using it with a Linksys WPC54G notebook adapter connecting to a Linksys WRT54g router with no security for well over a year now and it was working just fine. A couple of days ago I found that a neighbor was using my wireless, so I decided to finally use some security, I set up the router to use WEP and was able to get the laptop to connect just fine. Then I found out that WEP is not very secure so I decided to set it up with WPA. Now I can't get it to connect. It will ask for the passphrase I give it the correct one but it will not connect. I have an Ibook that connects just fine. Would anyone have any ideas?

---

### Post by nixscripter on 2008-03-19
The first thing I would check is to see if the encryption kernel modules are being loaded. They might not be if encryption was not being used before. Post the output of the command: ```
lsmod | grep ieee
``` There should be "ieee_crypt" and a few others in there.

---

### Post by bobt12 on 2008-03-19
Thanks in advance for your help.
When I do that command it shows nothing. I guess that would be the problem. So how do I get the modules to load? I read another post about wpa supplicant. Synaptic shows that is installed.

---

### Post by nixscripter on 2008-03-22
> **bobt12 said:**
> When I do that command it shows nothing. I guess that would be the problem.

Nothing? That means the wireless adapter isn't being detected. There should at least be "ieee80211" for the networking stack.

Was the device plugged in when you ran the command? It needs to be, since being a USB device, the kernel won't load the modules until they are needed. If it was, try rebooting the machine once, plugging it in, and run the command again just to make sure.

> So how do I get the modules to load? I read another post about wpa supplicant. Synaptic shows that is installed.

Assuming that plugging in the device doesn't do it, as I suggested above, you could use the modprobe command to load them manually. Something like this should do it: ```
sudo modprobe ieee80211 ieee80211_crypt ieee80211_crypt_wpa
``` You may also need to load the module which the card uses, which I don't know off hand (but I bet google does).

---

