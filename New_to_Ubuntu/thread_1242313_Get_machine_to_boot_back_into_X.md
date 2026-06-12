---
title: "Get machine to boot back into X?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-08-17
Hello,

I made my machine boot directly into terminal mode with system>admin>services>uncheck gdm, and started X using the 'startx' command but to my surprise I can't check it again so the computer boots back into X as before/normal. I notice that I can't access Synaptic and user switcher on my panel so I assume I can't do anything that requires root privileges. So I tried 'sudo startx' but the X doesn't start. It seems to be hanging.

So how could I get Ubuntu to boot like before? Which file should I change and how should I edit it? Or how can I get X to start so I can become root if I need to? (I don't want X to be root the whole time just if I need it!)

Thanks!

---

### Post by nhasian on 2009-08-17
how about:

```
sudo /etc/init.d/gdm/ start
```

---

### Post by prvteprts on 2009-08-17
Actually, I think

```
sudo gdm start
```

has the same effect, and it's easier to remember.

---

### Post by sylvainrb on 2009-08-17
Thanks both of them worked!

And if I want to stop X can I just type in
```
sudo gdm stop
```
or
```
sudo /etc/init.d/gdm/ stop
```?

Or can I just kill the process, but it seems a little to radical to turn it off this way haha!

---

