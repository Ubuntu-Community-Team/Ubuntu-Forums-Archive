---
title: "How to link 2 commands toan  icon?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by igorsand on 2009-01-03
In order to force webcamera work in Skype, I have to perform 
 ```
[COLOR="Blue"]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/COLOR]
```
This worked and I've made the alias
```
[COLOR="Blue"]alias skype="LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/COLOR]
```"
Now it works from terminal with the command 
 ```
[COLOR="Blue"]> skype[/COLOR]
```
Probably, stupid attempts to introduce these both commands 
into the command line of "properties" of the Skype icon or to write
into the file ~/.local/share/applications/skype.desktop 
instead of 
```
[COLOR="Blue"]Exec=skype[/COLOR]
```
the whole line,
```
[COLOR="Blue"]Exec="LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/COLOR]"
```
gives the same result: it does not find "child process LD_PRELOAD..."
***How to do it right?***

---

### Post by sdennie on 2009-01-03
Make a launcher that is:

```

sh -c "LD_PRELOAD=... skype"

```

Edit: In this case, you may have to use:

```

sh -c 'LD_PRELOAD=... skype' 

```

Because other wise the the "" of the LD_PRELOAD will break things.

---

### Post by igorsand on 2009-01-04
Thanks a lot, it works! :D
SOLVED

---

