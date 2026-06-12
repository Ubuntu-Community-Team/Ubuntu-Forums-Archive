---
title: "Black screen of death / no icons"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by maciej234 on 2011-02-18
I'm getting a black screen of death on my desktop, twice over the last 2 days.  The background will turn black, all the icons on AWN dock will be red squares, and some top panel icons on the notification side will disappear forcing a restart.

Gnome clock will not function, and I can' open any applications.  

The Chromium web browser will stay open and I can see the webpage, but the desktop turns black and the dock turns to red squared icons.  Everything stops working too.

---

### Post by sikander3786 on 2011-02-18
Can you notice any specific application running at that time?

Is that black screen periodic or just random?

If periodic, you can switch from compiz to metacity and see if it is compiz doing the damage or not.

Press Alt + F2 and type

```
metacity --replace
```

Same way you can switch back to compiz by

```
compiz --replace
```

---

### Post by maciej234 on 2011-02-18
I'll take a picture on my phone next time it happens and post it.  I can only narrow it down to using Chromium and playing a youtube video, Pithos was playing also but I think it has something to do with flash. It is just random.  I updated chromium the other day, maybe thats whats causing the display/graphics fall dead.

I switched to just the Chrome browser for now, hopefully nothing else.

It honestly looks like a video/graphics problem.  I ran a command to rebuild x server.  I am also running 11.2 ATI 5670 in case anyone is wondering.

---

### Post by grahammechanical on 2011-02-18
You could be running out of memory and your swap partition is too small and the CPU is running close to 100% paging data in and out of the swap memory.

Open system monitor.

Regards

---

### Post by maciej234 on 2011-03-14
I updated the driver and haven't had a problem yet.

---

