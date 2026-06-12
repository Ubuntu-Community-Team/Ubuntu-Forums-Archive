---
title: "level one wnc0302usb and NDISwrapper"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by oedipuss on 2007-07-26
Hello

I'm using ndiswrapper with a usb wireless stick from levelOne . I think it has an atheros chip, the model is wnc-0302usb.

I remember it working fine on edgy, but with feisty the module loads but cannot be removed.
If I try to unplug the usb something horrible happens with the kernel, and many things dont work .. I dont know what exactly.. The only message on dmesg is about a usb device being removed, and no more messages appear after that, and commands get stuck. Even 'lsusb' which is kinda  unrelated doesnt work after unplugging the usb.
About the same happens if I try to unload the module before unplugging the stick. 

I've tried with various versions of ndiswrapper, with the same results.. I've got wireless as long as I do not unplug the stick, which is very very annoying.

Is there a way to fix this , or maybe some native linux drivers that support it ?

---

