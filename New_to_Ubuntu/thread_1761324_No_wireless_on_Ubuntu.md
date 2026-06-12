---
title: "No wireless on Ubuntu???"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Instinctus on 2011-05-18
hey i just installed Ubuntu on my Acer Extensa 7220 and i cant get wireless working. My network controller thingy is broadcom corporation BCM4311 802.11b/g WLAN (rev 01). does anyone know how i can fix this. Thanks.

I have Ubunto release 11.04(natty) i have no idea what i have to do and im a tw*t when it comes to computers. thanks for any help.  bcmwl-kernel-source and the b43-fwcutter are both installed and still i cant get the wireless to work :S

---

### Post by Wim Sturkenboom on 2011-05-18
Did you try to search here for BCM4311 ? You might first try the ones that are marked as solved.

And post the version of Ubuntu (kubuntu/ubuntu/... , 10.04, 10.10, ...) that you're using! I'm not very familiar with wireless so probably can't help you further. But more information makes it easier for others to help.

---

### Post by mastablasta on 2011-05-18
have you tried connecting it with a wire and install the drivers for the wireless card?

---

### Post by garvinrick4 on 2011-05-18
Here is screenshot. Open Synaptics and type in bcm and you will get bcmwl-kernel-source
and the b43-fwcutter install the two of them.
Then hit the windows key/A same time and type in additional drivers and if not enabled do it. If 11.04 natty version.
If 10.04 or 10.10 version I believe it was System/Admin/ hardware drivers
Might have to reboot.
Screenshot below Sorry.

---

### Post by garvinrick4 on 2011-05-18
Here is the screenshot. click on it.

---

### Post by OGpmpdog on 2011-05-18
Hi,


Please visit the below link.

[http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu](http://wireless.kernel.org/en/users/Download#Getting_compat-wireless_on_Ubuntu)

Scroll down to "Getting Compat Wireless on Ubuntu"

Your ubuntu version is probably in that list; cut and paste to Terminal.

Reboot.

This is probably the quickest fix...the lesson learned is the command installs the latest wireless drivers to your kernel.

Good luck!

---

