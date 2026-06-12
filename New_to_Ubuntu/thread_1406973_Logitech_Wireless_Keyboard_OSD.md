---
title: "Logitech Wireless Keyboard OSD?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by walt.smith1960 on 2010-02-14
I just purchased a Logitech MK300 wireless keyboard. Using 9.10_64 and most things are plug & play--volume, shortcut keys etc. The one thing I don't have is On Screen Display for Caps Lock status. Wireless keyboards don't have LED Capslock and Numlock indicators like wired keyboards. The keyboard comes with a CD which has (Windows only:mad:) software to add this function. Not knowing the state of the Caps Lock key can make entering passwords hit and miss. I tried installing "hotkeys" from Synaptic but that didn't seem to work. I'd welcome any thoughts on how to get Caps Lock status onscreen. Thanks.

---

### Post by Tamlynmac on 2010-02-14
I'm not certain about 9.10, but in 9.04 there's a "lock keys" applet (lock-keys-applet) available in the synaptic package manager that will place a visual representation of the keys in question - in your panel.

Good Luck & hope this helps....

---

### Post by Yogotiss on 2010-02-14
> **walt.smith1960 said:**
> I just purchased a Logitech MK300 wireless keyboard. Using 9.10_64 and most things are plug & play--volume, shortcut keys etc. The one thing I don't have is On Screen Display for Caps Lock status. Wireless keyboards don't have LED Capslock and Numlock indicators like wired keyboards. The keyboard comes with a CD which has (Windows only:mad:) software to add this function. Not knowing the state of the Caps Lock key can make entering passwords hit and miss. I tried installing "hotkeys" from Synaptic but that didn't seem to work. I'd welcome any thoughts on how to get Caps Lock status onscreen. Thanks.

Is there any specific reason why you are using 9.10_64?

---

### Post by Enigmapond on 2010-02-14
Thank you for that. I have the same keyboard and I never thought to check for an applet...it works just fine.  Cheers!

---

### Post by Tamlynmac on 2010-02-14
> Enigmapond
Thank you for that. I have the same keyboard and I never thought to check for an applet...it works just fine.  Cheers!     Glad it worked for you... Good Luck

---

### Post by walt.smith1960 on 2010-02-15
Thank You Tamlynmac that seems to work nicely. Useful on Netbooks without status indicators as well. There are some useful and friendly boards on the www. This is one.

---

### Post by walt.smith1960 on 2010-02-15
> **Yogotiss said:**
> Is there any specific reason why you are using 9.10_64?
64 bit processor and 4 Gig RAM, it seemed reasonable to try an OS that seems appropriate to the hardware. I'd heard of some problems with drivers etc. and being the kind of guy who has to pee on the electric fence to see for myself :rolleyes: I installed the 64 bit version of 9.10. So far so good although this machine is not used for demanding tasks.

---

### Post by thecliff on 2010-02-15
Im using 9.10 64 bit and haven't had any issues so far.

---

### Post by Tamlynmac on 2010-02-15
> walt.smith1960
Thank You Tamlynmac that seems to work nicely. Useful on Netbooks without status indicators as well. There are some useful and friendly boards on the www. This is one.

No problem - Glad I could help.

This "is" the best forum on the net. People here, are community minded and enjoy helping each other. The whole concept behind Ubuntu/Linux is Humanity. Sounds corny, but I believe it works. In the help sections of this forum, it's all about users helping other users.

IMHO, it doesn't get any better than that. But to each their own. Someday, you may be able to help me solve a problem or point me in the right direction.

Good Luck & I'm pleased it worked for you.

---

### Post by Joeasaurus on 2010-07-05
Hi, i realise I'm trudging up an old thread here but the lock-keys-applet isn't the answer I was looking for. I want an actual OSD notification as opposed to an applet. Maybe something using notify-send? Can any one hep?

---

### Post by Joeasaurus on 2010-07-06
Bump

---

### Post by Joeasaurus on 2010-07-07
Bump bump. Please? Anyone?

---

### Post by thehand on 2011-04-10
Install "gkrellm" and "gkrellm-leds".
In GKrellM, go to "Properties" tab under "General" under "Configuration" (right-click on gkrellm) and select "Set on top of other windows of the same type".  LEDs can be found in the "Plugins" section of GKrellM configuration.
Also, the led plugin is not really 'aligned' to the key state of the keyboard,  it just uses a variable or something that is toggled on or off when you  press a "Lock" button on the keyboard.

Sorry about making a zombie thread, but if I came across this thread while I was looking for the answer to the same question Joeasaurus asked (from Google), then other people will too.

---

