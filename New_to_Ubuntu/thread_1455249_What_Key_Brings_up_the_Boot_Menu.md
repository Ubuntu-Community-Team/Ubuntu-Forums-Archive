---
title: "What Key Brings up the Boot Menu?"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by ChannelZ28 on 2010-04-15
i just added ubuntu to my asus eeepc already running xp, but it automatically boots into ubuntu. is there a key i can press as soon as i turn on the computer that will bring up a boot screen with options of which os i want to boot up?

---

### Post by Bachstelze on 2010-04-15
Shift.

But GRUB normally shows the menu automatically when it detects two OSes...

---

### Post by ChannelZ28 on 2010-04-15
nope, shift didnt work, neither of them. i thought it would load automatically also, but something must have been overwritten.

---

### Post by undecim on 2010-04-15
Did you install with Wubi or with a Live CD/USB

---

### Post by ChannelZ28 on 2010-04-15
live usb. i went through the partition steps very carefully, all my windows files are still there, just cant boot it up.

---

### Post by undecim on 2010-04-15
Boot Ubuntu, open a terminal, and paste and run this command:
```
sudo update-grub
```

And see if that fixes it.

---

### Post by ChannelZ28 on 2010-04-15
nope that didnt work either. im sure there must be a key to press to bring up the boot menu, i remember from the past that it would give me the option of booting up regular or in safe mode, thats the screen im looking for. i think the dual boot option would be on that screen. this is driving me nuts.

---

### Post by lisati on 2010-04-15
(vague recollection of having read something somewhere, I'm still using legacy grub)

Left shift?

---

### Post by undecim on 2010-04-15
> **ChannelZ28 said:**
> nope that didnt work either. im sure there must be a key to press to bring up the boot menu, i remember from the past that it would give me the option of booting up regular or in safe mode, thats the screen im looking for. i think the dual boot option would be on that screen. this is driving me nuts.

Shift brings up the grub menu. You have to be holding it when grub is loading (start holding it when you see your manufacturer's logo).

But that shouldn't be necessary if you have a dual boot option, unless you configured grub to have a timeout of 0.

---

### Post by SlickRick on 2010-04-15
try and fiddle around with your BIOS to see if usb is an option at boot time and since it's a live USB, it shouldn't use grub unless you have two OSs on it. You may have to bring up a BIOS boot menu. It's different for eveyone. May be delete or F12

---

