---
title: "Kubuntu crashed into Busybox"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Jazione on 2009-09-03
I've been using Kubuntu all summer while working at  a summer camp. Just got home and updated a few days ago. I dont think I updated to a new "Ku" or "U" buntu...  just installed the updates that collect in the administrator's box. 

Shortly after this update, while using Gimp or an audioplayer program the screen went black and now I'm in someing called Busybox. It claims to be a "shell" (ash)?. Is this an emergency mode? How do i get back to the desck top? I'd be really upset to have lost all the files I have stored on the desktop, a whole summers worth.  Any advice on how to get back to the desktop without wiping out the information thats was there? Some sort of back door? Or is it already gone?

I have a sony vaio "S vgn-s260" Its a laptop about five years old and ran windows xp before i completely erased it and installed Ubuntu two years ago and periodically updated it but I'm not sure to what animal. At the begining of this summer I updated to what was then the latest version of Kubuntu.

The bottom line reads (initramfs)

Yikes!

---

### Post by Penguin Guy on 2009-09-03
Do you mean your computer is still on? If so, try [COLOR="Green"]Ctrl + Alt + F7[/COLOR]. If it happens every time you boot try [COLOR="Green"]startx[/COLOR]. Yes, BusyBox is an emergency mode.

---

### Post by Jazione on 2009-09-03
The reply...
/bin/sh: startx: not found

Ctrl Alt F7  also had no effect

I can turn the computer on or off and end up on the same screen with "(initramfs)" at the bottom of the screen.

Maybe this would give you a better idea, a few lines above "(initramfs)",  is 
"Target filesytem doesnt have /sbin/init.
No init found. Try passing init= bootarg." 

By the way, molto grazi for your help!

---

