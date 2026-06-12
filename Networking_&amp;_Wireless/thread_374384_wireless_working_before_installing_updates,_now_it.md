---
title: "wireless working before installing updates, now it doesn't"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by wesmsl on 2007-03-02
I'm a fairly new ubuntu user and I finally got my wireless card to work on my laptop using this guide. -----> [http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092)

I am using edgy eft on a dell latitude D510 with a dell wireless 1470 dual band wlan wireless card.

Then I downloaded and installed all the updates.  The wireless worked no more!  Under System, Administration, Networking, it didn't even show the wireless card.  Is there some update that screws up the configuration I already did?  I would like to update my system fully, but I would also like wireless.  If anyone knows about this that would be helpful.

Thanks,

---

### Post by Westrayn on 2007-03-02
I have a similar problem with 6.10 and a wired network, any help or pointers would be greatly appreciated.

Thanks

---

### Post by wesmsl on 2007-03-02
Well I reinstalled everything.  Set up the wireless for the second time, it worked until i installed the updates.  This time, i redid all the configuration settings i made.  The wireless works with the updates installed!

---

### Post by nyinge on 2007-03-02
It is because whenever you update the kernel, you have to recompile and reactivate the ndiswrapper module.

---

