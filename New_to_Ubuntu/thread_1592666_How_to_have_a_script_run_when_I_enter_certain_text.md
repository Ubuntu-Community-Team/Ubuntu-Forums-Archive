---
title: "How to have a script run when I enter certain text?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by 3rr0r on 2010-10-10
Hello all.

I have installed thttpd on my ubuntu system and would only like to start its web server features when I like.  The command to start it is
```
/usr/local/sbin/thttpd -C /usr/local/etc/thttpd.conf
```  
However, I would like to start it from the terminal by typing "http start"

Any idea how I go about enabling that? I do not want this to start automatically when I boot up.  I will also need a "http stop" command.

Are symbolic links the way I should go?  If so, how do I make it so I can run "http start" and it understands that command from whichever directory I'm in (basically putting that command in PATH)?

---

### Post by nothingspecial on 2010-10-11
Make aliases in your .bashrc

```
gedit ~/.bashrc
```

The format is like this
```

alias custom_command='command you want to execute'
```

Put them on seperate lines

When you are done, save and exit then type

. ```
~/.bashrc
```

which "sort of" restarts bash

Your aliases will now be in effect.

---

