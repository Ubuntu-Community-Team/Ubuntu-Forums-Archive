---
title: "Power management or screensaver?"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by tonsil on 2010-02-11
I'm using Ubuntu 9.10. Every ten minutes my monitor goes black, and immeditately returns when I move the mouse. I thought it must be the screensaver. So I went to System->Preferences->Screensaver and unchecked Activate Screensaver when computer is idle. That didn't solve my issue. So I went to Power Management and made sure that "Put display to sleep when inactive for" is "Never" and it is set to default. I also went to startup applications and disabled (unchecked) screensaver. However my monitor still goes dark every ten minutes. Please help me. I want to turn this off. I can't read a book!

---

### Post by SecretCode on 2010-02-11
It's my (unsupported) opinion that settings made in Power Management don't reliably take effect. Try setting it and rebooting straight away.

---

### Post by nhasian on 2010-02-11
in a terminal try entering:

```
xset -dpms
```

this disables the energy star features of the monitor.  then enter:

```
xset s off
```

this disables the screen saver.

see how that works out.

---

### Post by tonsil on 2010-02-11
> **nhasian said:**
> in a terminal try entering:

```
xset -dpms
```this disables the energy star features of the monitor.  then enter:

```
xset s off
```this disables the screen saver.

see how that works out.


The code worked! Thank you very much! :D:D:D

---

### Post by tonsil on 2010-02-12
By the way, I have restarted my machine and it's the same thing again. The screensaver is not active and the power management is set to never. Is there a shortcut to typing the same code again and again at each startup? Is this a bug? Can I add this to startup applications? How do I enter the two codes in one line? Thank you!!

---

### Post by nhasian on 2010-02-12
Go to System->Preferences->startup applications and add this line:

```
bash -c 'xset -dpms && xset s off'
```

---

### Post by tonsil on 2010-02-12
Thank you! :D

---

### Post by dwhitney67 on 2010-02-14
> **tonsil said:**
> By the way, I have restarted my machine and it's the same thing again. The screensaver is not active and the power management is set to never. Is there a shortcut to typing the same code again and again at each startup? Is this a bug? Can I add this to startup applications? How do I enter the two codes in one line? Thank you!!

It makes me wonder if it is indeed a bug.  I have the same issue with my laptop, although I want the opposite of what you want.  I do want my (external) monitor to sleep when not active for say, 5 minutes.  But no matter what I do, my settings (via Power Management) are ignored.

I just got the latest kernel the other day; I wonder if there is a connection.  I am running Ubuntu 9.10 with release 2.6.31-19-generic of the kernel.

My screensaver (which is blank) is activated after 2 minutes (which is good), but the APM stuff never goes into effect.

---

