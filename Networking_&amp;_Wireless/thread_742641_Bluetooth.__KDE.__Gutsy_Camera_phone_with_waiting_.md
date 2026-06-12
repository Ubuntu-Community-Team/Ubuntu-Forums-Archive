---
title: "Bluetooth.  KDE.  Gutsy Camera phone with waiting images.  NO WORKY!  HELP!!!!!"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by meldroc on 2008-04-01
Searching the forums, I saw some posts from a few months ago that indicated the KDE bluetooth packages were completely and utterly broken.

I used to be able to transfer images from my phone, but I"m no longer able to - my phone sees my PC, and my PC sees my phone, but when I use Konqueror and I go to bluetooth:/ and click on the icon for my phone, the resulting "folder" I open up is empty.

Anyone know how to fix this?  Anyone?  Anyone?  Bueller?

BTW, if I have to install non-broken packages, are they compiled for AMD64?  I do own a Core 2 Duo, and like any self-respecting owner of such hardware, I have AMD64 Ubuntu on it, so trying to install i386 packages is either painful or impossible.

---

### Post by kwilliam on 2008-04-05
Well, if it use to work and now it doesn't, that's probably a bad sign. However, I have never been able to browse files on my phone with the bluetooth:/ protocol. The URL I use is:
```
obex://[00:XX:XX:XX:XX:XX]/
```
Where 00:XX:XX:XX:XX:XX is the device ID or whatever it's called. (If you don't know the one for your phone, start kbluetooth in the system tray, go to Configuration > Paired/Input Devices and you should see it listed next to the phone's "friendly" name, assuming you've paired it before using kbluetooth. If not, you could go under Configuration > Input Devices and search for it.) Once you have the device ID, you just go to the URL above in Konqueror, and bookmark it. :-)

Of course, this is assuming that the OBEX protocol still works on your computer and there's not something terribly wrong the the KDE bluetooth packages.

Non sequitur:
I'm also saddened to hear that I am apparently not a self-respecting owner of my Core 2 Duo laptop, as I am running the 32-bit version of Gutsy. I was under the impression that 64-bit was not mature, particularly Flash?

---

