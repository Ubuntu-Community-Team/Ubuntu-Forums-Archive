---
title: "Touchpad won't work properly after latest update?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by a2z22a on 2009-08-30
Hello all,

I have installed ubuntu yesterday, and was working perfectly. Last night, it told me it had found an update so I of course let it. The touchpad was working fine after a restart, however upon logging onto my laptop today it is not working.

The scroll and touch click will not work, and if you move the mouse it goes in the opposite direction: left = right, up = down etc.

Is there any way I can revert to the previous installation and keep it there (Immune to all other updates)?

Thank you for your time :)

Edit: Fixed by doing this

sudo apt-get remove xserver-xorg-input-synaptics
sudo apt-get install xserver-xorg-input-synaptics

---

