---
title: "Stuck at Grub Rescue Prompt after upgrading to 10.10"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by diablo75 on 2010-12-01
A friend of mine sent me an email this morning saying he tried to upgrade and somehow managed to hose his Grub menu in the process.  He says what he sees now at boot is:

Boot from CD:
error:  symbol not found:   'grub_putchar'.
grub rescue >   (cursor blinking)

My plan of attack to repair this is to reinstall Grub with a Live CD.  What's the easiest way to do this?

---

### Post by sikander3786 on 2010-12-01
I think that error appears when some older version of Grub is still present (with no apparent reason) in the MBR while Grub2 is also installed.

You can try booting from the Grub rescue prompt.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Or reinstalling Grub from Live CD will definitely fix that. The easiest method is here. Just 2 commands.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Or it can get even easier if you can post the output of your bootinfoscript :P

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by 666f6f on 2011-08-27
Just stumbled upon this issue myself. I solved it by explicitly setting the grub install location during installation.

---

### Post by Hammi on 2011-10-02
I can confirm this: When the installer asks whether or not to install grub into the MBR, say no and explicitly choose the MBR(!) of the applicable HDD.

---

