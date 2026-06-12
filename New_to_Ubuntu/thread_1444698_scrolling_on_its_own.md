---
title: "scrolling on its own"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by olayak on 2010-04-01
I have an eee pc 1005hab.  I also have ubuntu and firefox.  recently, whenever I select the scroll bar, it pauses and then continues to move downward (or upward) past where I wanted it to stop, until it gets to the bottom (or top) of the page.  how do i get this to stop!
it did not do this before.  maybe since I installed meerkat?
thanks
kathy

---

### Post by timjayko on 2010-04-01
always worth a reinstall try maybe that will fix it?

sudo apt-get remove firefox

sudo apt-get install firefox

---

### Post by undecim on 2010-04-01
> **timjayko said:**
> always worth a reinstall try maybe that will fix it?

sudo apt-get remove firefox

sudo apt-get install firefox

That will do nothing. It's very rare that binary files become corrupted in Ubuntu and that will still leave your settings intact.

This usually happens to me when I running a lot of programs at once and my computer gets slow. I overcompensate with the scrolling and firefox can't catch up until after I'm done and already see what I want.

This also happens a lot if you don't have video drivers installed, as that causes a similar kind of lag.

Take a look at the system monitor and see if you have an application taking up a lot of CPU.

---

### Post by olayak on 2010-04-01
ah, i do have a lot of programs open at a time. I will try and keep more closed. Is there another fix, too? Because I often need to have multiple programs working at once and multiple browser windows open.
thanks.

---

