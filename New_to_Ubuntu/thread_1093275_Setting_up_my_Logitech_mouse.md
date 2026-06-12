---
title: "Setting up my Logitech mouse"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Volt9000 on 2009-03-11
Ok well now that I have Ubuntu up and running I'd like to start tweaking it to my tastes.

One thing I'd like to do is enable support for my Logitech mouse. It's nothing special, just a wired mouse with extra buttons, but currently those extra buttons are completely useless. I'd like to be able to assign those buttons to certain tasks (for example, the back and forward buttons to behave as such when browsing with Firefox or Nautilus.)

So how do I go about doing this? Do I have to edit my xorg configuration file? And if so, how?

---

### Post by Volt9000 on 2009-03-11
Oh I should mention-- I'm running Ubuntu under VirtualBox. I don't know how this would affect the setup but I assume it would, since Ubuntu cannot see my mouse directly.

I tried following the instructions [here]("http://ubuntuforums.org/showthread.php?t=219894") but it didn't work. Can anyone offer any advice?

---

### Post by LowSky on 2009-03-11
you actually dont need to configure the mouse it should just work but if not could you specify which model, as mine (Logitech MX518 ) has for the last I think 3 Releases. And when I say work, it works in Firefox, unfortunatly there is no support for Nautilus at all.

---

### Post by kanikilu on 2009-03-11
It's been a while since I've run Ubuntu in VirtualBox, but I believe it installs and uses it's own mouse driver if you use the guest additions, so, this may not be possible :?:

---

### Post by LowSky on 2009-03-11
oh its a virtual box install.... that is a whole other monster, as VM is basically emulating a mouse for the OS

>  only passes a simple 3 button mouse with scroll functions to the VM, so you can scroll vertically, but not horizontally. The back and forward buttons are not send either. Unless you enable USB and pass the mouse to the VM (NOT RECOMMENDED), it won't work.

[http://forums.virtualbox.org/viewtopic.php?p=61307&sid=89986e46556f6fcb1c5435f8b1a1f676](http://forums.virtualbox.org/viewtopic.php?p=61307&sid=89986e46556f6fcb1c5435f8b1a1f676)

---

### Post by Volt9000 on 2009-03-11
Ah, that's what I figured, thanks!
Any guesses as to why it's a bad idea to pass the mouse as a USB device through the VM directly to Ubuntu?

---

### Post by LowSky on 2009-03-11
From experience no, sorry.

from what I think without looking up the information (a guess....lol)

You will not be able to control the mouse outside of the VB. So inother words if the VB freezes or crashes you wouldn't be able to use the mouse in the Base OS to close VB out. Like I said a Guess...

---

