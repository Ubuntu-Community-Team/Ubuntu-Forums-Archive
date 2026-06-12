---
title: "Boot Problems"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-28
K, I booted my computer that has my apache server on it and I get to the screen just before the login screen and I just get stuck at that circle. My web site is up and I can access my shares on my network. I booted from the live CD and ran fsck on all my ext3 partitions and it said their clean. I can hit ctrl+alt+F1 and log into the prompt but startx don't work. Please, I need to get this running, re-install is not an option.

---

### Post by Praxicoide on 2009-01-28
Have you tried reconfiguring x after logging into a prompt?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by balaknair on 2009-01-28
Yep, seems more like an X-Server error than a boot issue to me. It could also be a hardware issue(video card acting up?) but then the Live CD GUI probably wouldn't work either. So I'm guessing it's your Xorg.conf that's messed up.

Suggestion: either use tty1 with ctrl-alt-F1 and *sudo dpkg-reconfigure -phigh xserver-xorg* or just boot into recovery mode from GRUB and run a diagnostics check to see what's wrong(is your install detecting your video card).

---

