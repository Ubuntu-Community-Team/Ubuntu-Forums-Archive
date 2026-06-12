---
title: "error message at shut down"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by knuckle dragging monkey on 2009-06-08
Hello i see an error message or some type of message appears at shut down. but it it shows up and shuts down too fast i can't read it. Is there a way to find out what is says,like a message log or something like that. Thank you.

---

### Post by keplerspeed on 2009-06-08
Ubuntu flashes all kinds of crazy stuff on boot/shutdown. However, you could disable the splash screen to get a better look:

See codejunkie's post here [http://ubuntuforums.org/showthread.php?t=378861](http://ubuntuforums.org/showthread.php?t=378861)

---

### Post by knuckle dragging monkey on 2009-06-08
Thank you very much. i will do that.

---

### Post by kiridude on 2009-06-08
what you want to check out is the kernel ring buffer:

```
dmesg | less
```

you can scroll through the pages with the space bar and back with the b key.

---

