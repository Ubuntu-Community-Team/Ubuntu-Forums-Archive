---
title: "Small ubuntu on the screen"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by rrvnd on 2009-02-17
I installed ubuntu onto my XP using virtual box.
Installation has been successful but the screen is very small.the size of the ubuntu screen is centered in the middle and i cannot expand it.
I am also not sure if the above mentioned problem and the following error message are related or not.

"the virtual machine windows is optimized to work in 32 bit color mode but the color quality of the vitual display is current set to 16 bit please open the display properties dialog of the guest OS and select the 32 bit color mode, if it is available , for the best performance of the virtual display subsystem" 

Can anyone help me how to sort this problem out?
Thanks in advance

---

### Post by scorchgeek on 2009-02-17
You should be just fine using it without the 32 bit color mode. That message is simply telling you that you aren't using the maximum number of colors on your system. This could be because your graphics card can't support it. If you really want to try to fix it, you could try poking around in settings, but Ubuntu should run just fine in 16-bit color mode.

This error message is unrelated to your other problem. You can fix this by going into full-screen mode, if you're willing to do that. Just choose Machine --> Full Screen with the VM running.

---

### Post by RomeReactor on 2009-02-17
Hi. You should also try installing the [guest additions]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/").

---

