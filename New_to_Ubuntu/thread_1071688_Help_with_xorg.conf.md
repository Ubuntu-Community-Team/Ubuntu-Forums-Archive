---
title: "Help with xorg.conf"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by megaJuice on 2009-02-16
I recently tried to install my new ATI Radeon 9550 and couldn't get it to work, so I'm giving up and going back to the generic card that came with my computer. How do I revert xorg.conf to the generic card I have? Is that even what I have to change? I have no idea, and I just want my computer back to how it was. I'm stuck in low-graphics mode for now.

---

### Post by ajgreeny on 2009-02-16
Take out your new ati card, then boot to recovery mode and choose xfix (I think that is what it's called in 8.10, it certainly is in 8.04).  Let the system detect the onboard or generic card, and then go to a normal boot and you should be back to the GUI you started with when you installed.

---

### Post by megaJuice on 2009-02-16
ok I'll try it.

---

### Post by bodhi.zazen on 2009-02-16
> **megaJuice said:**
> I recently tried to install my new ATI Radeon 9550 and couldn't get it to work, so I'm giving up and going back to the generic card that came with my computer. How do I revert xorg.conf to the generic card I have? Is that even what I have to change? I have no idea, and I just want my computer back to how it was. I'm stuck in low-graphics mode for now.

You should also be aware that xorg.conf is now depreciated.

The intent of xorg is to improve auto detection of hardware, which is nice when it works.

But the problem is that previous techniques or edits to xorg.conf often do not work either :(

For example I have an old box at home, no version of linux recognizes the graphics.

The fix is a simple edit to xorg.conf

However the edit does not work beyond (xorg) 6.9

---

### Post by megaJuice on 2009-02-16
> **ajgreeny said:**
> Take out your new ati card, then boot to recovery mode and choose xfix (I think that is what it's called in 8.10, it certainly is in 8.04).  Let the system detect the onboard or generic card, and then go to a normal boot and you should be back to the GUI you started with when you installed.

Did it. Didn't work. Is there anything I should post to give more info as to the problem?

---

### Post by Dark006 on 2009-02-16
Not sure if this will help you (it usually works for me) but if you can get to a shell, try:
```
sudo dexconf
```
and restart. That usually just makes a default xorg.conf file and will work fine (at least in my case).

---

### Post by megaJuice on 2009-02-16
As far as I can tell, that didn't do anything... I'll try again though.

---

### Post by malathion on 2009-02-16
megaJuice, if I may ask, what problems were you having with the Radeon card that you couldn't resolve?

---

### Post by megaJuice on 2009-02-16
> **malathion said:**
> megaJuice, if I may ask, what problems were you having with the Radeon card that you couldn't resolve?

I followed every tutorial that I could to install the drivers and make the card work, but every time I would start my computer I would get to the Login screen with no problems, then after I logged in the screen would be a mess of diagonal stripes that (I'm guessing) were the desktop. I can see my mouse and everything on the screen, but it was all spread out and broken on the diagonal lines. I don't know if I made a mistake installing the drivers, or if it was a problem with my monitor's Vertical or Horizontal Sync rate. I'm a complete newbie to Ubuntu, and have no idea what to do.

---

### Post by malathion on 2009-02-16
> **megaJuice said:**
> I followed every tutorial that I could to install the drivers and make the card work, but every time I would start my computer I would get to the Login screen with no problems, then after I logged in the screen would be a mess of diagonal stripes that (I'm guessing) were the desktop. I can see my mouse and everything on the screen, but it was all spread out and broken on the diagonal lines. I don't know if I made a mistake installing the drivers, or if it was a problem with my monitor's Vertical or Horizontal Sync rate. I'm a complete newbie to Ubuntu, and have no idea what to do.

OK thanks, you are not having the same problem I am having. I would be interested to know whether you got the same error with the LiveCD and with other operating systems after reseating and cleaning the contacts. It is possible that your card is simply defective and should be RMA'd.

---

### Post by sarang on 2009-02-16
Are you folks sure that xorg.conf is going to go? To the best of my knowledge, the default build will have a blank xorg.conf because of auto-detection, but the use of the file for customization has not been deprecated.

Anyway, for a tutorial on using xorg.conf, try 
```

man xorg.conf

```
in a terminal. I have often considered it to be a very well written **man**ual.

---

### Post by megaJuice on 2009-02-16
I'll give it a shot, and let you know how it turns out.

---

### Post by megaJuice on 2009-02-16
Yeah... Still no idea what to do. Anymore suggestions?

---

