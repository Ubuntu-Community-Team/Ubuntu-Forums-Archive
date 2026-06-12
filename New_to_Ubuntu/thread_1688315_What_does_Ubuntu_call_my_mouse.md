---
title: "What does Ubuntu call my mouse?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by BunnyDee on 2011-02-15
How do I find the Ubuntu device name (what the OS 'sees it as') for a mouse I have, which I want to map the buttons for? I'm pretty sure there's some command I use in the Terminal, but I can't remember/find it.

I have no use for lspci since it's not a PCI card or anything, nor lsusb since it's not connected to a USB port.

It's connected via PS/2, although I can connect it to a USB drive if necessary, and the command I eventually need to use to map it is ```
xinput set-button-map "Whatever The Rodent Is Called Here" 1 2 3 4 5 6 9 7 8
```
Also, I don't know how to make this 'stick' - I did it yesterday and it worked... until I rebooted.

Oh, I use Ubuntu 10.10 (Maverick Meercat), although I doubt it really makes much difference. And the mouse is a Microsoft Comfort Optical Mouse 3000, but I remember that's not what Ubuntu 'calls it'.

Thanks for any info.

---

### Post by BunnyDee on 2011-02-15
...Found it, after all. It was pretty obvious, too. I used xinput list, in the Terminal (just to see if it would, at first, but, hey, it worked!!!)

---

### Post by Frogs Hair on 2011-02-15
```
"Whatever The Rodent Is Called Here"
``` Nice :)

---

