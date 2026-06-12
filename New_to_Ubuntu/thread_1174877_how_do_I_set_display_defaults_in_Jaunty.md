---
title: "how do I set display defaults in Jaunty?"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by mal1958 on 2009-05-31
I just changed my system from xubuntu to ubuntu 9.04 and have a problem.  My display keeps defaulting to 1600x something and anything printed on the screen is microscopic.  I have bad eyes to begin with and this is really a pain.  I tried to redo the display config but everytime I try to save I get the message that the 'xorg config file could not be overwritten.  Can anybody help?  I am trying to get my system to default to 1024 x 768 with a refresh of 60.


Mike

---

### Post by nandemonai on 2009-05-31
How are you actually trying to change the resolution?

It sounds like you're using nvidia-settings.

If so, then hit alt-F2 to bring up a run prompt in Gnome and enter:

```
gksudo nvidia-settings
```

You can only save the configuration as root. I could be way off but this seems to be a common problem for nvidia users.

---

### Post by mal1958 on 2009-05-31
Thank you, your method worked.  Now I have my normal default screen res.  Thank you again.

---

