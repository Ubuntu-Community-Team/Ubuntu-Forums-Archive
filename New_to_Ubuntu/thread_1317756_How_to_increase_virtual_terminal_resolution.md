---
title: "How to increase virtual terminal resolution?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by humphreybc on 2009-11-07
At the moment, my resolution in a virtual terminal is really low, so the text is unnecessarily large... how can I change this?

Also, how do you scroll up and down in a virtual terminal?

---

### Post by ad_267 on 2009-11-07
Do you mean the terminals from Ctrl+Alt+F1-6?

You have to edit the line in Grub (not sure how to do this in Grub 2) to add vga=SOME_NUMBER, where the number can be found here: [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers). There's more information at [http://wiki.archlinux.org/index.php/GRUB](http://wiki.archlinux.org/index.php/GRUB).

As for scrolling, you could use gnu screen to achieve this, otherwise I'm not sure.

Edit: Looks like this will help with Grub2: [http://wiki.archlinux.org/index.php/Grub2](http://wiki.archlinux.org/index.php/Grub2)

---

### Post by mavasplode on 2010-05-28
You should be able to scroll in the virtual terminal using shift+pgup n shift+pgdn.

---

### Post by Nythain on 2010-05-28
if you are using Lucid (10.04) and the proprietary ati/nvidia drivers, this is an excellent guide

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

*edit* crap, just realized this thread was magically resurrected from a half a year ago

---

