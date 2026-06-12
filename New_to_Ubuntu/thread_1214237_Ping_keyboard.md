---
title: "*Ping* keyboard"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by WinDevil on 2009-07-15
Hi,

I am wondering if there is any utility or a way to *ping* a keyboard. By *pinging* a keyboard, I mean something similar to *ping* a machine over the network. 

I could check the event file representing the keyboard in ```
/dev/input/
``` directory. The problem with that is the file produces some output only when something is typed on keyboard. While I want to make sure that keyboard *can* be used, even when nothing is typed on it.

Any help would be highly appreciated.

---

### Post by toupeiro on 2009-07-16
well, if its a USB keyboard, and you know the manufacturer, you might have some luck with the lsusb command.  That looks at your USB subsystem and returns everything attached.  thats **sort of** like pinging a usb device with regard to identifying whether or not the system recognizes it, even its its not currently being used, but as far as the keyboard being 100% functional, the only way to tell that is to type on it.  I'd say its no more informational than a ping.  A ping just tells you its connected, that doesn't always mean its functional. ;)

---

