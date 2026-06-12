---
title: "System hanging on &quot;Ubuntu&quot; Splash screen"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by Coximus on 2010-09-28
Hi,

I've carried out a clean install on a desktop (AMD64 x6) system with onboard graphics. 4 gig ram and a 1tb wd hardrive.

It installs fine from a usbpen drive, however it wouldnt boot from a CD, simply not responding to the boot menu selections.

Once installed, I re-start the system and it goes to the purpul "Ubuntu" splash screen, but hangs there and does nothing (for over 3 hours now).

What should I do next to get it to boot up?

---

### Post by Hippytaff on 2010-09-28
Is it a live CD or are you installing it?
 
The CD might be corrupt? did you burn it yourself?

---

### Post by Coximus on 2010-09-28
The usb pen installed from booted fine.

This is a 100% fresh install on a formatted harddrive.

I booted the live cd/usb and used the install ubuntu desktop icon. No errors were reported,
I then rebooted as per instruction, removed USB pendrive and it boots to the splash screen and hangs there.

---

### Post by CharlesA on 2010-09-28
boot into recovery node to see if it spits back any errors.

---

### Post by Coximus on 2010-09-28
> **CharlesA said:**
> boot into recovery node to see if it spits back any errors.
How exactaly do I go about this? The system doesnt respond to anything when is hung on the screen.

---

### Post by Hippytaff on 2010-09-28
Before the spash there should be a selection of os options. One should be recovery (safe) mode.

---

### Post by CharlesA on 2010-09-28
> **Hippytaff said:**
> Before the spash there should be a selection of os options. One should be recovery (safe) mode.

Only if you have two or more OSes installed.

Otherwise hold down shift and see if you can get the GRUB2 menu.

---

### Post by Hippytaff on 2010-09-28
>  
Only if you have two or more OSes installed.


 
True...I shouldn't assume :-)

---

### Post by Coximus on 2010-09-28
On the Grub menu if i select safemode it produces no errors, 
however it hangs if I continue to boot normaly.

Ive also noticed that the keyboard lights are unresponsive / dead on normal boot, but If i use the graphics option I can get to the Xsession screen.

Also, Ive noticed all 5 red progress 'dots' complete on normal boot.

GOOD NEWS - If i use rescue and then startx manually I can get to the desktop - now how do I go about making this permanent?

---

### Post by Hippytaff on 2010-09-28
Try viewing the logs to see the problem
```
 
 
/var/log/messages

```
 
```
 
dmesg | more

```

---

