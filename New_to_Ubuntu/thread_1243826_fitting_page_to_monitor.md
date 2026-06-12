---
title: "fitting page to monitor"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by romanskier on 2009-08-18
I can not size pages to view on monitor. For example I can't set up evolution mail because the whole page is not visible and there is no scrolling. Keyboard zoom out does not work in this situation, though I use it constantly on web pages.

---

### Post by LewRockwell on 2009-08-18
> **romanskier said:**
> I can not size pages to view on monitor. For example I can't set up evolution mail because the whole page is not visible and there is no scrolling. Keyboard zoom out does not work in this situation, though I use it constantly on web pages.

I found this comment from 2003:> Evolution does not respect the X geometry setting, thus at least the
position is left to the window manager.

However, Evolution does save its dimension (width and height) in GConf
and will start with that dimension the next time. So the dimension will
be remembered.

If you wanna *customize* the dimension on *every* startup, have a look
at the GConf settings in /apps/evolution/shell/view_defaults/ and change
them before starting Evolution. But IMHO this would be a somewhat
strange thing to do.


And I also found this more recent(but seemingly endless) bug report:

[https://bugs.launchpad.net/evolution/+bug/8629](https://bugs.launchpad.net/evolution/+bug/8629)

.

---

