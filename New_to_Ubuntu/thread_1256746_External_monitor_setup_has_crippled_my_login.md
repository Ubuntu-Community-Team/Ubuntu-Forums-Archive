---
title: "External monitor setup has crippled my login"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Eikokubyo on 2009-09-03
Hey all,

Quick question: 
I just now tried to set up my Ubuntu 9.04 Toshiba Dynabook 1610 to use an external monitor. I went through the Monitors preference setting dialog, unchecked "mirror screens" and set the resolution to the appropriate values, then hit apply.

I got an alert box that said Ubuntu would set some kind of internal preferences (a profile? monitor profile I think) and asked if it was OK. Remarked that it would be a good idea to do so. I figured what does this machine have to gain from lying to me, so I hit it. Then I got prompted to log out and back in again.

I logged out.

That was the last I've seen of my OS since. 

Now all I have when I turn the computer on is a big blue screen with two bars of lighter and darker blue on the right side. And a mouse cursor with nothing to click on.

Before I reinstall the OS from scratch, can anybody tell me if there is a non-drastic fix for this problem? I'd much appreciate it.

Sincerely yours
Ei.

---

### Post by zkriesse on 2009-09-03
Well to start with I'm assuming that you want the external monitor to display only. Well, you unchecking the mirror screens option right but you forgot an important detail. Click on the laptop monitor off...click mirror screens off, then click on the laptop monitor picture in the options window and turn it off. Hit apply and when it asks you if you want to keep those settings naturally you should click yes. After that close the window and your done!

---

### Post by blackened on 2009-09-03
It could be as ZachK18 suggested and your monitor is locked in an out-of-range setting. Fixing this might be as simple as unplugging your external monitor, closing the laptop lid, and re-opening it; or it might be as difficult as booting into recovery mode (from grub) and getting back to a more appropriate resolution that way, again with the external monitor unplugged.

If it is neither of those, then the question that it asked may have been if you wanted to set a virtual resolution in xorg.conf. This may have FUBARred xorg, but as long as you hadn't crafted a very specific xorg.conf by hand, then restoring it back to plain old default is as simple as
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by Eikokubyo on 2009-09-03
Wow! Thanks for such a quick response!

Those all sound like great fixes, and I'd love to implement them, but they all require that I first login, which I can't.

You wouldn't have any ideas on how I can login, would you?

Thanks

Edit: Wait. blackened said something about a "recovery mode". That sounds useful. What is that and how would one get into it, exactly?

And I believe that the alert box I got DID refer to xorg.conf, so that's probably it. I think you've hit the problem. Also, during the screen setup, one of my monitor icons (in the Monitors dialog window) was green and one was pink. Do you think that pink means problem and I should only hit "Apply" if both are green?

Thanks!

---

### Post by mano the shark on 2009-09-03
Recovery mode is accessible when grub loads while booting (usually second selection).  You should be able to access a command prompt after the computer is running by pressing ctrl+alt+F4 (F1-F6 tty and F7 Xorg).

---

### Post by Eikokubyo on 2009-09-03
Thanks!

Ctrl+Alt+F4 plus blackened's command line magic did the trick - thanks for showing me these EXTREMELY useful functions. 

I figured out the problem, by the way: turns out you can't run multiple monitors with Compiz turned on. After I set Desktop Effects to "none" everything worked OK.

---

### Post by blackened on 2009-09-04
Glad you got it sorted. Display problems are always a pain.

---

### Post by LewRockwell on 2009-09-04
> **blackened said:**
> Glad you got it sorted. Display problems are always a pain.

Compiz is a pain as well

.

---

### Post by zkriesse on 2009-09-04
> **LewRockwell said:**
> Compiz is a pain as well

.
Yeah it is...I tried it once...once was enough....

---

