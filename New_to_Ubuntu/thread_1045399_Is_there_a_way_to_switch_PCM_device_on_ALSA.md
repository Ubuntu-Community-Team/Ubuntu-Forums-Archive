---
title: "Is there a way to switch PCM device on ALSA?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by blaine1984 on 2009-01-20
Hi.
My Default PCM device on Alsa is not working with my 5.1 system, i tested it with speaker-test.

Editing .asoundrc I created a new PCM device:

```
pcm.ch51dup {
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
}

```

Wich works good with my 5.1 (tested with speaker-test -Dsurround51).
Is there a way to make every application (included gnome) use this PCM as default?

Thx.

---

