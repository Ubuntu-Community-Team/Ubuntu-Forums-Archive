---
title: "Soft shutdown fail after updating drivers!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-02
This problem occurred on my last install of Kubuntu, and the only way I got it fixed was to reinstall!  >=(  I don't want that to happen again..

So last night I updated my video drivers to the latest Catalyst 9.1.  Things didn't go smoothly, but I learned important things!  (Like that aticonfig is just a program to help with xorg.conf editing)  The hiccup I had was an error about a line "Disable dri2", which I removed in order to solve the problem and continue with --initial.

So now Kubuntu won't shutdown by itself..  It logs out, and at least once left Konqueror open, window decoration-less, against a blank background.  Other times, it's just a blank screen.  Ctrl+Alt+Backspace caused a slight flicker once, but didn't help.  Pushing the power button at this point on my PC initiates the **real** shutdown sequence, and the Kubuntu logo appears and reverses the loading bar, like normal, and shuts off..

Any ideas?

---

### Post by Gotaro on 2009-02-02
Bump.  Is Kubuntu just broken?

---

### Post by Crafty Kisses on 2009-02-02
Does it shutdown all the way when you run this command?
```
sudo shutdown -r now
```

---

### Post by Gotaro on 2009-02-02
> **Codename said:**
> Does it shutdown all the way when you run this command?
```
sudo shutdown -r now
```
It does restart successfully with that command.  There is still a noticeable lag after I've logged out and the music stops (like 10+ seconds) before the Ubuntu logo appears and starts to unload.  There used to be only maybe a few seconds pause before the logo appeared, if that means anything.

--Edit--
Logging out also fails, leaving me with a blank screen, but with a cursor.

---

### Post by Gotaro on 2009-02-03
Bump for good luck on getting this issue solved today! :)

---

