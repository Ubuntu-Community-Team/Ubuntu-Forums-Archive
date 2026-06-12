---
title: "i killed my realtime kernel"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Megatron3000 on 2009-09-04
yes indeed, and i will need it for recording music. upon configuring my graphics card with the proprietary driver, reboot was no longer possible, and somewhere i apparently wrecked recovery mode too. In my normal kernel, everything works fine and looks super swell. When i boot in my rt kernel now, in the loadng list before the log in menu, it says fglrx failed, after that, i get stuck in a list of strings of numbers and words, all nicely vintage-y on a black screen, and then everything just locks. Recovery mode does not boot either.
For my everyday non-music use, it's no problem, but since music is as everyday a use as the rest, i'd like my realtime kernel back.  Should i just deinstall the current one and load it again? Or is that a danger zone? thanks!

---

### Post by xir_ on 2009-09-04
> **Megatron3000 said:**
> yes indeed, and i will need it for recording music. upon configuring my graphics card with the proprietary driver, reboot was no longer possible, and somewhere i apparently wrecked recovery mode too. In my normal kernel, everything works fine and looks super swell. When i boot in my rt kernel now, in the loadng list before the log in menu, it says fglrx failed, after that, i get stuck in a list of strings of numbers and words, all nicely vintage-y on a black screen, and then everything just locks. Recovery mode does not boot either.
For my everyday non-music use, it's no problem, but since music is as everyday a use as the rest, i'd like my realtime kernel back.  Should i just deinstall the current one and load it again? Or is that a danger zone? thanks!

fglrx is the ATI binary for graphics. try uninstalling the ATI driver via synaptics first and then see if it will boot into your real time kernel.

---

### Post by Megatron3000 on 2009-09-04
it would actually be sweet to keep the graphics going, that's the whole reason why i started to mess with this. I should have mentioned that

---

### Post by xir_ on 2009-09-04
ok well, id suggest just removing it for now and seeing if it will boot, once its there you can try and reinstall the drivers.

---

