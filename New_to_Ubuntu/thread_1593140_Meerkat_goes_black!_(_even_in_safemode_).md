---
title: "Meerkat goes black! ( even in safemode )"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by norbird88 on 2010-10-11
I don't know what's wrong.
- i haved a fresh install of 10.0 --- worked fine
- activated the graphic driver from ATI ( my card is 4670 HD ), restarted --- still worked fine.
- tried to complied gyachi ( successfully) --- still worked fine.
- restarted again ---> Then the screen go black with something like a cursor there.

- I tried to boot to the safemode. Seem ok until reach the options. When i tried to choose from the solutions menu, the screen went black again. And this time, completely black.

What's wrong? What could I do ? ( if not a fresh install again :mad::mad::mad:)

---

### Post by Dougie187 on 2010-10-11
If you can get to a terminal you could check the logs. Or you could boot to a live cd to check the logs as well.

The latter is more difficult as you have to mount your hard drive manually. But one of the options when you are booting should be something about exiting to terminal login.

Once there you can check /var/log for the logs, and go through syslog or messages and look for the time when it went black.

---

### Post by norbird88 on 2010-10-11
> **Dougie187 said:**
> If you can get to a terminal you could check the logs. Or you could boot to a live cd to check the logs as well.

The latter is more difficult as you have to mount your hard drive manually. But one of the options when you are booting should be something about exiting to terminal login.

Once there you can check /var/log for the logs, and go through syslog or messages and look for the time when it went black.

Things is getting weird!. When in Recovery mode, the solutions menu only show about 5s. After 5s, if i don't choose an options fast enough, the screen becomes black, grey or red ( wth ? ).

-I could access to the root terminal now ( fast picking the option)
But yep, i'm a noob and know nothing to do now.
-I tried to load the falseSafeX---> succeed. Tried reconfigure the X ---> nothing happened. Other options like use default and load backup configuration result in nothing, too.
The only thing seems work is the logs. But i read it and didn't understand much.
- any suggestion? Or how can i post these logs here for you guy to have a look? I have only one PC which dual boot Windows 7 and Meerkat.

---

### Post by Quackers on 2010-10-11
Does ctrl+7 do anything?
Try startx in the terminal and hit enter

---

### Post by norbird88 on 2010-10-11
> **Quackers said:**
> Does ctrl+7 do anything?
Try startx in the terminal and hit enter

- I tried many shortcut keys, and the only one worked is Crtl+alt+del ( only in normal mode, which restart my PC )
- I found more colors, this time are white, green and yellow.
  
- I actual couldn't access to the terminal, the sreen go black with a freezing cursor right after that! :confused:

---

### Post by brydonhunter on 2010-10-11
It sounds more like a problem with your ATI driver. I had many problems at the beginning, sort of stable now.

Try removing all fglrx* drivers and rebooting into Ubuntu generic driver.

---

### Post by norbird88 on 2010-10-11
> **brydonhunter said:**
> It sounds more like a problem with your ATI driver. I had many problems at the beginning, sort of stable now.

Try removing all fglrx* drivers and rebooting into Ubuntu generic driver.

Yep, i had the same guess at first.
But:
- how can the screen still goes crazy in the Recovery Mode ? ( i mean, the fglrx drivers are not loaded right ? )
And, as i mentioned. The first reboot after activated the drives is smooth with no problem!
- how could i do anything if i can't access to the terminal? :confused:

---

