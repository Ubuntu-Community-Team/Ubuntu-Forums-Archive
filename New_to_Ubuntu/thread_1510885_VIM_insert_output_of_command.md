---
title: "VIM: insert output of command"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by alpha-lemming on 2010-06-16
Hello,

I know how to insert the output of a command into a new line belowl the cursor like this:

```
:r! <command> 
```but how can I insert the output into the middle of a line?

Thanks!

---

### Post by DaithiF on 2010-06-16
Hi,
this isn't possible in Vim out of the box, as far as I know.  You could define your own command to do it ... put this in your .vimrc:
```

:command! -nargs=1 R :normal mzi<RETURN><ESC>k:r!<args><RETURN>$J'z$J
```

then 
:R echo hello
would do what you want

---

