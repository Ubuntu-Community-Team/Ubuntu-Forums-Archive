---
title: "Wireless not detected Vaio VGN-FW190"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Ivanho on 2008-08-30
I'm a COMPLETE Linux noob. I'm trying to get into it because it is so much faster and I think I'll get more done while using it. My wireless card isn't even detected. I'm not too sure how to even find out what it is. I saw the "lspci" command somewhere and when I do that in the terminal it says (for the wireless I assume)

06:00.0 Network controller: Intel Corporation Unknown device 4232

Does anyone know how I can get my wireless working? Also my screen brightness switching isn't working (ATI HD 3470) but I'll post about that in the video area.

Thanks!

---

### Post by Ivanho on 2008-08-30
Don't want to be a pest, but does anyone know?

---

### Post by czz7661 on 2008-10-15
I just purchased one of these laptops but haven't received it yet.  I would imagine at this point the centrino 2 wireless chipset isn't supported under the 2.6.24 kernel you're most likely using.  Have you tried using ndiswrapper?  What kind of driver cd's does the machine come with?

You should be able to pull the inf file off of the disk and perhaps utilize it to run the wireless card until the time there is linux driver support for it.

---

