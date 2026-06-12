---
title: "K3B hangs when verifying a newly written data DVD"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-04-16
I use K3B to write data DVDs. Usually, I don't bother to verify the written data, because I have other backups.

But today, I'm writing some important data, so I want to verify the DVD after writing. To do that, checked "Verify written data".

After K3B has written its data, it ejects the DVD and waits for me to reinsert it so that it can verify. It shows overall progress at 50%, and verifying track 0 at 0%.

(See attached screenshot.)

However, when I reinsert the DVD, K3B does nothing. There is no prompt to continue, and it just sits there. Eventually, I have to click Cancel, and then try to verify the data from the terminal.

What have I done wrong?

Using Ubuntu Hardy 8.04 and K3B version 1.0.4

---

### Post by Ticketoride on 2009-04-16
Lots of Win Burning Progs have been doing that too, Nero probably the most notorious one. Its been fixed in 9.x, so it seems to be a Software Bug.

But then you may have a Coaster and the Software/Hardware freezes trying to read it.

Firmware Issues could also be at Play.

Use good Quality CD-Rs such as those made by Tayo Yuden.

---

### Post by Paddy Landau on 2009-04-16
> **Ticketoride said:**
> Lots of Win Burning Progs have been doing that too, Nero probably the most notorious one. Its been fixed in 9.x, so it seems to be a Software Bug.
Thanks, I'll await the release of 9.x and check manually in the meantime.

> **Ticketoride said:**
>  But then you may have a Coaster and the Software/Hardware freezes trying to read it.

Firmware Issues could also be at Play.
I suspect not, because when I reinsert the DVD, the computer successfully and automatically loads up the nautilus browser. K3B just sits there.

Thanks for the advice.

---

