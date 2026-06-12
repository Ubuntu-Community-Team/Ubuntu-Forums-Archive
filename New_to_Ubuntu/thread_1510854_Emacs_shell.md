---
title: "Emacs shell"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by nebu on 2010-06-16
Hey,
I am getting a lot of garbage characters when I run any commands in the shell provided in emacs.

I had tried looking it up in google and found this....
[http://joshstaiger.org/archives/2005/07/fixing_garbage.html](http://joshstaiger.org/archives/2005/07/fixing_garbage.html)

It is a method to fix the problem.... however, it is not working and I still get to see the garbage characters in the shell.

Any ideas guys??

---

### Post by jpkotta on 2010-06-17
The method in the link is the way to fix it.  You can try doing M-x ansi-color-for-comint-mode-on after enabling shell.

What happens if start it as "emacs -q"?

You might like to try term-mode, which is made more usable by multi-term ([http://www.emacswiki.org/emacs/MultiTerm](http://www.emacswiki.org/emacs/MultiTerm)).

---

### Post by hectorh30 on 2010-12-06
If it still helps, I found this [here]("http://www.emacswiki.org/emacs/ansi-color.el") :

> ;; If you decide you like this, add the following to your .emacs file:
;;
;; (autoload 'ansi-color-for-comint-mode-on "ansi-color" nil t)
;; (add-hook 'shell-mode-hook 'ansi-color-for-comint-mode-on)

Tried on 22.2 and Ubuntu 10.04 and seems to fix it.

---

