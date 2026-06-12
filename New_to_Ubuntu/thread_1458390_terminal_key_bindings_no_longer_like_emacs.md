---
title: "terminal key bindings no longer like emacs?"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by raequin on 2010-04-19
So, I had to get a new laptop and so installed 9.10 --- I think I had 9.04 previously.  Can you tell me how to get terminal to behave like before wrt key bindings?  E.g. <Control>p for prior command, <Control>c for break or end current command or whatever, <Control>d to close the terminal window.  Plus there were the emacs-like navigation commands --- <Control>f, b, and d for forward, backward, and delete.

Thanks a lot.  I am just trying to get back up and running at the same speed as before.

---

### Post by raequin on 2010-04-20
Okay, so here's a weird one.  I learned that the problem is not with the key bindings in terminal --- it's that I'm using a Dvorak keyboard.  When I type in terminal the keyboard works fine, but when I press <Control> terminal treats the keyboard as QWERTY.  For example, I press Dvorak "p" and terminal shows "p", but if I hold <Control> and press Dvorak "p" terminal shows "(reverse-i-search), as if I had pressed <Control>r.  The p-key in Dvorak is located at the QWERTY r-key.

Any help?

---

### Post by raequin on 2010-04-20
Aiite, the solution was to remove the USA keyboard layout.  But the funny thing is when I restarted that layout was still an option, yet the <Control> keyboard shortcuts now work with Dvorak.  What changed is that the keys to switch between layouts were set back to "Both Alt keys together."  So I guess the problem was that I had it set to "Ctrl+Shift."

---

