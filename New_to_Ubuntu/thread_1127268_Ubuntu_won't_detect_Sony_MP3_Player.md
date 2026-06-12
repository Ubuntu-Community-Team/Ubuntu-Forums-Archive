---
title: "Ubuntu won't detect Sony MP3 Player"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by EssexEagle on 2009-04-16
I have a Sony MP3 player - model NWZ-S639F - which works fine in Windows but not in Ubuntu.  When I connect it to the computer (via USB) it says "Connecting" on the screen but Ubuntu does not recognize it.  It's not just that it can't read what's on the player - it is totally oblivious to the fact that I've even plugged anything in.  It should connect via MTP but when I run mtp-detect I get "No Devices have been found".  I believe I have all the necessary MTP packages installed, by the way.

I want to use Amarok to put music onto the player but at the moment I'm having to boot up in Windows and use Windows Media Player, which is reeeaaaaally annoying.  Is there any way of getting Linux to detect the device?

---

### Post by ddrichardson on 2009-04-16
Does any of [this]("http://ubuntuforums.org/showthread.php?t=866297") help?

---

### Post by subzero316 on 2009-04-16
After you plug in type the following command. And see if it says anything about that device in the end.
```
$dmesg
```

---

### Post by llamabr on 2009-04-16
> **subzero316 said:**
> After you plug in type the following command. And see if it says anything about that device in the end.
```
$dmesg
```

Also, while plugged in, the output of df and lsusb

---

### Post by EssexEagle on 2009-04-16
Wow, thanks for the quick responses!

> **ddrichardson said:**
> Does any of [this]("http://ubuntuforums.org/showthread.php?t=866297") help?

This works, thanks ever so much!! :)  And yay for Linux being awesome :)

---

