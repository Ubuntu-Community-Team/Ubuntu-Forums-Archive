---
title: "can't partition HDD's"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by snowman12 on 2009-02-13
lappy just came back from repairs and the first thing I did was try to install ubuntu via WUBI.
The windows side works fine, but but once it reboots into ubuntu I get stuck at step 4 (prepare partitions). It doesnt show any hdd's in the list and all the buttons except for "forward" "back" and "quit" are greyed out.
Am I going mad?!?! :confused:

---

### Post by HermanAB on 2009-02-13
Run chkdsk in Windows and then try again.

Cheers,

Herman

---

### Post by TohBee on 2009-02-13
maybe this helps:

[http://forum.ubuntuusers.de/topic/dell-inspiron-530n-ubuntu-pc-:-wirklich-linux/](http://forum.ubuntuusers.de/topic/dell-inspiron-530n-ubuntu-pc-:-wirklich-linux/)

---

### Post by snowman12 on 2009-02-13
Herman, 

ran "chkdsk /F"
nothing happened.

Tohbee,

umm, what part exactly? it makes for a difficult read even with google translate ;)

---

### Post by caljohnsmith on 2009-02-13
Hi snowman12, how about posting a screen shot of what you are seeing, and also please post:
```
sudo fdisk -lu
```
And if you have more than one HDD, let us know which one you want to install Ubuntu to.

---

### Post by snowman12 on 2009-02-13
caljohnsmith,

attached are screenshots of what i see @ startup and the terminal output

hope this helps

---

### Post by caljohnsmith on 2009-02-14
So just to clarify, are you trying to install Ubuntu via Wubi again inside Windows? And are you doing it from the Live CD?

---

### Post by snowman12 on 2009-02-14
I started out from WUBI, got to the part where you shut down and reboot into ubuntu to finish the intstallaton, no problems. But when it asks to partition the HDD (There is only one BTW), it doesnt show up. I click on quit and it starts a live session, with or without the liveCD.
I only ran WUBI once (should I try reinstalling?) and if I run the install app/script on the desktop in a live session i get the same problem.

Funny though, the installer detects my flashdrive when I boot with it plugged in.

If you need any more info, just ask
thanks!

---

### Post by snowman12 on 2009-02-15
I uninstalled WUBI, then started a proper live session and ran the installer from there and. . . .


[SIZE="3"]SUCCESS!!!!!![/SIZE]


it detected my HDD!!!


new problem though,

It only shows two partitions and I need three. (windows, ubuntu, and a windows recovery partition).

Isn't there supposed to be a slider where you set how much breathing room windows gets?

anyway this is what I'm seeing

---

### Post by caljohnsmith on 2009-02-15
Glad to hear the installer at least sees your HDD now. I would recommend using gparted (Ubuntu's partition editor under System > Admin > Partition Editor) to first shrink whichever partition you want to make room for Ubuntu, and then you can manually set up your Ubuntu partitions with gparted. Or you could choose the "manual" partition option in the installer, and I think you can do basically the same thing. Here are a few guides that you might find helpful:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html) (manual partition setup)
[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html) (using gparted first)

Good luck and let me know how it goes.

---

### Post by snowman12 on 2009-02-15
:P:P:P:P:P:P:P:P
it's working fine now

thank you all soooo much!!

---

