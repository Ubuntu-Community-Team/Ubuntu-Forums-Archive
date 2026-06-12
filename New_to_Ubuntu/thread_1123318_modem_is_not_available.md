---
title: "modem is not available"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by mihan224 on 2009-04-12
Hi guys
My laptop brand is HP Pavilion dv5000 / AMD turion 64 and i use ubuntu 8.10
I can't connect via my dial up modem
the modem port is /tty0 and my ubuntu has recognized that but i think there is something wrong white my serial ports . I want you to help me immediately.

---

### Post by HereInOz on 2009-04-12
I am not too sure but I believe that dial up "winmodem" type modems, which this one is, I reckon, are not all that well supported by Linux generally.  

There are techniques for installing the drivers and configuring the modem, but I have not had great success with them.  Linux works much better with external serial modems, but then you probably don't have serial ports on that machine.

Good luck and I hope someone who has had success with these devices can assist you far more than I can.  Try searching these forums for "winmodem" and that sort of thing, and you may find what you seek.

---

### Post by lkraemer on 2009-04-12
Please have a look at Post #4 in this thread.
[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

If you have a Windows Modem (WinModem) you probably will have
trouble getting it to work, even with the help of the folks at
[www.linmodems.org](www.linmodems.org), but it is worth a try.  I'd suggest getting 
a used External USR modem and using it.  Or there are USR USB Modems sold
at Walmart for $44.00 (and probably Amazon) that work good.  It will save
you days of fighting with your configuration.

Either way, the guide should be of help.

Keep me informed of anything that needs corrected, or updated.

lkraemer

---

### Post by ivanvajar on 2009-04-12
Search for MartianModem drivers. You will also need to find out how to configure COM (tty) ports. Dial provider using wvdial. I'm sorry for not being able to provide more detail on this right now. This is how I made my winmodem to work in Ubuntu.

---

### Post by zerhacke on 2009-04-12
Actually Ivan, I think they would be better served with Gnome-PPP instead of wvdial.

---

