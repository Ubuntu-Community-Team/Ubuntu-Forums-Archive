---
title: "Need to install ndisgtk"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by melp57 on 2008-07-01
I have installed Ubuntu via Wubi and I am having a problem getting my wireless card to fire up during boot. I need to install ndisgtk in order to install my wireless windows driver. My problem is that I don't have an internet connection, so how can I install it?
The documentation here says to install this program in order to get the wireless working.
thanks in advance.

---

### Post by rasiel on 2008-07-02
yeah catch-22 eh? but obviously you're connected to the net in order to write this post. google the file (there are several versions available depending on version) then put it on a thumb drive and sneaker net it to your ubuntu machine.

that's how i'm doing it. (i'm a rank newbie)

ras

---

### Post by Ayuthia on 2008-07-02
If you have your liveCD (and using Hardy), ndisgtk is on the liveCD.  You could add the CD through Symantic (Through manage repositories->Third Party Repositories). The other way would be to open up the CD and go to:
```
/media/cdrom/pool/main/n
```
There should be two folders--one for ndisgtk and the other is for ndiswrapper.  If you have not installed any of them yet, you will want to install ndiswrapper-common, ndiswrapper-utils, then ndisgtk in that order.  Otherwise, you might get a message that it is missing dependencies.

Hope that helps.

---

