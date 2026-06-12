---
title: "[SOLVED] Xserver will not start, no screen found"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by laurielegit on 2008-12-22
I installed a new graphics card (Asus EN7300RC512) and installed the apropriate drivers. I had not removed my old graphics card (As it is a internal motherboard one). Ubuntu then told me to restart the computer, so I did, and left all the cables alone. When it booted back up, I was greeted with a blue screen saying that Xserver could not start, and that it had found no monitors. At this point the monitor was still plugged into the old graphics card, and when I pluged it into the new one, it behaved as if it was not plugged in at all. Can anyone help?

Thanks,

Laurie

---

### Post by Mazza558 on 2008-12-22
If you can get to a terminal, try this:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by laurielegit on 2008-12-22
> **Mazza558 said:**
> If you can get to a terminal, try this:

Yes I can get to terminal. I tried that, but it did not seem to do anything. It gave me a warning about overwriting somthing or other. I then tried it again but added -f to force it. It then displayed a long list of warnings of some kind.

---

### Post by taurus on 2008-12-22
After you ran that command from a prompt, what happens if you start up X server?

```
startx
```

p.s.  If you are using a new add-on graphic card, it's better to go into the BIOS and "turn" off the onboard graphic controller.

---

### Post by laurielegit on 2008-12-22
> **taurus said:**
> After you ran that command from a prompt, what happens if you start up X server?

```
startx
```

p.s.  If you are using a new add-on card, it's better to go into the BIOS and "turn" off the onboard graphic controller.

I'm a bit woried about turning off the onbord graphics controller as the only card that is working with my monitor is the inbuilt one. Would turning off the controller disable this?

---

### Post by taurus on 2008-12-22
If your monitor only works with the onboard graphic card, then why would you add a new video card to your machine?  Which video card does the monitor connect to right now?

---

### Post by laurielegit on 2008-12-22
> **taurus said:**
> If your monitor only works with the onboard graphic card, then why would you add a new video card to your machine?  Which video card does the monitor connect to right now?

My monitor *should* work with both the graphics cards. The monitor conncets to the onboard graphics card. Using this card, it can display terminal and other text. Formerly it could run Xserver, but adding the new card seems to have thrown it. I added the new card because I was not happy with the performance from the onboard one. 

> **taurus said:**
> After you ran that command from a prompt, what happens if you start up X server?

```
startx
```

I did this, and it failed to start X server. It was just the same message as I encountered before.

---

### Post by laurielegit on 2008-12-22
Ok, I disabled the onboard graphics card, which made no difference. I then followed your commands, and it started. Thank's loads,

Laurie

---

