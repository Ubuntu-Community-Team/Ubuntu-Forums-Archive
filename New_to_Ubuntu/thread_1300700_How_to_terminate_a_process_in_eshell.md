---
title: "How to terminate a process in eshell"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by shaoxiao on 2009-10-25
I debug a program in eshell ,the program has a bug and it can't be terminated 
because in eshell the ctrl+c can't be used to terminate.
Is there another way to terminate it?

Regards

---

### Post by whoop on 2009-10-25
Maybe you need kill?
```

man kill

```

---

### Post by diesch on 2009-10-25
It's C-c C-k in Eshell.

I prefer to use *term* in Emacs, that's a full vt100 emulation running your default shell, just like "normal" terminals.

---

### Post by shaoxiao on 2009-10-26
> **diesch said:**
> It's C-c C-k in Eshell.

I prefer to use *term* in Emacs, that's a full vt100 emulation running your default shell, just like "normal" terminals.


I found that C-c C-c can terminate the process that i am debugging.
And thank you for your tip about term.It's very good.

And thanks whoop too.

---

### Post by aspirintr on 2012-06-16
You can send ctrl+[*something*] to eshell in emacs (or to any other one as well, I am not quite sure) using ```
C-q C-[*something*]
``` . I found it from [http://emacswiki.org/emacs/MultiTerm](http://emacswiki.org/emacs/MultiTerm) some where near the bottom.

---

### Post by codemaniac on 2012-06-16
kill command as suggested above can take up different options to terminate a process .

have you tried xkill while killing GUI apps , its fun . ;)

---

