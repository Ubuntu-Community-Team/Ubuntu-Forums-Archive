---
title: "grub text too big"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by philkippy on 2009-03-05
hey, first I'd like to thank you all for your willingness to help others out. your time and know-how are very helpful, I've already learned alot just by reading other threads. this, however, either has not been dealt with, or I don't know how to search for it.

when I boot up the text in grub is way to big, almost as if it thinks my screen is a smaller resolution than it actually is. I had thought that was just the way it goes, but then yesterday I used unetbootin and when I booted into a linux from unetbootin the text suddenly got smaller (how it ought to be). this is not the actual desktop either, it is the text that shows loading progress. the standard login screen for ubuntu is also very big. I changed the dpi in ubuntu, but that only counts for the desktop.

just to check, I downloaded a finnix iso (console only linux live cd) and ran it with unetbootin. same thing happened. as soon as I hit enter to boot into unetbootin the text turns good. next, I added a small partition in my hard drive and copied the iso files there so I could boot to it. when I boot to finnix on my hard drive the text is big, while from unetbootin it is small.

can anyone tell me why this happens and how to change it? (I want to understand, not just fix it if possible)

---

### Post by fooman on 2009-03-05
i have no idea why....but, you could try using startup-manager to change the boot resolution.

to install startup-manager,  open a terminal and type or copy/paste:

```
sudo apt-get install startupmanager
```after it installs,  find it in system > administration > startup-manager

look under the "boot options" tab > display > resolution.

hope that helps.

---

### Post by philkippy on 2009-03-05
that didn't work, after rebooting the resolution in boot-manager goes back to being blank. I can select different resolutions, they just don't seem to be doing anything.

thanks though.

---

