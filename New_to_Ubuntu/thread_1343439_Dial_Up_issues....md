---
title: "Dial Up issues..."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by mb52 on 2009-12-01
Hey there, I'm a recent Ubuntu user, recently installing 9.10, so far its been pretty good, however I've recently had to switch over to dial up internet and I'm having issues getting it running.

I've downloaded Gnome PPP and managed to input all the user info, but when I begin dialing, I get an error that there is no dial tone detected.

Now I know my laptop's modem works, and the phoneline is working, as I'm connected right now through windows.

I'd prefer to get Ubuntu working, so that I can continue using it, as it is better than windows, however I'm at a loss as to what to try next.

Anyone have any thoughts on what I can try? I'm a complete noob so, any advice would best be simple.

Thanks!

---

### Post by ranch hand on 2009-12-01
What modem are you using?  Is it internal or external?

If it is internal you should get it listed by running;
```

lspci

```
That is a lower case L.

---

### Post by Some Penguin on 2009-12-01
You may want to read [http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098) and [http://www.linmodems.org/](http://www.linmodems.org/)

There is a pretty decent chance that you have a software modem.  It is close to certain if it is a PCI modem, which is extremely likely for an internal modem.

---

### Post by mb52 on 2009-12-02
> **ranch hand said:**
> What modem are you using?  Is it internal or external?

If it is internal you should get it listed by running;
```

lspci

```That is a lower case L.

Thank you both for the replies, I tried the above command, and from what I can tell this is my modem

```
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
```

I checked out the other links as well, and ran scanmodem, however the drivers it tells me to download are i386 drivers, which apparently do not work on my AMD machine. I'm not sure what else to do about that....

---

### Post by ranch hand on 2009-12-02
A quick search turned this up;

[https://bugs.launchpad.net/ubuntu/+bug/112149](https://bugs.launchpad.net/ubuntu/+bug/112149)

from way back in 2007.

And this that may give you some direction in looking for an answer;

[http://www.modem-help.co.uk/ATI/chipset.families/SB400-AC97.html](http://www.modem-help.co.uk/ATI/chipset.families/SB400-AC97.html)

I, personally, would get a "real" (hardware) external modem.  No drivers needed and should be faster no matter what OS you are using.  connection should hold up better too.

---

