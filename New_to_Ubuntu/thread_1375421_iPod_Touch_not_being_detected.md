---
title: "iPod Touch not being detected"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Ebonhawke on 2010-01-07
OK - I went out and bought myself an iPod Touch 3rd Generation today.  I was aware that Apple's iTunes only supported MAC OS/Windows, but saw a number of discussions on these forums that indicated that even if you were using Linux (currently on Karmic Koala) that it wasn't a big issue.

I tried some of the work arounds posted on these forums with some success, but wasn't able to get the iPod initialized - finally figured out that I needed to connect to iTunes the first time to 'activate' the device.  I set up a VirtualBox with Windows XP and was able to make things work.

Because I had only installed a 'demo' version of Windows, I wanted to try and manage content through Linux.  In reading a number of articles on the web and discussions on these forums, it seemed I needed to 'jailbreak' the device.  I tried the 'Blackra1n' method, which caused the iPod to go into recovery mode, which isn't a big deal according to the apple website, but failed to jailbreak the device.  The FAQ on the Apple web site indicates that all you need to do is reconnect into iTunes and the iPod will be restored.

Of larger consequence is that Ubuntu doesn't recognize the iPod anymore, so when I try to activate the iPod in the virtualbox so that itunes 'sees' it, the option is grayed out.  I was able to see the iPod in Linux before creating the VB, and can't now.  I tested out the USB ports with another device to make sure that those hadn't been damaged, and the other devices were recognized

Help?  Just trying to get back to Linux/Windows seeing the iPod and connecting to iTunes

---

### Post by Ebonhawke on 2010-01-07
OK - think the problem may be that the iPod isn't mounting properly (or at all).  Googling for help, but your help would be appreciated too :)

---

### Post by Ebonhawke on 2010-01-07
Using [http://cgsbay.com/ipod-iphone-karmic-koala/](http://cgsbay.com/ipod-iphone-karmic-koala/) reference, I get the following message in Terminal when trying to mount 

[I]usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
[/I]

---

### Post by fanum on 2010-02-07
Yes, I was having this problem when trying to set up the new iFUSE sync method for gtkpod. Turned out usbmux was not running. type this into terminal and try again:

sudo usbmuxd -f

---

