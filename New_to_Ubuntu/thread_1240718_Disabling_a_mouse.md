---
title: "Disabling a mouse"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by janyapwns on 2009-08-15
Hi!

I just installed Ubuntu a few hours ago and ever since have been searching for a way to disable a mouse and I can't seem to find any answers.  Here is my problem.  I am using a PS/2 trackball mouse and a Logitech wireless keyboard.  My husband whose computer is less than 2 feet away is also using a Logitech wireless keyboard/mouse combo.  When he moves his mouse my logitech wireless usb receiver is picking it up in addition to my mouse since I am not using a wireless mouse.  As you can imagine this is causing all sorts of mis-clicks and other shenanigans.  In windows device manager I can simply disable the second mouse but I haven't been able to find the equivalent in Ubuntu. I installed the gnome-device-manager but there is no option to disable.  Please help!

Thanks!!

---

### Post by mgranet on 2009-08-15
Have you tried changing the channels on the recievers? There is usually some sort of button or switch.

---

### Post by janyapwns on 2009-08-15
The only button on either receiver is a connect button.

---

### Post by mgranet on 2009-08-15
That's the one. There should also be one on each wireless mouse and keyboard. With the Logitech units, press the connect button on one reciever, then press the button on the device. Wait for it to connect, then repeat with every device you want to work on that computer. Once you have done one computer, repeat the procedure for the other computer, and it should eliminate the interference.

---

### Post by janyapwns on 2009-08-15
Right, that would be great, except there is only one wireless mouse.  When there were 2 this wasn't an issue because I could do like you suggested.

---

### Post by mgranet on 2009-08-15
It don't matter how many devices you have. The idea is you are making sure Mouse A is only talking to the reciever on Computer A. The fact that his mouse if affecting your computer means that BOTH recievers are operating on the same channel.

To ensure the devices are on separate channels:

Press the connect button on your receiver. Then, press the button on your keyboard.

Next, press your husband's connect button. Then, press the connect button on his mouse. Press your husband's connect button again. Now, press the connect button on his keyboard.

---

### Post by janyapwns on 2009-08-15
I understand what you are saying and I have I tried numerous times but it isn't working.  I sync the mouse and keyboard to receiver A.  I then sync the other keyboard to receiver B. My best guess is that the mouse is still showing up on both receivers because there is nothing replacing it when i sync receiver B.  Whatever the case, it doesn't solve the problem.  The keyboards operate with their respective computers just fine, but the mouse is determined to use both.  I know I could probably just go out and buy a new mouse and be done with it but it seems like there should be an easier solution. Also, since I prefer my current mouse to the wireless variety it seems like a waste of money.

---

### Post by mgranet on 2009-08-15
Hrm. That's odd. Maybe the old mouse configs are still loaded.

Can you post the output of your xorg?

```
cat /etc/X11/xorg.conf
```

---

### Post by janyapwns on 2009-08-15
[FONT=monospace]Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

[/FONT]

---

### Post by janyapwns on 2009-08-15
I'm going to go dig through boxes in the garage and see if I can't just find an old mouse to sync and throw in a drawer.

---

### Post by mgranet on 2009-08-15
I hate to ask, but are you sure there's not more to that config file? I install from the nvidia site, so my xorg is much more detailed. I'm not sure if a default conf is less detailed.

---

### Post by janyapwns on 2009-08-16
thats it.

---

