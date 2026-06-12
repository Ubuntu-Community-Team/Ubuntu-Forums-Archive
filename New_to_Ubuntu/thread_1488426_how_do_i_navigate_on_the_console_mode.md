---
title: "how do i navigate on the console mode?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2010-05-20
when i hit CTRL+ALT+F1 I enter into the console mode.
I enter my username and password. whenever i type in a command and some of the information scrolls all the way up.

how do i manage to scroll up in the console mode and read the contexts?

I tried using FN+Page up and FN+Page down. but it doesn't want to work. is there something wrong here? or is there another way to scroll in the console mode?

---

### Post by krishnandu.sarkar on 2010-05-20
As far I know, there is no way to scroll up and down in console.

---

### Post by Nythain on 2010-05-20
shift+page up or down

but there's a limited scrollback buffer set in your shell profile, so dont expect to scrollback infinately

---

### Post by blchinezu on 2010-05-20
> **Nythain said:**
> shift+page up or down

but there's a limited scrollback buffer set in your shell profile, so dont expect to scrollback infinately
  if that's not enough you can try:

*your --command* **| more**

where *your --command* is what you want to run

---

