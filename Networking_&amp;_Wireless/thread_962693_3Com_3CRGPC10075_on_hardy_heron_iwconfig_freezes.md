---
title: "3Com 3CRGPC10075 on hardy heron: iwconfig freezes"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by yo_marcus on 2008-10-29
Hello.
I'm running Ubuntu Hardy on an IBM Thinkpad T30. I aim at using my 3com pcmcia 3CRGPC10075 wireless card, but I have some difficulties.
I installed ndiswrapper-utils-1.9, ndisgtk and so on, following the standard procedure with the 3com windows driver I got from 3com website (windows XP version unpacked and - I suppose - correctly installed, it should be mrv8335x).

Well. I tried your comprehensive ndiswrapper troubleshooting guide, and I got
```
$ ndiswrapper -l
mrv8335x : driver installed
$ uname -m
i686
$ sudo lshw -C Network
```
and system freezes. What I mean?
[LIST]
[*]I cannot CTRL+C *lshw*
[*]I cannot *kill* (or *kill -9*) the *lshw* process
[*]I cannot *sudo* anything
[*]I can login from any of the ttys, but I can't *sudo*, *reboot*, *shutdown* etc.
[*]I can open a new tab in that gnome terminal, but I can't open a new terminal
[*]the same with every other program e.g. firefox
[*]the same if I try *iwconfig*, instead of *lshw* (I first noticed this problem with *iwconfig*, I tried your troubleshooting a couple of hours ago)
[*]my 3com led is on
[*]I got no problems installing the ndiswrapper module - only, no delay when modprobing ndiswrapper
[*]I can only reboot my system, with CTRL+ALT+DEL from any of the ttys
[*]Sometimes I can reboot/shutdown with the gnome red button, if I'm speedy
[/LIST]

Searching the forum I found a lucky guy who got this card working... perhaps I'm not as lucky as he is :(

Thank you in advance.

---

### Post by prshah on 2008-10-29
> **yo_marcus said:**
> 
```
$ ndiswrapper -l
mrv8335x : driver installed


Well, it doesn't seem to have found your device; the proper output should be similar to

> 
[code]
geetha@geetha-desktop:~/inf$ ndiswrapper -l
wg311v3 : driver installed
        device (11AB:1FAA) present

```

Note the last line, where the device is detected.

Are you sure you're using the right driver? Did you "modularize" the driver ```
sudo ndiswrapper -m
``` and then run a depmod ```
sudo depmod -a
```

---

### Post by yo_marcus on 2008-10-29
My mistake, I miscut the original output... that was *before* plugging in the pcmcia, when I was just calling *ndiswrapper -l* to check if the driver name was mrv8335x or something else... ;)

With the card plugged in, I correctly get *device XXX present* (XXX is the same listed in *lspci*, of course).
I modularized and depmodded before and after rebooting, but the problem remains the same.

---

### Post by wamcvey on 2009-11-12
Did you ever get this solved? I am having very similar behavior under Karmic with the same card. ndiswrappers sees the card, but anything touching the network interfaces (iwconfig, ifconfig, etc) hang indefinitely. Dmesg shows the hardware as recognized and shows all the auth methods, but nothing happens because of the freeze ups. Frustrating that this is still happening more than a year after the initial thread was started.

---

### Post by yo_marcus on 2009-11-13
Of course the problem did NOT get solved. It seems like using 3Com wireless devices on Ubuntu (and eventually Linux) is not a good idea.

---

