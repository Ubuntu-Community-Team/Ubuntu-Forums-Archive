---
title: "Picture frozen when coming out of screen saver"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by gannon12raiders on 2009-11-21
Hi,

I'm having a slight issue when I try to use a screen saver. By default, the screen saver is off on 9.10. I had it this way for a little while now, but decided to go ahead and try some out.

When I lock the screen, the screen saver starts up, it's all good. As soon as I move my mouse, I can see the cursor and move it around. However, the screen saver picture is frozen on the screen. If I type in my password (note here that I can't see the dialog box - I just assumed it must be there) I'm back at my desktop with no issues.

This is only a problem because any other user walking up to this computer won't know that a login prompt even exists...

anybody have any pointers?

---

### Post by emigrant on 2009-11-21
i guess you have ati card; had the same issue; disabled screensavers ;)
```

lspci | grep VGA

```

---

### Post by gannon12raiders on 2009-11-21
So there's no way to use screensavers with an ATI card?

...I'm impressed?

---

### Post by emigrant on 2009-11-21
man i can live without it :D

---

### Post by gannon12raiders on 2009-11-21
It's just too bad that I can't get full functionality out of my card. I mean, I spent over 100 bucks on it, I expect to be able to run screensavers.

Oh well. Guess that's part of the reason I'm dual-booting.

---

### Post by emigrant on 2009-11-21
i bet you have another problem unnoticed, which i have with that card :D

see whether you can enable 'extra visual effects' on both user accounts at the same time.

---

### Post by julkops on 2009-11-27
> **emigrant said:**
> i guess you have ati card; had the same issue; disabled screensavers ;)


I don't think it's the card. I have a similar problem. After resume i get a black screen or a frozen screen saver picture. As long as I move the cursor i can see it. I can log to another terminal and restart gdm. Once in 5 times I even get to log in properly and then everything works fine.

My card:
```

$> lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

---

