---
title: "rebind &lt;ESC&gt; in emacs"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by 2123 on 2010-05-10
Often when I type shortcuts in emacs ( I work on emacs only on my desktop and laptop), I tend to press the <ESC> key to cancel the command (the equivalent of C-g). Is it advisable ( or possible) to rebind the <ESC> key to work like a C-g?

---

### Post by jpkotta on 2010-05-11
It's possible, but it might cause trouble.  I'd say try it out and see if breaks anything you care about (which it might not).

```

(global-set-key (kbd "<escape>") 'keyboard-quit)

```

Note: by default, ESC ESC ESC (that's three separate presses of escape), will run the command keyboard-escape-quit, which is similar to keyboard-quit (which is what C-g does).  

You can find most key bindings with C-h k *key*.

---

### Post by 2123 on 2010-05-11
Thank you.

---

