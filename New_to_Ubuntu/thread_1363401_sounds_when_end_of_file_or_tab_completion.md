---
title: "sounds when end of file or tab completion"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by dagarshali on 2009-12-24
Hi,
I have the 64 bit ubuntu karmic kaola...and I have this high pitched annoying sound that I get when ever i use tab completion or when i reach the end of file on emacs or when I click on a link in firefox and the its comes back with a error. How do I make this stop.

Regards,
Vishwa

---

### Post by bodhi.zazen on 2009-12-24
disable your pc speaker.

There are several ways to do this

```
modprobe -r pcspkr
```

If that works, black list the module

Edit /etc/modprobe.d/blacklist , add pcspkr at the bottom.

You can also use other options:

[http://www.cyberciti.biz/faq/how-to-linux-disable-or-turn-off-beep-sound-for-terminal/](http://www.cyberciti.biz/faq/how-to-linux-disable-or-turn-off-beep-sound-for-terminal/)

---

