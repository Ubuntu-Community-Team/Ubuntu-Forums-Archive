---
title: "how to replace jaunty volume icon with intrepid?"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by 11010110 on 2009-05-27
Hi everyone,

I noticed that as part of the new notification system in jaunty, the volume notification popup was changed both in appearance and position. I am not a fan of the new volume notification system (although the other notifications are just fine). I was wondering if there was a way that i could change the new volume popup to the old centered one from intrepid. 

If anyone has any ideas on how i could do this it would be a great help. thanks in advance!

---

### Post by ibuclaw on 2009-05-27
You can't change it without removing the entire notification system in general.

But to remove the notification system, run
```
sudo apt-get remove notify-osd
```
Then
```
kill -9 `pgrep notify-osd`
```

Regards
Iain

---

### Post by Jeff250 on 2009-05-27
A better way to switch to the old notification system is here:
[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

---

### Post by 11010110 on 2009-05-27
how can i change just that part of the notification system without messing with the rest?

---

### Post by 11010110 on 2009-05-28
bump

---

### Post by 11010110 on 2009-05-29
bump

---

### Post by 11010110 on 2009-05-30
does anyone know how to just replace the volume indicator while leaving the rest of the notification system intact?

---

### Post by 11010110 on 2009-05-31
bump... anyone?

---

