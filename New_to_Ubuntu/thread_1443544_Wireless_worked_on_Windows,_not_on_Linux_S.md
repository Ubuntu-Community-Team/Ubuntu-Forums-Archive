---
title: "Wireless worked on Windows, not on Linux? :S"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-03-31
I'm trying to follow this advice:

"You might want to try changing the WPA Supplicant on your network manager to wext. On wicd it's the first option when you go into Preferences. "

Where do I acess this option?

---

### Post by tooatw on 2010-03-31
something that worked for me: "switch the wireless off and back on"
not from linux, switch it off from the laptop switch and check at connections if it finds any connections, if they are not there it means its off, then turn it back on, do the "sudo dhclient" and it should be working fine

---

### Post by papuccino1 on 2010-03-31
It seems my laptop wifi button isn't working with Linux. What can I do?

---

### Post by tooatw on 2010-03-31
so nomatter if its on or off you can't see any wireless connections detected by it? or you just can't switch it on/off?

---

### Post by papuccino1 on 2010-03-31
I followed a guide and rebooted many times, nothing worked. Finally I got pissed off and pressed my laptops "fn" key with F1,F2,F3 etc. and my screen went black. I rebooted by pressing the power button for a long time and turned the laptop back on. Now it works. WTF?

Did the stars align or something?

---

### Post by Slonda828 on 2010-03-31
Check your factory hotkeys. Sometimes, there is a FN+something key combination that turns your wifi on or off at the hardware level (sometimes even in addition to the switch if you have one). I had a trackpad on a user's netbook that wouldn't work for a whole week until we figured out that he used FN+F7 and locked himself out of it. I know what you are thinking, then why does it work in windows? Different kernels use hardware and hot keys differently. Let us know what you uncover. If this doesn't work, we can start hand jamming CLI commands and see where your hardware is at as far as being recognized. ;)

---

### Post by tooatw on 2010-03-31
> **papuccino1 said:**
> I followed a guide and rebooted many times, nothing worked. Finally I got pissed off and pressed my laptops "fn" key with F1,F2,F3 etc. and my screen went black. I rebooted by pressing the power button for a long time and turned the laptop back on. Now it works. WTF?

Did the stars align or something?

you probably turned it off and back on randomly with the Fn key because some laptop have the hotkey for the wireless Fn+ something

---

