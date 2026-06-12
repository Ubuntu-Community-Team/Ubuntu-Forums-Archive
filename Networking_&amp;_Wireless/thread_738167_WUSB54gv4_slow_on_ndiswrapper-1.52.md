---
title: "WUSB54gv4 slow on ndiswrapper-1.52"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2008-03-28
Things I have tried:
1) Installed ndiswrapper-1.52:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=588045&page=13](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=588045&page=13)
2) Failed to install ndiswrapper-1.8:
[http://www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html](http://www.linuxforums.org/forum/wireless-internet/64463-installing-wusb54g-ubuntu-wireless-adapter.html)
3) No ndiswrapper approach: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=588045](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=588045)

Each method requires that I blacklist either "rt2500usb" or "rt2570." I can only get an internet connection when I blacklist rt2570, though. Even then, the connection is extremely slow. So, it's either blacklist rt2500usb and get no connection, or blacklist rt2570 and get a slow one. How have three how-tos failed to give me a decent connection?

---

### Post by dstew on 2008-03-28
What is the output of```
ndiswrapper -l
```?

---

### Post by xjgnsdof on 2008-03-28
rt2500usb: driver installed
            device (13B1:000D) present (alternate driver: rt2570)

---

### Post by dstew on 2008-03-28
[This thread]("http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/") shows the same process you are going through. The confusion may be that the .inf file for the Windows driver that you install into ndiswrapper has the same name as a linux binary driver, that is, rt2500usb. Hence you get the funny statement:```
rt2500usb : driver installed
device (13B1:000D) present (alternate driver: rt2500usb)
```You have to blacklist the linux binary driver rt2500usb if you get this statement. By blacklisting that driver, you are not touching the ndiswrapper-enclosed driver at all.

From your ndiswrapper -l output, I can only recommend that you blacklist the rt2570 driver. However, I suspect that the binary rt2500usb driver may be lurking somewhere, ready to strike. Just for fun, try```
sudo modprobe -r rt2500usb
```and see if you get any better performance.

---

### Post by xjgnsdof on 2008-03-28
I blacklisted rt2570 already, but it's slow as hell. Also, the error message that you think I got is not quite correct: mine lists another driver as the alternate. I'm still confused as to what to do, here.

---

### Post by xjgnsdof on 2008-03-28
I'm please to report that I am posting this with the help of my (roommate's) Linksys WUSB54Gv4 wireless adapter!

I followed the directions at the URL you gave me, and it works. I didn't even have to reboot. There were some steps there that I never followed in other guides, so I can see why it works perfectly now. Thanks for pointing me in the right direction.

---

