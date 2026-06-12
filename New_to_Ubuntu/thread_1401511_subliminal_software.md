---
title: "subliminal software"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by scrimple101 on 2010-02-08
Hello, does anyone know of any applications that are designed to flash subliminal messages on the screen?

---

### Post by 3rdalbum on 2010-02-08
Not an ideal solution, but this might put you on the right track:

```
xterm -e "echo 'hello'& sleep 0.2"
```

I believe 'subliminal' messages are illegal in some parts of the world, and the whole thing looks like being a myth anyway.

---

### Post by scrimple101 on 2010-02-08
> **3rdalbum said:**
> Not an ideal solution, but this might put you on the right track:

```
xterm -e "echo 'hello'& sleep 0.2"
```

I believe 'subliminal' messages are illegal in some parts of the world, and the whole thing looks like being a myth anyway.

what does the code do?

---

### Post by mikechant on 2010-02-08
This is just for your own use, or use on others for research purposes - with their consent?

Doing this to other people without their consent would be unethical (and possibly invite a lawsuit).

Anyhow, assuming that you are using this with consent, you might want to look at this:
[http://linux.die.net/man/6/xsublim](http://linux.die.net/man/6/xsublim)
(native Linux)

and this
[http://sourceforge.net/projects/subliminal-msgs/files/](http://sourceforge.net/projects/subliminal-msgs/files/)
requires mono, which is probably already installed on your system

---

### Post by NikoC on 2010-02-08
It opens xterm for 0.2 seconds and displays the message 'hello' in this xterm window after which it closes.

---

