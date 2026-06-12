---
title: "Karmic Koala Screen Resolutions and KVM's"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-12-22
I've been trying to get the screen resolution improved on Karmic Box and I think I had a light bulb go off on why I can't do that...

After considerable googling, I suspect that my KVM is not letting my monitors EFID through.  (I had similar issues in Hardy but I managed to brute force my way through and manually configured) It didn't dawn to me that the issue was with the KVM,

I suppose I should diconnect the KVM and reboot and see if it magically heels itselt and that way I'll now if its the KVM.

[Note to self]
I need to site the post somewhere about forcing the system to requery the monitors(don't know if that's valid for Karmic thou)

Assuming the issue is the KVM not passing the EFID, what is the "official way" to lock settings down, so I can use my KVM. I just did another fresh install and update and I haven't installed the proprietary Nvidia drivers yet. I read that nvida-settings will do that.  Is that valid for Koala?
 
Please pardon my rant here. But.....
It seems that the trend is to remove the tools for manual configuration in the newest releases..
If the problem is the KVM blocking the EFID signal, why doesn't something in installation procedure say, hey I can't read your monitors EFID, If your using an old monitor that doesn't have a EFID do this, else if your using a KVM do this...](*,)](*,)](*,)](*,)](*,)
Time to go to bed and have dreams out KVM cables trying to ensnare me..

---

### Post by Jonas thomas on 2009-12-22
Duh... The issue was my Kvm.  I shut down, disconnected my KVM and now everything is fine.... I think it may be time to upgrade my ebay hong kong special....
Now... if I could get the sound to work...

---

### Post by KeLa on 2009-12-22
Had also problems with my KVM when changed monitor to new make and model.
KVM is belkin with DVI connectors and old monitor was Samsung something and it
worked fine with it but when i put BenQ monitor in there there was strange blue horizontal
lines in black backgrounds moving up and down all the time.
There was nothing wrong in Karmic side because exact same effect was in WinXP box in
other line of KVM.
Only thing i can do is to use Karmic dvi direct to monitor and WinXP with vga connector:(

---

### Post by Jonas thomas on 2009-12-22
> **KeLa said:**
> Had also problems with my KVM when changed monitor to new make and model.
KVM is belkin with DVI connectors and old monitor was Samsung something and it
worked fine with it but when i put BenQ monitor in there there was strange blue horizontal
lines in black backgrounds moving up and down all the time.
There was nothing wrong in Karmic side because exact same effect was in WinXP box in
other line of KVM.
Only thing i can do is to use Karmic dvi direct to monitor and WinXP with vga connector:(

Can you run computers simulataneously when you do that?

---

### Post by KeLa on 2009-12-22
yes. Ubuntu is in box number 1 and windows in box number 2.
(it's 2 port KVM)
but you can see only one box at the time because
monitor, mouse and keyboard are connected to one box at the time.

---

### Post by Jonas thomas on 2009-12-22
If I understand you correctly, use still using the KVM to switch, it's just that you have VGA and DVI both hooked up.

Oh... My Kvm is a 4 port with vga only, mouse, keyboard imports.

Doe's anyone have recommendations on a KVM that places nice and won't break the budget?  I suppose 2 port would work, but 4 port comes in handy at times.

JT

---

### Post by KeLa on 2009-12-22
I now use it only to split keyb and mouse between two boxes.

Mine is 2 port Belkin (once replaced by warranty) (Belkin OmniView SOHO Series F1DD102U)
It's DVI version with USB keyboard and mouse + audio (mic and headphones).
Won't recommend it to anyone.

One thing that i had to do in the first place was hook a stripped down usb keyboard to it's normal keyboard connector (only way to stop it beeping for missing keyb) and use keyboard connected to normal usb port in it (have 2 usb ports to share)
and this is because only about half of the keys in keyboard worked in that normal port :P
Never used the audio share because it's not any funny that you play music on one box and the go to other and you can't hear anymore that music.

---

