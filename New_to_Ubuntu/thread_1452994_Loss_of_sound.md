---
title: "Loss of sound"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by Tremlett on 2010-04-12
I lose sound, right about at the 24 hour mark each day. A reboot gets me back on Youtube, but another reboot will be necessary tomorrow. I can't seem to find any permanent solution to the problem.

Suggestions?

---

### Post by benhorton2 on 2010-04-12
Do you know if you are using ALSA or jackd to run your sound output? This info. will be necessary to diagnose (ALSA is the default unless you remember installing jackd)

---

### Post by Tremlett on 2010-04-12
It's ALSA since I haven't changed it.

---

### Post by sandyd on 2010-04-12
can you run this in the terminal (copy and paste)
```

lspci > ~/Desktop/lspci.txt
aplay -l >> ~/Desktop/soundinfo.txt
alsactl -v >> ~/Desktop/soundinfo.txt
uname -a >> ~/Desktop/soundinfo.txt

```

The terminal is accessable through Applications -> Accessories -> Terminal.

Then, just attach soundinfo.txt and lspci.txt (their on your desktop) to your post.

---

### Post by Tremlett on 2010-04-13
Ok Carlee, expecting magic here...

---

### Post by sandyd on 2010-04-13
whats the computer manufacturer?

you can tr the method here: [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Tremlett on 2010-04-14
Now I have no sound at all.
I'm going to try and go back to 9.4, I didn't have this problem for the short time I used that. Can't find an install for it...****.

---

### Post by cuberts on 2010-04-14
> **Tremlett said:**
> I lose sound, right about at the 24 hour mark each day. A reboot gets me back on Youtube, but another reboot will be necessary tomorrow. I can't seem to find any permanent solution to the problem.

Suggestions?Actually I cant even get any sound working on my Ubuntu 9.10
I dual boot with Windows XP

---

### Post by Tremlett on 2010-04-20
Try installing alsamixer. I found it in Synaptic.

---

