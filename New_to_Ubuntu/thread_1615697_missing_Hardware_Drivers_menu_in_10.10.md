---
title: "missing Hardware Drivers menu in 10.10"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by marlenus on 2010-11-07
I'm a first time Ubuntu user and just installed 10.10 in a VirtualBox VM.  I now need to install ATI drivers


But Additional Drivers is empty and appears disabled.  (ignore the nvidia tab in the screenshot, I thought this machine had an nvidia card but that's my other one, this has an ATI HD 4800)

[IMG]http://clip2net.com/clip/m46884/1289143120-clip-67kb.png[/IMG]

---

### Post by sikander3786 on 2010-11-07
Virtualbox uses a virtual graphics card instead of the original one so you don't need to/cannot install ATI driver on a virtual machine. Instead, install the guest additions which would improve the graphics.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by marlenus on 2010-11-07
So I manually downloaded the driver from ATI and started installing it, but I can't see the options on this screen to continue

[IMG]http://clip2net.com/clip/m46884/1289145445-clip-82kb.jpg[/IMG] 
and cant get scroll bars, etc.  just tried tabbing to the invisible options (there appear to be three) and guessing by hitting space and CR but no go.


JUST SAW THE RESPONSE ABOVE.  Will cancel this and try that.  THanks.

Wow, they don't make the guest additions DVD easy to find.  In case anyone else needs this in the future, I found it here:
[http://download.virtualbox.org/virtualbox/3.2.10/VBoxGuestAdditions_3.2.10.iso](http://download.virtualbox.org/virtualbox/3.2.10/VBoxGuestAdditions_3.2.10.iso)

---

