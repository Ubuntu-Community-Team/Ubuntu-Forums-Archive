---
title: "Ubuntu is running in low-graphics mode"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-12-13
After running fsck at start up, I encountered this message:

Ubuntu is running in low-graphics mode
Your screen, graphics card, and input device settings
could not be detected correctly.  You will need to
configure these yourself.

I have been using ubuntu on and off for about a year now and I have never had any problems with drivers on this lappy of mine: everything always 'just worked'.  Now this.  How do I get ubuntu to detect my screen, graphics card and input device settings?  And if I have to configure these myself, then I'll need a lot of guidance to do this.

My graphics card is: ATI Technologies Inc RS690M [Radeon X1200 Series]

-Yos

PS This bug has just been confirmed on launchpad.  If anyone else has this problem, please subscribe [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/495973")

---

### Post by hoppipolla on 2009-12-13
I had this problem recently! And yeah it was a nightmare to get it to start in normal mode again!!

Weirdly, the time that fixed it for me is when I did this:

```
sudo rm /var/log/Xorg*log*
```


Sounds dangerous I know but I promise all it's doing is removing the logs at X writes upon starting up. On mine, the second I removed them, bizarrely it just worked and booted into my standard desktop!

It might be best to dip into /var/log and back them up quickly into a different directory just in case we need to read them later to determine where X went wrong, but deleting the X logs won't do any harm :)

Let me know if it works anyway, if not we'll start thinking about drivers and checking things further!

Hoppi

---

### Post by YosefKaro on 2009-12-13
Hoppi,

Thank you for coming to help me out :)  I did as you suggested but it did not work.  So, what is the next step ?

-Yos

---

### Post by NoaHall on 2009-12-13
> **YosefKaro said:**
> Hoppi,

Thank you for coming to help me out :)  I did as you suggested but it did not work.  So, what is the next step ?

-Yos

Try this - 
```
 sudo mv /etc/X11/xorg.conf /etc/X11/xorg.back.conf
```
Then, reboot, and see if it works.
You could also try -
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by YosefKaro on 2009-12-13
That's part of the problem: I don't have a /etc/X11/xorg.conf file to begin with.  Looks like I have to make it from scratch but I have no idea where to begin to do that for ATI.

-Yos

---

### Post by NoaHall on 2009-12-13
In karmic, it doesn't use a fixed-xorg.conf, it makes one on the fly - I thought I'd just check. I'm not sure what to do, because I'm used to nvidia cards, not ATI.

---

### Post by YosefKaro on 2009-12-13
Guess that is part of the problem with being on the cutting edge of technology...You can get caught alone, dangling on a thin limb.

-Yos


Ooops, that wasn't tomboy notes :D

---

